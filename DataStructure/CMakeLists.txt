# DataStructure: every .cpp here is a self-contained program with its own main(),
# so each one becomes its own executable target.
#
# Note: these files use C-style bodies inside .cpp translation units, which is why
# they are compiled as C++ (a C++ compiler is required, not a C one).

set(DATASTRUCTURE_PROGRAMS
    BinaryTree
    HashTable
    LinkList
    LinkList_with_head
    RedBlackTree
    SqList
    SqStack
)

foreach(program IN LISTS DATASTRUCTURE_PROGRAMS)
    add_executable(${program} ${program}.cpp)

    # These teaching files define their own return codes, including
    #     #define OVERFLOW -2
    # They now include <cstdlib> explicitly (malloc/free must not be relied on
    # transitively), and the Windows CRT exposes a legacy macro with the same name
    # in the same header chain, which makes MSVC report C4005 for these six targets.
    # The source is left untouched: the warning is a header collision of our making,
    # so it is silenced per target rather than globally and only for MSVC.
    if(MSVC)
        target_compile_options(${program} PRIVATE /wd4005)
    endif()
endforeach()

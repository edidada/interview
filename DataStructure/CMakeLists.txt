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
endforeach()

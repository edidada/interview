# Algorithm: the search/sort programs here are each self-contained with their own
# main(), so each one becomes its own executable target.

set(ALGORITHM_PROGRAMS
    CountSort
    FibonacciSearch
    HeapSort
)

foreach(program IN LISTS ALGORITHM_PROGRAMS)
    add_executable(${program} ${program}.cpp)
endforeach()

# Not wired on purpose:
#   BucketSort.cpp  - defines ListNode/insert/Merge/BucketSort but has no main(),
#                     so it is a fragment rather than a program. Compile-only clean.
#   *.h             - header-only implementations, kept for browsing and reuse;
#                     they are indexed by the IDE without needing a target.

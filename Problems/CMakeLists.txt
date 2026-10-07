# Problems: each problem folder holds one self-contained program with its own main().
# Target names are the file stems and must stay unique across the whole build.

set(PROBLEM_PROGRAMS
    ChessboardCoverageProblem/ChessboardCoverage
    KnapsackProblem/pack
    NeumannNeighborProblem/Formula/Neumann2_3_12
    NeumannNeighborProblem/Recursive/Neumann2_4_12
    RoundRobinProblem/MatchTable
    TubingProblem/Tubing
)

foreach(program IN LISTS PROBLEM_PROGRAMS)
    get_filename_component(target_name ${program} NAME)
    add_executable(${target_name} ${program}.cpp)
endforeach()

# The *.exe files committed next to these sources are stale artifacts of the
# pre-CMake days; build output now goes to the CMake build directory instead.

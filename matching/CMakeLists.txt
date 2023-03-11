add_library (csm_graphalgorithm STATIC "graphflow.cpp" "iedyn.cpp" "matching.cpp" "sj_tree.cpp" "symbi.cpp" "turboflux.cpp")
target_link_libraries(csm_graphalgorithm csm_graph csm_induced_graph csm_globals)

add_library (csm STATIC "main.cpp")
target_link_libraries(csm csm_graphalgorithm)
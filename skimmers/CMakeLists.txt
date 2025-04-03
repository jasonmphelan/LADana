#include_directories(${INCLUDES} )
#include_directories(${INCLUDES} ${LIBRARIES})

add_executable(test_skimmer test_skimmer.cpp)

target_link_libraries(test_skimmer ${ROOT_LIBRARIES} -LLAD_LIB)


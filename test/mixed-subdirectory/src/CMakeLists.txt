if(MSVC)
  add_definitions(-D_CRT_SECURE_NO_WARNINGS)
  set(pch_source test-pch.c test-pch.cpp)
endif()
set(CMAKE_CXX_FLAGS "${CMAKH_CXX_FLAGS} -Werror")
set(CMAKE_C_FLAGS "${CMAKH_CXX_FLAGS} -Werror")
include_directories("${CMAKE_CURRENT_SOURCE_DIR}/../")
add_executable(test-mixed-subdirectory test-mixed.c test-mixed.cpp ../test-pch.h ${pch_source})
add_precompiled_header(test-mixed-subdirectory ../test-pch.h PCH_PATH test-pch.h)
add_test(test-mixed-subdirectory test-mixed-subdirectory)

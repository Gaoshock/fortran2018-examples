# This example also shows CMake Fortran preprocessor directives
cmake_minimum_required(VERSION 3.1)
project(f2008contig Fortran)
enable_testing()

get_directory_property(hasParent PARENT_DIRECTORY)
if(NOT hasParent)
  include(../cmake/compilers.cmake)
endif()


add_executable(contig contiguous.F90)
target_compile_options(contig PRIVATE ${FFLAGS})
target_link_libraries(contig PRIVATE ${FLIBS})
target_compile_definitions(contig PRIVATE ISCONTIG=${f08contig})
if(CMAKE_Fortran_COMPILER_ID STREQUAL GNU)
  target_compile_options(contig PRIVATE -Warray-temporaries)
endif()

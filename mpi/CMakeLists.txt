cmake_minimum_required (VERSION 2.8.12)
project(fortran2015demo Fortran) 

# ------- MPI Fortran examples ----------------
find_package(MPI)
if(MPI_Fortran_COMPILER)
    set(CMAKE_Fortran_COMPILER ${MPI_Fortran_COMPILER}) #wrapper compiler mpif90
    # FIXME these lines should work, but used wrapper compiler mpif90 instead
    # consider mpif90 --showme
    # https://www.open-mpi.org/faq/?category=mpi-apps
    #
    #add_definitions(${MPI_Fortran_COMPILE_FLAGS})
    #include_directories(${MPI_Fortran_INCLUDE_PATH})
    #list(APPEND CMAKE_Fortran_LINK_FLAGS ${MPI_Fortran_LINK_FLAGS})

    add_executable(hello mpi_helloworld.f90)
    #target_link_libraries(hello ${MPI_Fortran_LIBRARIES})

    add_executable(pass mpi_pass.f90)
endif()
cmake_minimum_required(VERSION 3.12)
project(SCTL LANGUAGES CXX VERSION 1.0.0)

find_package(MPI REQUIRED)
find_package(OpenMP REQUIRED)

add_library(sctl INTERFACE)
target_include_directories(sctl INTERFACE ${PROJECT_SOURCE_DIR}/include)
target_link_libraries(sctl INTERFACE MPI::MPI_CXX OpenMP::OpenMP_CXX)
target_compile_features(sctl INTERFACE cxx_std_11)
target_compile_options(sctl INTERFACE "-DSCTL_HAVE_MPI" "-DSCTL_GLOBAL_MEM_BUFF=2048")

add_library(SCTL::sctl ALIAS sctl)

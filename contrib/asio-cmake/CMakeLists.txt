set(LIBRARY_DIR "${sample_cpp_SOURCE_DIR}/contrib/asio/asio")

add_library(asio_ STATIC ${LIBRARY_DIR}/src/asio.cpp)
target_include_directories(asio_ PUBLIC ${LIBRARY_DIR}/include)
target_compile_definitions(
  asio_ PUBLIC -DASIO_STANDALONE -DASIO_SEPARATE_COMPILATION
               -DASIO_NO_DEPRECATED)
find_package(Threads)
target_link_libraries(asio_ PRIVATE Threads::Threads)
add_library(contrib::asio ALIAS asio_)

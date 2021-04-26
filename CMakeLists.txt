cmake_minimum_required(VERSION 3.0.0)
project(main VERSION 0.1.0)

include_directories(${CMAKE_HOME_DIRECTORY}/include)

link_directories(./lib)

set(CMAKE_VERBOSE_MAKEFILE on)
set (CMAKE_CXX_STANDARD 11)

add_executable(main main.cpp)
target_link_libraries(
    main
    PRIVATE
    avformat avcodec avutil avfilter
)

add_executable(demuxing_decoding demuxing_decoding.c)
target_link_libraries(
    demuxing_decoding
    PRIVATE
    avformat avcodec avutil avfilter
)

add_executable(remuxing remuxing.c)
target_link_libraries(
    remuxing
    PRIVATE
    avformat  avutil 
)

add_executable(muxing muxing.c)
target_link_libraries(
    muxing
    PRIVATE
    avformat  avutil swscale swresample avcodec
)



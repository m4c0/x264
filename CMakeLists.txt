cmake_minimum_required(VERSION 3.5)
project(x264 VERSION 0.1 LANGUAGES C)

set(CMAKE_CXX_STANDARD 14)

add_library(x264 STATIC
    common/mc.c common/predict.c common/pixel.c common/macroblock.c
    common/frame.c common/dct.c common/cpu.c common/cabac.c
    common/common.c common/osdep.c common/rectangle.c
    common/set.c common/quant.c common/deblock.c common/vlc.c
    common/mvpred.c common/bitstream.c
    encoder/analyse.c encoder/me.c encoder/ratecontrol.c
    encoder/set.c encoder/macroblock.c encoder/cabac.c
    encoder/cavlc.c encoder/encoder.c encoder/lookahead.c
)
target_include_directories(x264 PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/common)

add_executable(x264-example example.c)
target_link_libraries(x264-example PUBLIC x264)


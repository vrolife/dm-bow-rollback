cmake_minimum_required(VERSION 3.16)

if(ANDROID_PLATFORM)
    set(CMAKE_TOOLCHAIN_FILE "$ENV{ANDROID_NDK_HOME}/build/cmake/android.toolchain.cmake")
endif(ANDROID_PLATFORM)

project(dm-bow-rollback)

set(CMAKE_CXX_STANDARD 17)

add_executable(dm-bow-rollback dm-bow-rollback.cpp)

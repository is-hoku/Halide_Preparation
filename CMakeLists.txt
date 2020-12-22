# CMakeの最低バージョンを記述
cmake_minimum_required(VERSION 2.8)

# コンパイラオプション
add_definitions("-std=c++11")

find_package(OpenCV REQUIRED)

# 環境変数設定
set(ENV{PROJECT_NAME}       test)
set(ENV{Halide_ROOT_DIR}    /home/nono/projects/Halide-10.0.0-x86-64-linux)
set(ENV{Halide_INSTALL_DIR} $ENV{Halide_ROOT_DIR})
set(ENV{Halide_INCLUDE_DIR} $ENV{Halide_INSTALL_DIR}/include)
set(ENV{Halide_LIBRARY_DIR} $ENV{Halide_INSTALL_DIR}/lib)


# インクルードパス設定
include_directories($ENV{Halide_INCLUDE_DIR})
include_directories(${OpenCV_INCLUDE_DIRS})

# ライブラリパス設定
link_directories($ENV{Halide_LIBRARY_DIR})

# 実行ファイル名とソース指定
add_executable($ENV{PROJECT_NAME} lesson_01_basics.cpp UsingOpencv.cpp)

# リンク設定
target_link_libraries($ENV{PROJECT_NAME} Halide)
target_link_libraries($ENV{PROJECT_NAME} pthread)
target_link_libraries($ENV{PROJECT_NAME} dl)
target_link_libraries($ENV{PROJECT_NAME} ${OpenCV_LIBS})

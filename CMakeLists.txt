cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(YOLOv7LibTorch)
SET(CMAKE_BUILD_TYPE Release)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

find_package(OpenCV REQUIRED)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${TORCH_CXX_FLAGS} -lopencv_core -lopencv_imgproc -lopencv_highgui")
list(APPEND CMAKE_PREFIX_PATH "./libtorch")
find_package(Torch REQUIRED)
add_executable(YOLOv7LibTorch src/YOLOv7LibTorch.cpp)

include_directories(
${PROJECT_SOURCE_DIR}/include
${OpenCV_INCLUDE_DIRS}
)

target_link_libraries(YOLOv7LibTorch ${OpenCV_LIBS} ${TORCH_LIBRARIES})
set_property(TARGET YOLOv7LibTorch PROPERTY CXX_STANDARD 17)
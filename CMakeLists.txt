# CMakeList.txt: VulkanCourse 的 CMake 项目，在此处包括源代码并定义
# 项目特定的逻辑。
#
cmake_minimum_required (VERSION 3.8)

project ("VulkanCourse")

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/")

include(CPM)
find_package(Vulkan REQUIRED)

file(GLOB SOURCES
  src/*.h
  src/*.cpp
)

CPMAddPackage(
  GITHUB_REPOSITORY g-truc/glm
  GIT_TAG 0.9.9.8
)

CPMAddPackage(
  GITHUB_REPOSITORY glfw/glfw
  GIT_TAG 3.3.6
  OPTIONS "GLFW_BUILD_EXAMPLES OFF" "GLFW_BUILD_TESTS OFF" "GLFW_BUILD_DOCS OFF" "GLFW_INSTALL OFF"
)

# 将源代码添加到此项目的可执行文件。
add_executable(VulkanCourse ${SOURCES})

target_sources(
  VulkanCourse
  PRIVATE
)

target_include_directories(
  VulkanCourse
  PRIVATE
)

target_link_libraries(
  VulkanCourse
  PRIVATE
  glfw
  glm
  Vulkan::Vulkan
)

# TODO: 如有需要，请添加测试并安装目标。

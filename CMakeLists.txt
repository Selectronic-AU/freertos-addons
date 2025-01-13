# Minimum required version of CMake
cmake_minimum_required(VERSION 3.12)
 
# Define the project name, version, and language
project(FreertosAddonsLibrary VERSION 1.0 LANGUAGES CXX)
 
# Set the target library name
set(TARGET_NAME freertos-addons)
 
set (FREE_RTOS_ROOT "../freertos")
 
# Specify the source files for the freertos-addons library
set(FREERTOS_ADDONS_SRC_FILES
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/ccondition_variable.cpp
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/cevent_groups.cpp
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/cmem_pool.cpp
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/cmutex.cpp
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/cqueue.cpp
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/cread_write_lock.cpp
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/csemaphore.cpp
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/ctasklet.cpp
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/cthread.cpp
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/ctickhook.cpp
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/ctimer.cpp
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/cworkqueue.cpp
)
 
# Define the include directories for the freertos-addons library
set(FREERTOS_ADDONS_INCLUDE_DIRS
    ${CMAKE_CURRENT_LIST_DIR}/c++/Source/include
	${FREE_RTOS_ROOT}/include
    ${FREE_RTOS_ROOT}/portable/GCC/ARM_CM4F
)
 
# Create the library target
add_library(${TARGET_NAME} STATIC ${FREERTOS_ADDONS_SRC_FILES})
 
# Define the include directories for the library
target_include_directories(${TARGET_NAME} PUBLIC ${FREERTOS_ADDONS_INCLUDE_DIRS})
 
 
# Optionally: Pass the include directories to the parent scope
set(FREERTOS_ADDONS_INCLUDE_DIRS ${FREERTOS_ADDONS_INCLUDE_DIRS} PARENT_SCOPE)
 
# Optionally: Define additional compiler properties (e.g., C++ standard)
# set_target_properties(${TARGET_NAME} PROPERTIES CXX_STANDARD 11)

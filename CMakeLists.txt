cmake_minimum_required(VERSION 2.8) #Проверка версии CMake.

set(PROJECT_NAME LAB4) #Создаем обычную локальную переменную с именем проекта
project(${PROJECT_NAME}) # Название проекта

set(Arraylist Arraylist) #Переменная с именем приложения
set(List List) #Переменная с именем библиотеки
set(main main)

set(CMAKE_CONFIGURATION_TYPES "Debug;Release" CACHE STRING "Configs" FORCE) #Создается переменная CMAKE_CONFIGURATION_TYPES со значением "Debug;Release" и меткой/разделом Configs, переменная сохраниется в специальном файле доступном из всех файлов,
if(NOT CMAKE_BUILD_TYPE) # проверка имеющихся у компилятора вариантов сборки
  set(CMAKE_BUILD_TYPE Release) #Если нет то устанавливаем Release
endif()

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE})

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/Arraylist
${CMAKE_CURRENT_SOURCE_DIR}/List)
# ${CMAKE_CURRENT_SOURCE_DIR}/gtest)

add_subdirectory(Arraylist) #Добавляем директорию с под-CMakeList-ом, и выполняем под-CMakeList
add_subdirectory(List)
add_subdirectory(main)
add_subdirectory(gtest)
add_subdirectory(test)
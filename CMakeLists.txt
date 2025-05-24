cmake_minimum_required(VERSION 3.11)
project(lab06 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Включение CPack
include(InstallRequiredSystemLibraries)

# Настройка версии
set(CPACK_PACKAGE_VERSION_MAJOR "1")
set(CPACK_PACKAGE_VERSION_MINOR "0")
set(CPACK_PACKAGE_VERSION_PATCH "0")

# Включаем необходимые политики
cmake_policy(SET CMP0002 NEW)
cmake_policy(SET CMP0079 NEW)

# Контактная информация
set(CPACK_PACKAGE_CONTACT "max2007varlamov@gmail.com")

# Описание пакета
set(CPACK_PACKAGE_DESCRIPTION "A simple solver for quadratic equations")

# Сводка описания
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "Solves quadratic equations")

# Файл лицензии
set(CPACK_RESOURCE_FILE_LICENSE "${CMAKE_SOURCE_DIR}/LICENSE")

# Файл README
set(CPACK_RESOURCE_FILE_README "${CMAKE_SOURCE_DIR}/README.md")

# Настройка для RPM
set(CPACK_RPM_PACKAGE_RELEASE "1")
set(CPACK_RPM_PACKAGE_LICENSE "MIT")

# Включение модуля CPack
include(CPack)

# Подключаем подпроекты в правильном порядке
add_subdirectory(formatter_lib)
add_subdirectory(formatter_ex_lib)
add_subdirectory(solver_lib)  # Добавляем solver_lib
add_subdirectory(solver_application)

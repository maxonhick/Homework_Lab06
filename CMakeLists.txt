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
set(CPACK_PACKAGE_NAME "lab06")
set(CPACK_PACKAGE_DESCRIPTION "A simple solver for quadratic equations")
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "Solves quadratic equations")
set(CPACK_PACKAGE_CONTACT "email")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "contacts")
set(CPACK_RESOURCE_FILE_LICENSE "${CMAKE_SOURCE_DIR}/LICENSE")
set(CPACK_RESOURCE_FILE_README "${CMAKE_SOURCE_DIR}/README.md")

# Настройка генераторов CPack
set(CPACK_GENERATOR "TGZ;ZIP")
if(UNIX AND NOT APPLE)
    set(CPACK_GENERATOR "${CPACK_GENERATOR};DEB;RPM")
elseif(APPLE)
    set(CPACK_GENERATOR "${CPACK_GENERATOR};DragNDrop")
elseif(WIN32)
	set(CPACK_GENERATOR "WIX")
endif()

# Настройка RPM
set(CPACK_RPM_PACKAGE_RELEASE "1")
set(CPACK_RPM_PACKAGE_LICENSE "MIT")
set(CPACK_RPM_PACKAGE_GROUP "Development/Tools")

# Настройка DEB
set(CPACK_DEBIAN_PACKAGE_SECTION "devel")
set(CPACK_DEBIAN_PACKAGE_DEPENDS "libc6 (>= 2.27)")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "Ваше имя <ваш.email@example.com>")

# Настройка WIX (Windows)
if(WIN32)
    # Указываем WiX как генератор
    set(CPACK_GENERATOR "WIX")

    set(CPACK_WIX_PRODUCT_GUID "CDF8CD0C-12F9-4599-87D7-ACD9FAB2B27C")

    # Имя и версия продукта
    set(CPACK_PACKAGE_NAME "lab06")
    set(CPACK_PACKAGE_VERSION "1.0.0")

    # Файл лицензии (в формате RTF)
    set(CPACK_RESOURCE_FILE_LICENSE "${CMAKE_SOURCE_DIR}/LICENSE")
endif()

# Настройка DragNDrop (macOS)
if(APPLE)
    set(CPACK_DMG_VOLUME_NAME "Lab06 Solver")
    set(CPACK_DMG_FORMAT "UDBZ")
    set(CPACK_DMG_BACKGROUND_IMAGE "${CMAKE_SOURCE_DIR}/background.png")
endif()

include(CPack)

# Подключаем подпроекты в правильном порядке
add_subdirectory(formatter_lib)
add_subdirectory(formatter_ex_lib)
add_subdirectory(solver_lib)
add_subdirectory(solver_application)


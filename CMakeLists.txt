cmake_minimum_required(VERSION 3.30)

set(ORG KarypisLab)
set(NAME GKlib)
set(VERSION 8bd6bad750b2b0d90800c632cf18e8ee93ad72d7)
set(EXT tar.gz)
set(SHA256 e1d59de12336731e6dde8465f05de7b907fae5d72c921cffcde217a89eaab654)
set(TAG_PREFIX "")

project("cmeel-${NAME}" VERSION 0.0.1)

include(ExternalProject)
ExternalProject_Add(
  ${NAME}
  URL "https://github.com/${ORG}/${NAME}/archive/${TAG_PREFIX}${VERSION}.${EXT}"
  URL_HASH "SHA256=${SHA256}"
  DOWNLOAD_EXTRACT_TIMESTAMP OFF
  CMAKE_ARGS "-DBUILD_SHARED_LIBS=ON" "-DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX}"
)

# dummy file for install target
install(FILES README.md DESTINATION share/cmeel-${NAME}/)

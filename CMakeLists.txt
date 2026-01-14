cmake_minimum_required(VERSION 3.30)

set(ORG KarypisLab)
set(NAME GKlib)
set(VERSION 6e7951358fd896e2abed7887196b6871aac9f2f8)
set(EXT tar.gz)
set(SHA256 42c52e58408ad06dc23c2a052eea529b269287ea8a6f3f6cdc47f18d50b2a177)
set(TAG_PREFIX "")

project("cmeel-${NAME}" VERSION 0.0.2)

if(CMAKE_SYSTEM_PROCESSOR MATCHES "(x86)|(X86)|(amd64)|(AMD64)")
  set(NO_X86 OFF)
else()
  set(NO_X86 ON)
endif()

include(ExternalProject)
ExternalProject_Add(
  ${NAME}
  URL "https://github.com/${ORG}/${NAME}/archive/${TAG_PREFIX}${VERSION}.${EXT}"
  URL_HASH "SHA256=${SHA256}"
  DOWNLOAD_EXTRACT_TIMESTAMP OFF
  CMAKE_ARGS "-DBUILD_SHARED_LIBS=ON"
             "-DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX}"
             "-DNO_X86=${NO_X86}")

# dummy file for install target
install(FILES "README.md" DESTINATION "share/cmeel-${NAME}/")

file(GLOB_RECURSE SOURCES "*.cpp" "*.c")
#file(GLOB_RECURSE SOURCES "*.c")

add_library(ngscope_dci STATIC ${SOURCES})

target_link_libraries(ngscope_dci config rrc_asn1 asn1_utils srsran_common)

# Link with C++ standard library
if(BUILD_STATIC)
  target_link_libraries(ngscope_dci stdc++)
endif()

if (LIBASN4G)
  target_link_libraries(ngscope_dci ${LIBASN4G_LIBRARY})
endif(LIBASN4G)

if (LIBASN5G)
  target_link_libraries(ngscope_dci ${LIBASN5G_LIBRARY})
endif(LIBASN5G)

if(ENABLE_GUI AND SRSGUI_FOUND)
  target_link_libraries(ngscope_dci ${SRSGUI_LIBRARIES})
endif()

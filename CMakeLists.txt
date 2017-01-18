cmake_minimum_required(VERSION 2.8.4)

PROJECT(n3ar_build)

INCLUDE_DIRECTORIES(./)

find_package(OpenCV QUIET)
if (OpenCV_FOUND)
  INCLUDE_DIRECTORIES(${OpenCV_INCLUDE_DIRS})
else()
  message("OpenCV not found!!!")
endif()

#set_target_properties(dlib PROPERTIES POSITION_INDEPENDENT_CODE ON)

set(runtime_source_files 
	./runtime/sample.c
	)

ADD_EXECUTABLE(n3ar ${runtime_source_files})
TARGET_LINK_LIBRARIES(n3ar ${OpenCV_LIBS} )

ADD_EXECUTABLE(dgen learning/dgen.c)
TARGET_LINK_LIBRARIES(dgen ${OpenCV_LIBS} )

ADD_EXECUTABLE(tlrn learning/tlrn.c)
TARGET_LINK_LIBRARIES(tlrn ${OpenCV_LIBS} )
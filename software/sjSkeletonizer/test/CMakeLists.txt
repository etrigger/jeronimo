IF(CGAL_Qt4_FOUND AND QT4_FOUND AND OPENGL_FOUND AND QGLVIEWER_FOUND)


	INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/source/exception)
	INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/source/io)
	INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/source/core)
	INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/source/log)
	INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/source/parameters)
	INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/source/plugin)
	INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/source/utils)
	INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/source/system)
	INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/source/xml)
	
	INCLUDE_DIRECTORIES(${CMAKE_CURRENT_BINARY_DIR})
	INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/extern)
	INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/extern/OGF)
	INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/extern/log4cplus/include)
	INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/extern/libxml2/include)
	INCLUDE(AddFileDependencies)
	INCLUDE_DIRECTORIES(${QGLVIEWER_INCLUDE_DIR})
	INCLUDE_DIRECTORIES(${TAUCS_INCLUDE_DIR})
	
	SET(sjtestcgalopennl_SOURCE
		sjTestCgalOpenNL.cpp
	)
	
	ADD_EXECUTABLE ( sjTestCgalOpenNL ${sjtestcgalopennl_SOURCE} )

	TARGET_LINK_LIBRARIES ( sjTestCgalOpenNL
		basic
		math
		${QT_LIBRARIES} 
		${CGAL_LIBRARIES} 
		${CGAL_3RD_PARTY_LIBRARIES} 
		${QGLVIEWER_LIBRARIES} 
		${OPENGL_gl_LIBRARY} 
		${OPENGL_glu_LIBRARY} 
		${TAUCS_LIBRARIES_DIR}/libtaucs
	)
	
	ADD_EXECUTABLE ( sjTestParameters sjTestParameters.cpp )
	TARGET_LINK_LIBRARIES ( sjTestParameters parameters exception log log4cplus) 
	
	ADD_EXECUTABLE ( sjTestPlugin sjTestPlugin.cpp )
	TARGET_LINK_LIBRARIES ( sjTestPlugin plugin system parameters exception log log4cplus xml io libxml2) 

ELSE (CGAL_Qt4_FOUND AND QT4_FOUND AND OPENGL_FOUND AND QGLVIEWER_FOUND)
    message(STATUS "THE REQUIRED LIBRARIES ARE NOT PRESENT.")
ENDIF (CGAL_Qt4_FOUND AND QT4_FOUND AND OPENGL_FOUND AND QGLVIEWER_FOUND)
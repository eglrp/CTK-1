set(KIT ${PROJECT_NAME})

create_test_sourcelist(Tests ${KIT}CppTests.cpp
  ctkAbstractPythonManagerTest.cpp
  #EXTRA_INCLUDE TestingMacros.h
  )

SET (TestsToRun ${Tests})
REMOVE (TestsToRun ${KIT}CppTests.cpp)

set(LIBRARY_NAME ${PROJECT_NAME})

include_directories(${CMAKE_SOURCE_DIR}/Libs/Testing
                    ${CMAKE_CURRENT_BINARY_DIR})

QT4_GENERATE_MOCS(
  ctkAbstractPythonManagerTest.cpp
  )

add_executable(${KIT}CppTests ${Tests})
target_link_libraries(${KIT}CppTests ${LIBRARY_NAME} ${CTK_BASE_LIBRARIES})

#
# Add Tests
#

SIMPLE_TEST( ctkAbstractPythonManagerTest )

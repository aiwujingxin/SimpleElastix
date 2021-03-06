
foreach(p
    CMP0064 # CMake 3.4
    )
  if(POLICY ${p})
    cmake_policy(SET ${p} NEW)
  endif()
endforeach()

#
# Python Tests
#
sitk_add_python_test( Test.ImageTests
  "${CMAKE_CURRENT_SOURCE_DIR}/sitkImageTests.py" )

sitk_add_python_test( Test.ImageIndexing
  "${CMAKE_CURRENT_SOURCE_DIR}/ImageIndexingTest.py" )

sitk_add_python_test( Test.IOTest
  "${CMAKE_CURRENT_SOURCE_DIR}/IOTest.py"
  "${SimpleITK_TEST_OUTPUT_DIR}")

# Numpy test.
sitk_add_python_test( Test.Numpy
  "${CMAKE_CURRENT_SOURCE_DIR}/sitkNumpyArrayConversionTest.py"
  )

sitk_add_python_test( Test.ProcessObject
  "${CMAKE_CURRENT_SOURCE_DIR}/sitkProcessObjectTest.py"
  )

sitk_add_python_test( Test.ConcurrentImageRead
  "${CMAKE_CURRENT_SOURCE_DIR}/ConcurrentImageRead.py"
  )

sitk_add_python_test( Test.ImageReadWriteInt64
  "${CMAKE_CURRENT_SOURCE_DIR}/ImageReadWriteInt64.py"
  )


if(CMAKE_VERSION VERSION_GREATER "3.3")
  if(TEST Python.Test.ConcurrentImageRead)
    set_tests_properties( Python.Test.ConcurrentImageRead PROPERTIES LABELS "UNSTABLE" )
  endif()
endif()

sitk_add_python_test( Test.ArrayView
  "${CMAKE_CURRENT_SOURCE_DIR}/sitkGetArrayViewFromImageTest.py"
  )

sitk_add_python_test( Test.TransformixImageFilter
  "${CMAKE_CURRENT_SOURCE_DIR}/sitkTransformixImageFilterTest.py"
  )


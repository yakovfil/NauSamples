if (NAU_CORE_SAMPLES OR NAU_DEMO_SOURCE_DIR)

  if(NAU_RUNTIME_PROFILE STREQUAL "minimal")
    add_subdirectory(minimalApp)
    return()
  endif()

  add_subdirectory("sample_common")

  nau_collect_cmake_subdirectories(sampleDirs ${CMAKE_CURRENT_SOURCE_DIR})

  foreach(sample ${sampleDirs})
    if (NOT ${sample} STREQUAL "sample_common")
      message(STATUS "Found sample: (${sample})")
      add_subdirectory(${sample})
    endif()
  endforeach()

  # Copy samples to prebuild engine
  install(DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/"
    DESTINATION samples
    PATTERN ".git" EXCLUDE
    PATTERN "build" EXCLUDE
    PATTERN "bin" EXCLUDE
    PATTERN "output" EXCLUDE
    PATTERN "__pycache__" EXCLUDE
    PATTERN "*imgui.ini" EXCLUDE
  )
endif()

if(MSVC)
	FILE(GLOB LIBRARY_FILES_C "*.cpp" "*.rc")
else()
	FILE(GLOB LIBRARY_FILES_C "*.cpp")
endif()
FILE(GLOB LIBRARY_FILES_H "*.h" "*.inl")

cxx_executable_with_flags_no_pch(ReconstructMesh "Apps" "${cxx_default}" "MVS;MVArchive;${OpenMVS_EXTRA_LIBS}" ${LIBRARY_FILES_C} ${LIBRARY_FILES_H})

# Install
INSTALL(TARGETS ReconstructMesh
	EXPORT OpenMVSTargets
	RUNTIME DESTINATION "${INSTALL_BIN_DIR}" COMPONENT bin)

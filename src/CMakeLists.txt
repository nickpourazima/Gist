add_library (
    Gist STATIC
    AccelerateFFT.cpp
    AccelerateFFT.h
    CoreFrequencyDomainFeatures.cpp
    CoreFrequencyDomainFeatures.h
    CoreTimeDomainFeatures.cpp
    CoreTimeDomainFeatures.h
    Gist.cpp
    Gist.h
    MFCC.cpp
    MFCC.h
    OnsetDetectionFunction.cpp
    OnsetDetectionFunction.h
    WindowFunctions.cpp
    WindowFunctions.h
    Yin.cpp
    Yin.h
)

target_include_directories(Gist 
    PUBLIC 
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${GIST_FFTW_INCLUDE_DIRS}
)

target_compile_definitions (Gist PUBLIC -DUSE_FFTW)
target_link_libraries(Gist PRIVATE ${GIST_FFTW_LIBRARIES})

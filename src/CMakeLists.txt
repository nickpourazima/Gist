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

target_include_directories(Gist PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/src)

source_group (Source src)

target_compile_definitions (Gist PUBLIC -DUSE_FFTW)
target_link_libraries(Gist PRIVATE ${FFTW_LIBRARIES})

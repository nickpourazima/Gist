include_directories(${CMAKE_CURRENT_SOURCE_DIR})
if(NOT FFTW_FOUND)
    include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../libs/kiss_fft130)
endif()

add_library(Gist STATIC
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

if(FFTW_FOUND)
    target_link_libraries(Gist PUBLIC FFTW::FFTW)
endif()

source_group(Source src)

# This is to expose the necessary headers to projects that link against Gist
target_include_directories(Gist PUBLIC 
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    $<INSTALL_INTERFACE:include>
)

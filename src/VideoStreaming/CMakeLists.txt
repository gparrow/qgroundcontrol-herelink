set(EXTRA_LIBRARIES)

if (GST_FOUND)
	set(EXTRA_LIBRARIES ${GST_LIBRARIES})
	list(APPEND EXTRA_SRC
		gstqtvideosink/delegates/basedelegate.cpp
		gstqtvideosink/delegates/qtquick2videosinkdelegate.cpp
		gstqtvideosink/delegates/qtvideosinkdelegate.cpp
		gstqtvideosink/delegates/qwidgetvideosinkdelegate.cpp
		gstqtvideosink/gstqtglvideosink.cpp
		gstqtvideosink/gstqtglvideosinkbase.cpp
		gstqtvideosink/gstqtquick2videosink.cpp
		gstqtvideosink/gstqtvideosink.cpp
		gstqtvideosink/gstqtvideosinkbase.cpp
		gstqtvideosink/gstqtvideosinkplugin.cpp
		gstqtvideosink/gstqwidgetvideosink.cpp
		gstqtvideosink/painters/genericsurfacepainter.cpp
		gstqtvideosink/painters/openglsurfacepainter.cpp
		gstqtvideosink/painters/videomaterial.cpp
		gstqtvideosink/painters/videonode.cpp
		gstqtvideosink/utils/bufferformat.cpp
		gstqtvideosink/utils/utils.cpp
	)
endif()

add_library(VideoStreaming
    GLVideoItemStub.cc
    GLVideoItemStub.h
    gstqgc.c
    gstqgcvideosinkbin.c
    SubtitleWriter.cc
    SubtitleWriter.h
    VideoReceiver.cc
    VideoReceiver.h
    VideoStreaming.cc
    VideoStreaming.h
    VideoManager.cc
    VideoManager.h
)

target_link_libraries(VideoStreaming
        PRIVATE
                gst_plugins_good
	PUBLIC
		qgc
		Qt5::Multimedia
		Qt5::OpenGL
		${EXTRA_LIBRARIES}
)

target_include_directories(VideoStreaming INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})

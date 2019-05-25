if (NOT WIN32)
	return()
endif()

project(obs-timetext)

if(WIN32)
	set(obs-timetext_PLATFORM_SOURCES
		gdiplus/obs-timetext.cpp)
	set(obs-timetext_PLATFORM_DEPS
		gdiplus)
endif()

add_library(obs-timetext MODULE
	${obs-timetext_PLATFORM_SOURCES}
	${obs-timetext_PLATFORM_HEADERS})
target_link_libraries(obs-timetext
	libobs
	${obs-timetext_PLATFORM_DEPS})

install_obs_plugin_with_data(obs-timetext data)

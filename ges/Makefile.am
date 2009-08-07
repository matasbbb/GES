built_header_make = gesmarshal.h
build_source_make = gesmarshal.c

lib_LTLIBRARIES = libges-@GST_MAJORMINOR@.la

EXTRA_libges_@GST_MAJORMINOR@_la_SOURCES = gesmarshal.list 

CLEANFILES = $(BUILT_SOURCES) $(built_header_make) $(built_source_make)

libges_@GST_MAJORMINOR@_la_SOURCES = 		\
	ges.c					\
	ges-simple-timeline-layer.c		\
	ges-timeline.c				\
	ges-timeline-layer.c			\
	ges-timeline-object.c			\
	ges-timeline-pipeline.c			\
	ges-timeline-source.c			\
	ges-timeline-transition.c		\
	ges-track.c				\
	ges-track-object.c			\
	ges-track-source.c

libges_@GST_MAJORMINOR@includedir = $(includedir)/gstreamer-@GST_MAJORMINOR@/ges/
libges_@GST_MAJORMINOR@include_HEADERS = 	\
	ges-types.h				\
	ges.h					\
	ges-internal.h				\
	ges-simple-timeline-layer.h		\
	ges-timeline.h				\
	ges-timeline-layer.h			\
	ges-timeline-object.h			\
	ges-timeline-pipeline.h			\
	ges-timeline-source.h			\
	ges-timeline-transition.h		\
	ges-track.h				\
	ges-track-object.h			\
	ges-track-source.h


libges_@GST_MAJORMINOR@_la_CFLAGS = $(GST_PLUGINS_BASE_CFLAGS) $(GST_CFLAGS)
libges_@GST_MAJORMINOR@_la_LIBADD = $(GST_PLUGINS_BASE_LIBS) $(GST_BASE_LIBS) $(GST_LIBS) 
libges_@GST_MAJORMINOR@_la_LDFLAGS = $(GST_LIB_LDFLAGS) $(GST_ALL_LDFLAGS) $(GST_LT_LDFLAGS)

DISTCLEANFILE = $(CLEANFILES)

#files built on make all/check/instal
BUILT_SOURCES =			\
	$(built_header_make)	\
	$(built_source_make)

gesmarshal.h: gesmarshal.list
	glib-genmarshal --header --prefix=ges_marshal $^ > gesmarshal.h.tmp
	mv gesmarshal.h.tmp gesmarshal.h

gesmarshal.c: gesmarshal.list
	echo "#include \"glib-object.h\"" >gesmarshal.c.tmp
	echo "#include \"gesmarshal.h\"" >> gesmarshal.c.tmp
	glib-genmarshal --body --prefix=ges_marshal $^ >> gesmarshal.c.tmp
	mv gesmarshal.c.tmp gesmarshal.c
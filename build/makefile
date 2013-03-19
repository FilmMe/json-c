#
# Copyright (C) 2013 FilmMe Group Oy
# makefile for json-c DEB build
# note: run make as root
#

PRODUCT="json-c"
VER="0.1.0"
ARCH=`dpkg --print-architecture`
ROOT=$(PRODUCT)_$(VER)_$(ARCH)

all:
	# create control files
	mkdir $(ROOT)
	mkdir $(ROOT)/DEBIAN
	cat src/control  | sed s/#VER#/$(VER)/ | sed s/#ARCH#/$(ARCH)/ > $(ROOT)/DEBIAN/control
	cp src/postinst $(ROOT)/DEBIAN/postinst
	# copy content
	./cp2 ../.libs libjson.so.$(VER) $(ROOT)/usr/local/lib
	# make deb package
	dpkg-deb --build $(ROOT)
	# remove temp directory
	rm -R $(ROOT)

clean:
	# remove temp directories
	rm -R -f $(PRODUCT)_*_$(ARCH)/
	# remove deb packages
	rm -f $(PRODUCT)_*_$(ARCH).deb


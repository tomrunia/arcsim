.PHONY: all clean clean-subdirs

# Runia (2019-03) | Originally:
#	all: lib/libalglib.a lib/libjson.a lib/libtaucs.a
# But libjson can all be installed using apt-get
all: lib/libalglib.a lib/libtaucs.a

lib/libalglib.a:
	cd alglib/cpp/src && g++ -c *.cpp && ar rcs libalglib.a *.o
	mkdir -p include/alglib/ lib/
	cp alglib/cpp/src/*.h include/alglib/
	cp alglib/cpp/src/libalglib.a lib/

lib/libjson.a:
	cd jsoncpp && scons platform=linux-gcc
	mkdir -p include/json/ lib/
	cp jsoncpp/include/json/*.h include/json/
	cp jsoncpp/libs/linux-gcc-*/libjson_linux-gcc-*_libmt.a lib/libjson.a

lib/libtaucs.a:
	cd taucs && ./configure module=\!METIS && $(MAKE)
	mkdir -p include/ lib/
	cp taucs/build/*/*.h taucs/src/*.h include/
	cp taucs/lib/*/libtaucs.a lib/

clean: clean-subdirs
	rm -rf include/* lib/*

clean-subdirs:
	rm -f alglib/cpp/src/*.{o,a}
	rm -rf jsoncpp/{bin,buildscons,dist,libs}
	$(MAKE) -C taucs clean

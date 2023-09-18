FROM ubuntu:18.04
RUN apt-get update -qq
RUN apt-get install -qq -y \
	  autoconf \
	  automake \
	  autopoint \
	  autotools-dev \
	  android-sdk \
	  build-essential \
	  git \
	  debmake \
	  pkg-config \
	  libgles2-mesa-dev \
	  libwayland-dev \
	  libtool
WORKDIR /root/libhybris
COPY ./hybris .
COPY ./android-headers-30 /root/libhybris/androidheaders
COPY ./android_system/lib64 /system/lib64
RUN ./autogen.sh
RUN ./configure \
		--prefix=/opt/libhybris \
		--enable-arch=arm64 \
		--with-android-headers=/root/libhybris/androidheaders
RUN make -j10
RUN make clean
RUN make install
CMD ["tail", "-f", "/dev/null"]

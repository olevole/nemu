MKDIR_P = mkdir -p
TOP_DIR = ${CURDIR}

deps:
	dnf -y install cmake gcc \
		ncurses-devel \
		sqlite-devel \
		libusbx-devel \
		systemd-devel \
		libxml2-devel \
		libarchive-devel \
		graphviz-devel \
		dbus-devel \
		git

build:
	cmake \
	-DCPACK_RPM_PACKAGE_SOURCES=ON \
	-DNM_WITH_NETWORK_MAP=ON \
	-DNM_WITH_DBUS=ON \
	-DNM_SAVEVM_SNAPSHOTS=ON && \
	cpack -G RPM --config CPackSourceConfig.cmake && \
	cp *.src.rpm $(outdir)

srpm: deps build

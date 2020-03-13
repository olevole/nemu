MKDIR_P = mkdir -p
BUILD_DIR = build

deps:
	dnf -y install cmake gcc \
		ncurses-devel \
		sqlite-devel \
		libusbx-devel \
		systemd-devel \
		libxml2-devel \
		libarchive-devel \
		graphviz-devel \
		dbus-devel

dirs:
	${MKDIR_P} ${BUILD_DIR}
	${MKDIR_P} $(outdir)

build: dirs
	cd ${BUILD_DIR} && \
	cmake ../ \
	-DCPACK_RPM_PACKAGE_SOURCES=ON \
	-DNM_WITH_NETWORK_MAP=ON \
	-DNM_WITH_DBUS=ON \
	-DNM_SAVEVM_SNAPSHOTS=ON && \
	cpack -G RPM --config ./CPackSourceConfig.cmake && \
	cp *.src.rpm $(outdir)

srpm: deps build

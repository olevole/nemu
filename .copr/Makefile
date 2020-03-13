MKDIR_P = mkdir -p
TOP_DIR = ${CURDIR}
BUILD_DIR = ${CURDIR}/build

# su -c 'COMMAND' - mockbuild

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

dirs:
	su -c '${MKDIR_P} ${BUILD_DIR}' - mockbuild
	su -c '${MKDIR_P} $(outdir)' - mockbuild

build: dirs
	su -c '\
	cd ${BUILD_DIR} && \
	cmake ${TOP_DIR} \
	-DCPACK_RPM_PACKAGE_SOURCES=ON \
	-DNM_WITH_NETWORK_MAP=ON \
	-DNM_WITH_DBUS=ON \
	-DNM_SAVEVM_SNAPSHOTS=ON && \
	cpack -G RPM --config ./CPackSourceConfig.cmake && \
	cp *.src.rpm $(outdir)' - mockbuild

srpm: deps build

MKDIR_P = mkdir -p
BUILD_DIR = build

deps:
	dnf -y install cmake

dirs:
	${MKDIR_P} ${BUILD_DIR}
	${MKDIR_P} $(outdir)

build: dirs
	cd ${BUILD_DIR} && \
	cmake ../ \
	-DCPACK_RPM_PACKAGE_SOURCES=ON \
	-DNM_WITH_NETWORK_MAP \
	-DNM_WITH_DBUS \
	-DNM_SAVEVM_SNAPSHOTS && \
	cpack -G RPM --config ./CPackSourceConfig.cmake && \
	cp *.src.rpm $(outdir)

srpm: deps build

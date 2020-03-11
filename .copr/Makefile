MKDIR_P = mkdir -p

deps:
	dnf -y install cmake

dirs:
	${MKDIR_P} $(outdir)

build: dirs
	cd $(outdir) && \
	cmake ../ \
	-DCPACK_RPM_PACKAGE_SOURCES=ON \
	-DNM_WITH_NETWORK_MAP \
	-DNM_WITH_DBUS \
	-DNM_SAVEVM_SNAPSHOTS && \
	make package

srpm: deps build


# Maintainer: 
pkgname="ros-melodic-franka-description"
pkgver="0.6.0"
pkgrel=1
pkgdesc="franka_description contains URDF files and meshes of Franka Emika robots"
arch=('x86_64')
url="http://wiki.ros.org/franka_description"
license=('Apache 2.0')

makedepends=(
'cmake'
)

depends=(
'ros-melodic-xacro'
)

provides=($pkgname)
conflicts=($pkgname)
_dir="franka_ros-release-release-melodic-franka_description-0.6.0-1"
source=("$pkgname-$pkgver.tar.gz::https://github.com/frankaemika/franka_ros-release/archive/release/melodic/franka_description/0.6.0-1.tar.gz")
md5sums=('f0ceec6f6f0274a88ccdd85609276d9a')

build() {
	# Use ROS environment variables
  	source /usr/share/ros-build-tools/clear-ros-env.sh
  	[ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

	# Create build directory
  	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  	cd ${srcdir}/build

	# Build project
	cmake ${srcdir}/${_dir} \
	      -DCMAKE_BUILD_TYPE=Release \
	      -DCATKIN_BUILD_BINARY_PACKAGE=ON \
	      -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
	      -DPYTHON_EXECUTABLE=/usr/bin/python3 \
	      -DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}

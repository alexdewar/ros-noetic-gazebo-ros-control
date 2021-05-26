# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - gazebo_ros_control."
url='http://ros.org/wiki/gazebo_ros_control'

pkgname='ros-noetic-gazebo-ros-control'
pkgver='2.9.2'
arch=('i686' 'x86_64' 'aarch64' 'armv7h' 'armv6h')
pkgrel=2
license=('BSD')

ros_makedepends=(ros-noetic-joint-limits-interface
  ros-noetic-controller-manager
  ros-noetic-transmission-interface
  ros-noetic-hardware-interface
  ros-noetic-std-msgs
  ros-noetic-angles
  ros-noetic-roscpp
  ros-noetic-catkin
  ros-noetic-pluginlib
  ros-noetic-urdf
  ros-noetic-control-toolbox
  ros-noetic-gazebo-dev)
makedepends=('cmake' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-noetic-joint-limits-interface
  ros-noetic-controller-manager
  ros-noetic-hardware-interface
  ros-noetic-std-msgs
  ros-noetic-angles
  ros-noetic-roscpp
  ros-noetic-urdf
  ros-noetic-pluginlib
  ros-noetic-gazebo-ros
  ros-noetic-control-toolbox
  ros-noetic-transmission-interface)
depends=(${ros_depends[@]})

_dir="gazebo_ros_pkgs-${pkgver}/gazebo_ros_control"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros-simulation/gazebo_ros_pkgs/archive/${pkgver}.tar.gz"
        "no_GAZEBO_CXX_FLAGS.patch")
sha256sums=('db937f15e5bf8f804de5d8dc0b67607f8b354aecde35785b6bff2d43387abff4'
            '3adb9bdff185e9358eda7f406d5968f2d7b18e997ccf46fa1dc0386bfb59e0bc')

prepare() {
  cd "$srcdir/gazebo_ros_pkgs-$pkgver"
  patch -p0 < "$srcdir/no_GAZEBO_CXX_FLAGS.patch"
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/noetic/setup.bash ] && source /opt/ros/noetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_CXX_STANDARD=17 \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/noetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

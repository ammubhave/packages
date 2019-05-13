include $(TOPDIR)/rules.mk

PKG_NAME:=fbzmq
PKG_VERSION:=2019.05.06.00
PKG_RELEASE:=1
PKG_MAINTAINER:=Amol Bhave <ambhave@fb.com>

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/facebook/fbzmq/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=feff700f75ede6a7afba543e9de557294b4da1fddefd7227f406e581d562ce61

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

PKG_BUILD_PARALLEL:=1
CMAKE_SOURCE_SUBDIR:=fbzmq
CMAKE_OPTIONS:= \
	-DCMAKE_POSITION_INDEPENDENT_CODE=ON \
	-DBUILD_TESTS=OFF \
	-DBUILD_SHARED_LIBS=OFF \
	-DTHRIFT1="$(STAGING_DIR_HOST)/bin/thrift1"
CMAKE_INSTALL:=1

define Package/fbzmq
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=Facebook ZeroMQ wrappers.
	DEPENDS:=+glog +gflags +libfolly +libzstd +libsodium +libfizz +fbthrift \
		+libdouble-conversion +libzmq +libsigar
endef

define Package/fbzmq/description
	Facebook ZeroMQ wrappers.
endef

define Package/fbzmq/install
	$(INSTALL_DIR) $(1)/usr/lib
endef

$(eval $(call BuildPackage,fbzmq))

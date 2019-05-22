include $(TOPDIR)/rules.mk

PKG_NAME:=openr
PKG_SOURCE_DATE:=2019-05-06
PKG_SOURCE_VERSION:=9437bbaff3e463a56f592c60d33e4fc33e2e27f9
PKG_RELEASE:=1
PKG_MAINTAINER:=Amol Bhave <ambhave@fb.com>

PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_DATE).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/facebook/openr/tar.gz/$(PKG_SOURCE_VERSION)?
PKG_HASH:=15acb76b5867e247f9d15342b7cad3f03028f8b8e19ae515e0f5cc5f1a9557b5
PKG_BUILD_DIR:=$(BUILD_DIR)/openr-$(PKG_SOURCE_VERSION)

PKG_BUILD_DEPENDS:=fbthrift/host fbthrift libfolly libsigar libnl fbzmq authsae

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

TARGET_LDFLAGS:=-Wl,--dynamic-linker=/lib/ld-uClibc-0.9.33.2.so
PKG_BUILD_PARALLEL:=1
CMAKE_BINARY_SUBDIR:=build
CMAKE_OPTIONS:= \
	-DCMAKE_POSITION_INDEPENDENT_CODE=ON \
	-DBUILD_TESTS=OFF \
	-DBUILD_SHARED_LIBS=OFF \
	-DTHRIFT1="$(STAGING_DIR_HOST)/bin/thrift1" \
	-DBUILD_FBMESHD=ON
CMAKE_INSTALL:=1

define Package/openr
	SECTION:=network
	CATEGORY:=Network
	TITLE:=OpenR: Distributed platform for building autonomic network functions.
	DEPENDS:=+libstdcpp +fbthrift +libfolly +libsigar +libzmq-nc \
		+libnl-core +libnl-route +re2 +libatomic +fbzmq +libsae +libpcap
endef

define Package/openr/description
	Open Routing, OpenR, is Facebook's internally designed and developed routing
	protocol/platform. Originally built for performing routing on the Terragraph
	network, its has found adoption in other networks at Facebook including
	Express Backbone.
endef

define Package/openr/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/{fbmeshd,run_fbmeshd.sh} $(1)/usr/sbin/
	sed -i 's%/bin/bash%/bin/sh%' $(1)/usr/sbin/run_fbmeshd.sh
endef

$(eval $(call BuildPackage,openr))

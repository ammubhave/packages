include $(TOPDIR)/rules.mk

PKG_NAME:=fbthrift
PKG_VERSION:=2019.05.27.00
PKG_RELEASE:=1
PKG_MAINTAINER:=Amol Bhave <ambhave@fb.com>

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/facebook/fbthrift/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=7c56dae532e60844520cef4ce03abd4911323fe340fdee0cc3a6a3e8adb09e3f

PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=fbthrift/host
HOST_BUILD_DEPENDS:=boost/host libmstch/host

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/cmake.mk

HOST_BUILD_PREFIX:=$(STAGING_DIR_HOST)

PKG_BUILD_PARALLEL:=1
HOST_BUILD_PARALLEL:=1
CMAKE_OPTIONS:= \
	-DBoost_NO_BOOST_CMAKE=ON \
	-DCMAKE_POSITION_INDEPENDENT_CODE=ON \
	-DBUILD_SHARED_LIBS=ON
CMAKE_HOST_OPTIONS:= \
	-DBoost_NO_BOOST_CMAKE=ON \
	-Dcompiler_only=ON
HOST_LDFLAGS:=-Wl,-rpath=$(STAGING_DIR_HOST)/lib
CMAKE_INSTALL:=1

define Package/fbthrift
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=Facebook's branch of Apache Thrift, including a new C++ server.
	DEPENDS:=+libwangle +libfmt +libmstch +librsocket-cpp +@boost-host-build-filesystem \
		+@boost-host-build-thread +@boost-host-build-system
endef

define Package/fbthrift/description
	Facebook's branch of Apache Thrift, including a new C++ server.
endef

define Package/fbthrift/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,fbthrift))
$(eval $(call HostBuild))

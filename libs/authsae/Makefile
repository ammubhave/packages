include $(TOPDIR)/rules.mk

PKG_NAME:=authsae
PKG_VERSION:=1.2.9
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/cozybit/authsae/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=a75e0432ba87d9f44fd9d7e9a9ddaf05bd00802b3a61ad6637a4922b9bf38144

PKG_BUILD_DEPENDS:=libnl openssl libconfig

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

PKG_BUILD_PARALLEL:=1
CMAKE_OPTIONS:= \
	-DENABLE_LINUX_TARGETS=OFF
EXTRA_CXXFLAGS:=-Wno-error
CMAKE_INSTALL:=1

define Package/libsae
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=authsae library by cozybit, Inc.
	DEPENDS:=+libnl-core +libnl-route
endef

define Package/libsae/description
	Simultaneous Authentication of Equals: Unofficial official clone of the now stale http://sourceforge.net/projects/authsae -- currently maintained by cozybit, Inc.
endef

$(eval $(call BuildPackage,libsae))

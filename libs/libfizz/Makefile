include $(TOPDIR)/rules.mk

PKG_NAME:=libfizz
PKG_VERSION:=2019.05.27.00
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/facebookincubator/fizz/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=d3f5325717a2af3684a41889d45b19e975cfff177faffdfaab8cb63df4e0318c
PKG_BUILD_DIR:=$(BUILD_DIR)/fizz-$(PKG_VERSION)

PKG_LICENSE:=BSD
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

PKG_BUILD_PARALLEL:=1
CMAKE_SOURCE_SUBDIR:=fizz
CMAKE_OPTIONS:= \
	-DBUILD_EXAMPLES=OFF \
	-DBUILD_SHARED_LIBS=ON
CMAKE_INSTALL:=1

define Package/libfizz
	SECTION:=libs
	CATEGORY:=Libraries
	DEPENDS:=+libfolly
	TITLE:=C++14 implementation of the TLS-1.3 standard
	URL:=https://github.com/facebookincubator/fizz
endef

define Package/libfizz/description
	C++14 implementation of the TLS-1.3 standard.
	Fizz currently supports TLS 1.3 drafts 28, 26 (both wire-compatible with the final specification), and 23.
endef

define Package/libfizz/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libfizz.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libfizz))

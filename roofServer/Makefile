include $(TOPDIR)/rules.mk

PKG_NAME:=roofServer
PKG_VERSION:=0.1.0
PKG_RELEASE:=1

PKG_MAINTAINER:=Mohit Rathod
PKG_LICENSE:=MIT

PKG_BUILD_PARALLEL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/msrathod/roof_server.git
PKG_SOURCE_VERSION:=v0.1.0
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

include $(INCLUDE_DIR)/uclibc++.mk
include $(INCLUDE_DIR)/package.mk

#define Build/Prepare
#	mkdir -p $(PKG_BUILD_DIR)
#	$(CP) -r /data2/Projects/blynk-library-arduino/* $(PKG_BUILD_DIR)/
#endef

define Package/roofServer
  SUBMENU:=Blynk
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Roof server for IOT RetRoof
  URL:=http://www.blynk.cc
  DEPENDS:=+libpthread +librt
endef

define Package/roofServer/description
 Blynk is a platform with iOS and Android apps to control Arduino,
 Raspberry Pi, Onion Omega and the likes over the Internet.
 You can easily build graphic interfaces for all your projects
 by simply dragging and dropping widgets.
endef

MAKE_FLAGS += LD="$(TARGET_CC)"

define Package/roofServer/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/roofServer $(1)/usr/bin/
endef

$(eval $(call BuildPackage,roofServer))

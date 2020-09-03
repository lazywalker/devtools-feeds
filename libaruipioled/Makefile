#
# Copyright 2020 Michael BD7MQB <bd7mqb@qq.com>
# This is free software, licensed under the GNU GENERAL PUBLIC LICENSE, Version 3.0
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libaruipioled
PKG_REV:=4119148
PKG_VERSION:=0.1.0
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://github.com/hallard/ArduiPi_OLED
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_PROTO:=git

PKG_LICENSE:=GPL-3.0
PKG_MAINTAINER:=Michael BD7MQB <bd7mqb@qq.com>

include $(INCLUDE_DIR)/package.mk

define Package/${PKG_NAME}
    SECTION:=DEV Tools
    CATEGORY:=DEV Tools
    TITLE:=Aruipi OLED Library
    DEPENDS:=+kmod-i2c-mt7628 +libi2c +libstdcpp
endef

define Package/${PKG_NAME}/description
Aruipi OLED Library
endef

LIB=libArduiPi_OLED
CFLAGS=-Wall -Ofast -DOPENWRT
MAKE_FLAGS += \
    LIB="${LIB}" \
    CFLAGS="${CFLAGS}" \

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/include
	# toolchains
	$(CP) $(PKG_BUILD_DIR)/$(LIB).so.1.0 $(1)/usr/lib/
	$(LN) $(LIB).so.1.0 $(1)/usr/lib/${LIB}.so.1
	$(LN) $(LIB).so.1.0 $(1)/usr/lib/${LIB}.so

	$(CP)  $(PKG_BUILD_DIR)/Adafruit_*.h $(1)/usr/include/
	$(CP) $(PKG_BUILD_DIR)/ArduiPi_*.h $(1)/usr/include/
	$(CP) $(PKG_BUILD_DIR)/bcm2835.h $(1)/usr/include/
endef

define Package/${PKG_NAME}/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/usr/lib

	$(CP) $(PKG_BUILD_DIR)/$(LIB).so.1.0 $(1)/usr/lib/
	$(LN) $(LIB).so.1.0 $(1)/usr/lib/${LIB}.so.1
	$(LN) $(LIB).so.1.0 $(1)/usr/lib/${LIB}.so
	
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/oled_demo $(1)/usr/bin/
endef

$(eval $(call BuildPackage,${PKG_NAME}))

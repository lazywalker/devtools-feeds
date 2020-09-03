include $(TOPDIR)/rules.mk

PKG_NAME:=oled-tool
PKG_VERSION:=0.1.0
PKG_RELEASE:=1

PKG_LICENSE:=GPL-3.0
PKG_MAINTAINER:=Michael BD7MQB <bd7mqb@qq.com>

PKG_INSTALL:=1
PKG_KCONFIG:=RALINK_MT7620 RALINK_MT7628

include $(INCLUDE_DIR)/package.mk

define Package/${PKG_NAME}
    SECTION:=DEV Tools
    CATEGORY:=DEV Tools
    TITLE:=OLED Testing Tool
    DEPENDS:=+kmod-i2c-mt7628
endef

define Package/${PKG_NAME}/description
OLED Testing Tool
endef

BIN:=oledtool
MAKE_FLAGS += \
    BIN="${BIN}" \

define Package/${PKG_NAME}/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/${BIN} $(1)/usr/bin/
endef

$(eval $(call BuildPackage,${PKG_NAME}))

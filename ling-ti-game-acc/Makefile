#
# Copyright (C) 2015-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v3.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=LingTiGameAcc
PKG_VERSION:=2023
PKG_RELEASE:=1.7.1

PKG_LICENSE:=GPLv3
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=eSir Playground

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  CATEGORY:=eSir Playground
  SUBMENU:=2. GameAcc
  TITLE:=LingTi Game Accelerator
  URL:=https://github.com/esirplayground/LingTiGameAcc
  DEPENDS:=+kmod-tun
endef

define Package/$(PKG_NAME)/description
LingTi Game Acc is a Game Accelerator which is paid service.
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) ./files/$(ARCH)/lingti $(1)/usr/bin


	$(INSTALL_DIR) $(1)/etc/init.d 
	$(INSTALL_BIN) ./root/etc/init.d/lingti $(1)/etc/init.d
endef

define Package/$(PKG_NAME)/postinst
#!/bin/sh
	chmod +x $(1)/usr/bin/lingti
	chmod +x $(1)/etc/init.d/lingti
exit 0
endef

$(eval $(call BuildPackage,$(PKG_NAME)))

#
# Copyright (C) Libremesh 2017
#
# This is free software, licensed under the GNU General Public License v3.

include $(TOPDIR)/rules.mk

PKG_NAME:=lime-app
PKG_VERSION:=v0.2.51
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_HASH:=35bb04bdbd17adf56fb790f6bf3ae9acd0bae7217d5b7c0f50ff335955d09ce1
PKG_SOURCE_URL:=https://libre.luandro.com

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	CATEGORY:=LiMe
	TITLE:=LimeApp
	MAINTAINER:=Marcos Gutierrez <gmarcos@altermundi.net>
	URL:=http://github.com/libremesh/lime-app
	DEPENDS:=+uhttpd +uhttpd-mod-ubus \
		+ubus-lime-location +ubus-lime-metrics +ubus-lime-utils \
		+ubus-lime-openairview +ubus-lime-grondrouting \
		+pirania +pirania-app
	PKGARCH:=all
endef

define Package/$(PKG_NAME)/description
	Light webApp for LibreMesh over uhttpd
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/www/app/
	$(CP) $(BUILD_DIR)/build/* $(1)/www/app/
	$(INSTALL_DIR) $(1)/usr/share/rpcd/acl.d || true
endef

define Package/$(PKG_NAME)/postinst
#!/bin/sh
[ -n "$${IPKG_INSTROOT}" ] ||	( /etc/init.d/rpcd restart && /etc/init.d/uhttpd restart ) || true
endef

$(eval $(call BuildPackage,$(PKG_NAME)))

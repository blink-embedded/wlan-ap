include $(TOPDIR)/rules.mk

PKG_NAME:=ucentral-schema
PKG_RELEASE:=1

PKG_SOURCE_URL=https://github.com/Telecominfraproject/wlan-ucentral-schema.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2022-05-29
PKG_SOURCE_VERSION:=caac3f11f790d2819bf9e41189c3cf99a5d18a78

PKG_MAINTAINER:=John Crispin <john@phrozen.org>
PKG_LICENSE:=BSD-3-Clause

include $(INCLUDE_DIR)/package.mk

define Package/ucentral-schema
  SECTION:=ucentral
  CATEGORY:=uCentral
  TITLE:=OpenWrt uCentral schema
  DEPENDS+= +ucode-mod-nl80211 +ucode-mod-rtnl
endef

define Package/ucentral-recovery
  SECTION:=ucentral
  CATEGORY:=uCentral
  TITLE:=OpenWrt uCentral recovery tooling
endef

define Build/Compile

endef

define Package/ucentral-schema/install
	$(INSTALL_DIR) $(1)/usr/share/ucentral
	$(CP) $(PKG_BUILD_DIR)/schemareader.uc $(1)/usr/share/ucentral
	$(CP) $(PKG_BUILD_DIR)/renderer/* $(1)/usr/share/ucentral
	$(CP) $(PKG_BUILD_DIR)/command/*.uc $(1)/usr/share/ucentral
	$(CP) $(PKG_BUILD_DIR)/system/*.uc $(1)/usr/share/ucentral
	$(CP) ./files/* $(1)
endef

define Package/ucentral-recovery/install
	$(INSTALL_DIR) $(1)/usr/share/ucentral $(1)/etc/uci-defaults/
	$(CP) $(PKG_BUILD_DIR)/command/*.uc $(1)/usr/share/ucentral
	$(CP) $(PKG_BUILD_DIR)/system/{capabilities,crashlog}.uc $(1)/usr/share/ucentral
	$(CP) ./files/etc/uci-defaults/99-ucentral-hostname $(1)/etc/uci-defaults/
endef

$(eval $(call BuildPackage,ucentral-recovery))
$(eval $(call BuildPackage,ucentral-schema))

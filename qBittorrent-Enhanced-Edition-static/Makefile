include $(TOPDIR)/rules.mk

PKG_NAME:=qBittorrent-Enhanced-Edition-static
PKG_VERSION:=4.4.5.10
PKG_RELEASE=$(AUTORELEASE)

ifeq ($(ARCH),x86_64)
	PKG_ARCH:=x86_64
	HASH:=95f8705c8b66669340b6fb72aa57ab6bf95f561bd4d7e2d0e3d70572dae96c5e
endif

ifeq ($(ARCH),arm64)
	PKG_ARCH:=aarch64
	HASH:=da2a95d1a19e77723ec3a35a5dc45c0fcd5697de8d056d963018fc63ce9c9370
endif

ifeq ($(ARCH),aarch64)
	PKG_ARCH:=aarch64
	HASH:=da2a95d1a19e77723ec3a35a5dc45c0fcd5697de8d056d963018fc63ce9c9370
endif

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	SUBMENU:=BitTorrent
	SECTION:=net
	CATEGORY:=Network
	TITLE:=bittorrent client programmed in C++ / Qt
	URL:=https://github.com/c0re100/qBittorrent-Enhanced-Edition
	DEPENDS:=@(aarch64||arm64||x86_64)
endef

define Package/$(PKG_NAME)/description
	qBittorrent is a bittorrent client programmed in C++ / Qt that uses
	libtorrent (sometimes called libtorrent-rasterbar) by Arvid Norberg.
	It aims to be a good alternative to all other bittorrent clients out
	there. qBittorrent is fast, stable and provides unicode support as
	well as many features.
endef

define Download/$(PKG_NAME)
  URL:=https://github.com/c0re100/qBittorrent-Enhanced-Edition/releases/download/release-$(PKG_VERSION)
  URL_FILE:=qbittorrent-enhanced-nox_$(PKG_ARCH)-linux-musl_static.zip
  FILE:=qbittorrent-nox_$(PKG_ARCH).zip
endef

define Build/Compile
	unzip -o -d $(PKG_INSTALL_DIR) $(DL_DIR)/qbittorrent-nox_$(PKG_ARCH).zip
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/qbittorrent-nox $(1)/usr/bin/
endef

$(eval $(call Download,$(PKG_NAME)))
$(eval $(call BuildPackage,$(PKG_NAME)))

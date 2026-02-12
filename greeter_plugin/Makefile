# WARNING: Automatically generated file using BAF (Build system Agnostic File) tooling
# WARNING: You should contribute changes to the project repository instead

include $(TOPDIR)/rules.mk

PKG_NAME:=greeter_plugin
PKG_VERSION:=v0.4.5
SHORT_DESCRIPTION:=Ambiorix Greeter data model plugin example
PKG_SOURCE:=greeter_plugin-v0.4.5.tar.gz
PKG_SOURCE_URL:=https://gitlab.com/prpl-foundation/components/ambiorix/examples/datamodel/greeter_plugin/-/archive/v0.4.5
PKG_HASH:=skip

PKG_BUILD_DIR:=$(BUILD_DIR)/greeter_plugin-v0.4.5

PKG_MAINTAINER:=Soft At Home <support.opensource@softathome.com>
PKG_LICENSE:=BSD-2-Clause
PKG_LICENSE_FILES:=LICENSE

COMPONENT:=greeter_plugin

PKG_RELEASE:=1

define SAHInit/Install
	install -d $(1)/etc/rc.d/
	ln -sfr $(1)/etc/init.d/$(COMPONENT) $(1)/etc/rc.d/S$(CONFIG_SAH_AMX_GREETER_PLUGIN_ORDER)$(COMPONENT)
	ln -sfr $(1)/etc/init.d/$(COMPONENT) $(1)/etc/rc.d/K$(CONFIG_SAH_AMX_GREETER_PLUGIN_ORDER)$(COMPONENT)
endef

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	CATEGORY:=prpl Foundation
	SUBMENU:=Examples
	TITLE:=$(SHORT_DESCRIPTION)
	URL:=https://gitlab.com/prpl-foundation/components/ambiorix/examples/datamodel/greeter_plugin
	DEPENDS += +libamxc
	DEPENDS += +libamxp
	DEPENDS += +libamxd
	DEPENDS += +libamxb
	DEPENDS += +libamxo
	DEPENDS += +amxrt
	MENU:=1
endef

define Package/$(PKG_NAME)/description
	Ambiorix Greeter data model plugin example.
	Demonstrates data model creation, object methods, parameter validation,
	event handling, and persistent storage using the Ambiorix framework.
endef

define Build/Compile
	$(call Build/Compile/Default, \
		STAGINGDIR=$(STAGING_DIR) \
		CONFIGDIR=$(STAGING_DIR) \
		PKG_CONFIG_PATH=$(STAGING_DIR)/usr/lib/pkgconfig \
		LIBDIR=/usr/lib \
		INSTALL_LIB_DIR=/lib \
		INSTALL_BIN_DIR=/bin \
		RAW_VERSION=$(PKG_VERSION) \
		PKG_CONFIG=$(PKG_CONFIG) \
		CONFIG_SAH_AMX_GREETER_PLUGIN_ORDER=$(CONFIG_SAH_AMX_GREETER_PLUGIN_ORDER))
endef

define Build/Install
	$(call Build/Install/Default, \
		install \
		INSTALL=install \
		D=$(PKG_INSTALL_DIR) \
		DEST=$(PKG_INSTALL_DIR) \
		STAGINGDIR=$(STAGING_DIR) \
		CONFIGDIR=$(STAGING_DIR) \
		PV=$(PKG_VERSION) \
		PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig \
		LIBDIR=/usr/lib \
		INSTALL_LIB_DIR=/lib \
		INSTALL_BIN_DIR=/bin \
		RAW_VERSION=$(PKG_VERSION) \
		PKG_CONFIG=$(PKG_CONFIG) \
		CONFIG_SAH_AMX_GREETER_PLUGIN_ORDER=$(CONFIG_SAH_AMX_GREETER_PLUGIN_ORDER))
	$(call SAHInit/Install,$(PKG_INSTALL_DIR))
endef

define Build/InstallDev
	$(call Build/Install/Default, \
		install \
		INSTALL=install \
		D=$(STAGING_DIR) \
		DEST=$(STAGING_DIR) \
		STAGINGDIR=$(STAGING_DIR) \
		CONFIGDIR=$(STAGING_DIR) \
		PV=$(PKG_VERSION) \
		PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig \
		LIBDIR=/usr/lib \
		INSTALL_LIB_DIR=/lib \
		INSTALL_BIN_DIR=/bin \
		RAW_VERSION=$(PKG_VERSION) \
		PKG_CONFIG=$(PKG_CONFIG) \
		CONFIG_SAH_AMX_GREETER_PLUGIN_ORDER=$(CONFIG_SAH_AMX_GREETER_PLUGIN_ORDER))
	$(call SAHInit/Install,$(STAGING_DIR))
endef

define Package/$(PKG_NAME)/install
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
	if [ -d ./files ]; then \
		$(CP) ./files/* $(1)/; \
	fi
	find $(1) -name *.a -exec rm {} +;
	find $(1) -name *.h -exec rm {} +;
	find $(1) -name *.pc -exec rm {} +;
endef

define Package/$(PKG_NAME)/config
	source "$(SOURCE)/Config.in"
endef

$(eval $(call BuildPackage,$(PKG_NAME)))


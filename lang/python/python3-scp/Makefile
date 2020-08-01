include $(TOPDIR)/rules.mk

PKG_NAME:=python3-scp
PKG_VERSION:=0.13.2
PKG_RELEASE:=1

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/jbardin/scp.py/archive
PKG_MD5SUM:=291eddf215d969fa9cf0ec95c27caaf9

PKG_BUILD_DIR:=$(BUILD_DIR)/scp.py-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python3

include $(INCLUDE_DIR)/package.mk
include ../python3-package.mk

define Package/python3-scp
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-scp
  URL:=https://github.com/jbardin/scp.py
  DEPENDS:=+python3 +python3-paramiko
  VARIANT:=python3
endef

define Package/python3-scp/description
 Native Python scp library 
endef

define Py3Build/Compile
	$(call Build/Compile/Py3Mod,, \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
	)
endef

$(eval $(call Py3Package,python3-scp))
$(eval $(call BuildPackage,python3-scp))
$(eval $(call BuildPackage,python3-scp-src))

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-paramiko
PKG_VERSION:=2.7
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/paramiko/paramiko/archive
PKG_MD5SUM:=420c2166543e170482aefa45e53b3e21

PKG_BUILD_DIR:=$(BUILD_DIR)/paramiko-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python3

include $(INCLUDE_DIR)/package.mk
include ../python3-package.mk
#$(call include_mk, python3-package.mk)

define Package/python3-paramiko
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-paramiko
  URL:=https://github.com/paramiko/paramiko
#  DEPENDS:=+python3
  VARIANT:=python3
endef

define Package/python3-paramiko/description
 Native Python SSHv2 protocol library 
endef

define Py3Build/Compile
	$(call Build/Compile/Py3Mod,, \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
	)
endef

$(eval $(call Py3Package,python3-paramiko))
$(eval $(call BuildPackage,python3-paramiko))

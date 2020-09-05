include $(TOPDIR)/rules.mk

PKG_NAME:=PyNaCl
PKG_VERSION:=1.4.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/cf/5a/25aeb636baeceab15c8e57e66b8aa930c011ec1c035f284170cacb05025e/PyNaCl-1.4.0.tar.gz
PKG_MD5SUM:=8c6c57893327a694c72510fb620e4744

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python3

HOST_PYTHON3_PACKAGE_BUILD_DEPENDS:="cffi>=1.4.1"

include $(INCLUDE_DIR)/package.mk
include ../python3-package.mk
$(call include_mk, python3-package.mk)

PYTHON3_PKG_SETUP_VARS:= SODIUM_INSTALL=system

#PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python3-pynacl
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-pynacl
  URL:=https://pypi.org/project/PyNaCl/
#  DEPENDS=+python3-light
  DEPENDS:=+python3-light +libsodium @!LIBSODIUM_MINIMAL +python3-cffi +python3-six
#  DEPENDS:=+python3 +libsodium +python3-cffi +python3-six
#  DEPENDS:=+python3 +libsodium @!LIBSODIUM_MINIMAL
#  DEPENDS+=+libsodium @!LIBSODIUM_MINIMAL
#  DEPENDS+=+libsodium
#  DEPENDS+= \
#      +PACKAGE_python3-pynacl:python3-light \
#      +PACKAGE_python3-pynacl:python3-cffi \
#      +PACKAGE_python3-pynacl:python3-six

#      +PACKAGE_python3-pynacl:libsodium @!LIBSODIUM_MINIMAL
  VARIANT:=python3
endef

define Package/python3-pynacl/description
 Python libsodium library 
endef

# define Py3Build/Compile
# 	$(call Build/Compile/Py3Mod,, \
# 		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
# 	)
# endef

$(eval $(call Py3Package,python3-pynacl))
$(eval $(call BuildPackage,python3-pynacl))
$(eval $(call BuildPackage,python3-pynacl-src))

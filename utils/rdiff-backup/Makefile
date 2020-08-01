#
# Copyright (C) 2006-2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
 
include $(TOPDIR)/rules.mk

PKG_NAME:=rdiff-backup
PKG_VERSION:=2.0.4rc0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/rdiff-backup/rdiff-backup/releases/download/v$(PKG_VERSION)/
PKG_MD5SUM:=d9d3fa48c607524de294cd006c17dd71

#PKG_BUILD_DEPENDS:=python

include $(INCLUDE_DIR)/package.mk
include ../../lang/python/python3-package.mk
#$(call include_mk, python3-package.mk)

define Package/rdiff-backup
  SUBMENU:=backup
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Incremental backup utility
  URL:=http://www.nongnu.org/rdiff-backup
  DEPENDS:=+python3 +librsync +libpopt +openssl-util
  VARIANT:=python3
endef

define Package/rdiff-backup/description
	rdiff-backup backs up one directory to another, possibly over a
	network. The target directory ends up a copy of the source directory,
	but extra reverse diffs are stored in a special subdirectory of that
	target directory, so you can still recover files lost some time ago.
	The idea is to combine the best features of a mirror and an incremental
	backup.
endef

define PyPackage/rdiff-backup/filespec
+|/usr/bin/rdiff-backup
+|$(PYTHON_PKG_DIR)/rdiff_backup
endef

define Py3Build/Compile
	@echo check
	$(if $(Build/Compile/Py3Mod),,@echo Python packaging code not found.; false)
	@echo build
	$(call Build/Compile/Py3Mod,., \
		build --librsync-dir="$(STAGING_DIR)/usr" , \
	)
#	$(call Build/Compile/Py3Mod,,install --prefix="/usr" --root="$(PKG_INSTALL_DIR)")
	@echo install
#	$(call Build/Compile/PyMod,., \
		install --prefix="$(PKG_INSTALL_DIR)/usr", \
	)
	$(call Build/Compile/Py3Mod,, \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)/usr", \
	)
endef

#define Package/rdiff-backup/install
#        $(INSTALL_DIR) $(1)/usr
#endef

$(eval $(call Py3Package,rdiff-backup))
$(eval $(call BuildPackage,rdiff-backup))

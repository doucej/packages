include $(TOPDIR)/rules.mk

PKG_NAME:=duplicity
PKG_VERSION:=0.8.14
PKG_RELEASE:=1
PKG_MAINTAINER:=Joe Doucette <doucej@gmail.com>
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://launchpad.net/duplicity/0.8-series/0.8.14/+download/
https://github.com/rdiff-backup/rdiff-backup/releases/download/v$(PKG_VERSION)/
PKG_HASH:=9af2f0aa5fb8986a5f6fdfcb50284976

include $(INCLUDE_DIR)/package.mk
include ../python3-package.mk

define Package/duplicity
  SUBMENU:=backup
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Incremental backup utility
  URL:=http://duplicity.nongnu.org
  DEPENDS:=+python3-light +librsync +libpopt +openssl-util +python3-boto3
  VARIANT:=python3
endef

define Package/duplicity/description
        Duplicity backs directories by producing encrypted tar-format volumes
        and uploading them to a remote or local file server. Because duplicity
        uses librsync, the incremental archives are space efficient and only
        record the parts of files that have changed since the last backup.
        Because duplicity uses GnuPG to encrypt and/or sign these archives,
        they will be safe from spying and/or modification by the server.
endef

define PyPackage/duplicity/filespec
+|/usr/bin/duplicity
+|$(PYTHON_PKG_DIR)/duplicity
endef

# define Py3Build/Compile
# 	@echo check
# 	$(if $(Build/Compile/Py3Mod),,@echo Python packaging code not found.; false)
# 	@echo build
# 	$(call Build/Compile/Py3Mod,., \
# 		build --librsync-dir="$(STAGING_DIR)/usr" , \
# 	)
# 	@echo install
# 	$(call Build/Compile/Py3Mod,, \
# 		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
# 	)
# endef

$(eval $(call Py3Package,duplicity))
$(eval $(call BuildPackage,duplicity))
$(eval $(call BuildPackage,duplicity-src))

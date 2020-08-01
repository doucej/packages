
include $(TOPDIR)/rules.mk

PKG_NAME:=librsync
PKG_VERSION:=2.3.1
PKG_RELEASE:=1

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/librsync/librsync/archive
PKG_MD5SUM:=9a9925b14b2919a1c8c6e2d9f13c9f0b

PKG_FIXUP:=libtool
PKG_INSTALL:=1
CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

TARGET_CFLAGS += $(FPIC)

define Package/librsync
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=implementation of the rolling-checksum algorithm
  URL:=https://github.com/librsync/librsync/archive
  DEPENDS:=+libbz2
endef

define Package/librsync/description
	librsync implements the rolling-checksum algorithm of remote file
	synchronization that was popularized by the rsync utility and is
	used in rproxy. This algorithm transfers the differences between 2
	files without needing both files on the same system.
endef

CMAKE_OPTIONS += \
	-DENABLE_TESTING:Bool=OFF \
	-DENABLE_PROGRAMS:Bool=ON

# define Build/Configure
# 	$(call Build/Configure/Default, \
# 		--enable-shared \
# 		--enable-static \
# 	);
# endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/librsync{,_export}.h $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/librsync.so* $(1)/usr/lib/
endef

define Package/librsync/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/librsync.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,librsync))

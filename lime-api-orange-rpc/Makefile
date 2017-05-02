#
# Copyright (C) 2017 LibreMesh.org
#
# This is free software, licensed under the GNU General Public License v3.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=lime-api-orange-rpc

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/libremesh/lime-api-orange-rpc.git
PKG_SOURCE_VERSION:=d29eb8d37b117b3962a52dce63c89b7cf5b03806
PKG_VERSION=$(GIT_COMMIT_DATE)-$(GIT_COMMIT_TSTAMP)
GIT_COMMIT_DATE:=$(shell git log -n 1 --pretty=%ad --date=short . )
GIT_COMMIT_TSTAMP:=$(shell git log -n 1 --pretty=%at . )

PKG_VERSION:=3.16.01-$(PKG_SOURCE_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_MIRROR_MD5SUM:=

PKG_LICENSE:=GPLv3+
PKG_LICENSE_FILES:=

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  CATEGORY:=LiMe
  TITLE:=lime-api-orange-rpc - provides the LibreMesh orange-rpcd api
  MAINTAINER:=Nicolas Echaniz <nicoechaniz@altermundi.net>
  DEPENDS:= +libiwinfo-lua +orange-rpcd
endef

define Package/$(PKG_NAME)/description
LibreMesh api for access through orange-rpcd:
 * provides the necessary api for the LibreMesh mobile and web app
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/
	$(CP) ./files/* $(1)/
endef

define Package/$(PKG_NAME)/postinst
#!/bin/sh

sed "\|.*last_internet_path.*|d" -i /etc/crontabs/root
echo "*/6 * * * * /usr/sbin/internet_path > /tmp/last_internet_path" >> /etc/crontabs/root

exit 0

endef


$(eval $(call BuildPackage,$(PKG_NAME)))

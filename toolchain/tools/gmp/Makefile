#
# Copyright (C) 2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=gmp
PKG_VERSION:=4.3.2

PKG_SOURCE_URL:=@GNU/gmp/
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_MD5SUM:=dd60683d7057917e34630b4a787932e8

include $(INCLUDE_DIR)/host-build.mk

unexport CFLAGS

ifeq ($(HOST_OS),Darwin)
  GNU_HOST_NAME:=
  HOST_CONFIGURE_ARGS:=$(filter-out --target= --build= --host=,$(HOST_CONFIGURE_ARGS))
endif

HOST_CONFIGURE_ARGS += \
        --enable-static \
        --disable-shared \
        --enable-cxx \
        --enable-mpbsd

define Build/Configure
        $(call Build/Configure/Default,\
	    $(HOST_CONFIGURE_ARGS) \
        )
endef

define Build/Install
        $(MAKE) -C $(PKG_BUILD_DIR) install
endef

$(eval $(call HostBuild))

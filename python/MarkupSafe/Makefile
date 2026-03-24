#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=MarkupSafe
PKG_VERSION:=1.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/4d/de/32d741db316d8fdb7680822dd37001ef7a448255de9699ab4bfcbdf4172b/
PKG_HASH:=a6be69091dac236ea9c6bc7d012beab42010fa914c459791d627dad4910eb665

HOST_BUILD_DEPENDS:=python/host

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-MarkupSafe-$(PKG_VERSION)

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Daniel Golle <daniel@makrotopia.org>

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)
HOST_UNPACK:=$(HOST_TAR) -C $(HOST_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python-MarkupSafe/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  URL:=https://pypi.python.org/pypi/six
endef

define Package/python-MarkupSafe
$(call Package/python-MarkupSafe/Default)
  TITLE:=python-MarkupSafe
  DEPENDS:=+PACKAGE_python-MarkupSafe:python-light
  VARIANT:=python
endef

define Package/python3-MarkupSafe
$(call Package/python-MarkupSafe/Default)
  TITLE:=python3-MarkupSafe
  DEPENDS:=+PACKAGE_python3-MarkupSafe:python3-light
  VARIANT:=python3
endef

define Package/python-MarkupSafe/description
MarkupSafe implements a XML/HTML/XHTML Markup safe string for Python
endef

define Package/python3-MarkupSafe/description
$(call Package/python-MarkupSafe/description)
.
(Variant for Python3)
endef

define Host/Compile
	$(call Build/Compile/HostPyMod,,install --prefix="" --root="$(STAGING_DIR_HOSTPKG)")
endef

Host/Install:=

$(eval $(call HostBuild))

$(eval $(call PyPackage,python-MarkupSafe))
$(eval $(call BuildPackage,python-MarkupSafe))
$(eval $(call BuildPackage,python-MarkupSafe-src))

$(eval $(call Py3Package,python3-MarkupSafe))
$(eval $(call BuildPackage,python3-MarkupSafe))
$(eval $(call BuildPackage,python3-MarkupSafe-src))

#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=Jinja2
PKG_VERSION:=2.10
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/source/J/Jinja2
PKG_HASH:=f84be1bb0040caca4cea721fcbbbbd61f9be9464ca236387158b0feea01914a4

HOST_BUILD_DEPENDS:=python/host

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-Jinja2-$(PKG_VERSION)

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Daniel Golle <daniel@makrotopia.org>

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)
HOST_UNPACK:=$(HOST_TAR) -C $(HOST_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python-Jinja2/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  URL:=https://pypi.python.org/pypi/six
endef

define Package/python-Jinja2
$(call Package/python-Jinja2/Default)
  TITLE:=python-Jinja2
  DEPENDS:=+PACKAGE_python-Jinja2:python-light
  VARIANT:=python
endef

define Package/python3-Jinja2
$(call Package/python-Jinja2/Default)
  TITLE:=python3-Jinja2
  DEPENDS:=+PACKAGE_python3-Jinja2:python3-light
  VARIANT:=python3
endef

define Package/python-Jinja2/description
Jinja2 is a full featured template engine for Python. It has full
unicode support, an optional integrated sandboxed execution
environment, widely used and BSD licensed.
endef

define Package/python3-Jinja2/description
$(call Package/python-Jinja2/description)
.
(Variant for Python3)
endef

define Host/Compile
	$(call Build/Compile/HostPyMod,,install --prefix="" --root="$(STAGING_DIR_HOSTPKG)")
endef

Host/Install:=

$(eval $(call HostBuild))

$(eval $(call PyPackage,python-Jinja2))
$(eval $(call BuildPackage,python-Jinja2))
$(eval $(call BuildPackage,python-Jinja2-src))

$(eval $(call Py3Package,python3-Jinja2))
$(eval $(call BuildPackage,python3-Jinja2))
$(eval $(call BuildPackage,python3-Jinja2-src))

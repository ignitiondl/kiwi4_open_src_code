#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-kconfiglib
PKG_VERSION:=13.1.1
PKG_RELEASE:=1

#PKG_SOURCE:=six-$(PKG_VERSION).tar.gz
#PKG_SOURCE_URL:=https://pypi.python.org/packages/16/d8/bc6316cf98419719bd59c91742194c111b6f2e85abac88e496adefaf7afe
#PKG_HASH:=70e8a77beed4562e7f14fe23a786b54f6296e34344c23bc42f07b15018ff98e9
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/ulfalizer/Kconfiglib.git
PKG_SOURCE_VERSION:=bf01114a0ce09b891ed04609ea7e9cc6f3ef3df2

HOST_BUILD_DEPENDS:=python/host

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-kconfiglib-$(PKG_VERSION)

#PKG_LICENSE:=MIT
#PKG_LICENSE_FILES:=LICENSE
#PKG_MAINTAINER:=Jeffery To <jeffery.to@gmail.com>, Alexandru Ardelean <ardeleanalex@gmail.com>

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

#PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)
#HOST_UNPACK:=$(HOST_TAR) -C $(HOST_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python-kconfiglib/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  URL:=https://github.com/ulfalizer/Kconfiglib
endef

define Package/python-kconfiglib
$(call Package/python-kconfiglib/Default)
  TITLE:=python-kconfiglib
  DEPENDS:=+PACKAGE_python-kconfiglib:python-light
  VARIANT:=python
endef

define Package/python3-kconfiglib
$(call Package/python3-kconfiglib/Default)
  TITLE:=python3-kconfiglib
  DEPENDS:=+PACKAGE_python3-kconfiglib:python3-light
  VARIANT:=python3
endef

define Package/python-kconfiglib/description
Kconfiglib is a Kconfig implementation in Python 2/3.
endef

define Package/python3-kconfiglib/description
$(call Package/python-kconfiglib/description)
.
(Variant for Python3)
endef

define Host/Compile
	$(call Build/Compile/HostPyMod,,install --prefix="" --root="$(STAGING_DIR_HOSTPKG)")
endef

Host/Install:=

$(eval $(call HostBuild))

$(eval $(call PyPackage,python-kconfiglib))
$(eval $(call BuildPackage,python-kconfiglib))
$(eval $(call BuildPackage,python-kconfiglib-src))

#$(eval $(call Py3Package,python3-kconfiglib))
#$(eval $(call BuildPackage,python3-kconfiglib))
#$(eval $(call BuildPackage,python3-kconfiglib-src))

#
# Copyright (C) 2007-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=django
PKG_VERSION:=1.11.17
PKG_RELEASE=4

PKG_SOURCE:=Django-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/source/D/Django
PKG_HASH:=a787ee66f4b4cf8ed753661cabcec603989677fa3a107fcb7f15511a44bdb483
PKG_BUILD_DIR=$(BUILD_DIR)/Django-$(PKG_VERSION)

PKG_MAINTAINER:=Alexandru Ardelean <ardeleanalex@gmail.com>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE LICENSE.python
PKG_CPE_ID:=cpe:/a:djangoproject:django

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-django-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/django/Default
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=The web framework for perfectionists with deadlines.
  URL:=https://www.djangoproject.com/
endef

define Package/python-django
$(call Package/django/Default)
  DEPENDS:= \
	+PACKAGE_python-django:python \
	+PACKAGE_python-django:python-pytz
  VARIANT:=python
endef

define Package/python-django/description
    The web framework for perfectionists with deadlines.
endef

define Package/python3-django
$(call Package/django/Default)
  DEPENDS:= \
	+PACKAGE_python3-django:python3 \
	+PACKAGE_python3-django:python3-pytz
  VARIANT:=python3
endef

define Package/python3-django/description
$(call Package/python-django/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-django))
$(eval $(call BuildPackage,python-django))

$(eval $(call Py3Package,python3-django))
$(eval $(call BuildPackage,python3-django))

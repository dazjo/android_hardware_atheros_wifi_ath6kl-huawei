#cfg80211
obj-m += cfg80211.o

cfg80211-y += core.o sysfs.o radiotap.o util.o reg.o scan.o nl80211.o
cfg80211-y += mlme.o ibss.o sme.o chan.o ethtool.o mesh.o
cfg80211-y += wext-compat.o wext-sme.o
cfg80211-y += regdb.o
#cfg80211-y += debugfs.o

ccflags-y += -D__CHECK_ENDIAN__
ccflags-y += -DCONFIG_CFG80211
ccflags-y += -DCONFIG_CFG80211_DEFAULT_PS
ccflags-y += -DCONFIG_CFG80211_WEXT
#ccflags-y += -DCONFIG_CFG80211_INTERNAL_REGDB
ccflags-y += -DCONFIG_NL80211_TESTMODE

ATH_ROOT = $(src)/..

ccflags-y += -I$(ATH_ROOT)/include
ccflags-y += -I$(ATH_ROOT)/cfg80211
ccflags-y += -include $(ATH_ROOT)/include/linux/ieee80211.h
ccflags-y += -include $(ATH_ROOT)/include/linux/nl80211.h
ccflags-y += -include $(ATH_ROOT)/include/net/cfg80211.h
ccflags-y += -include $(ATH_ROOT)/include/linux/compat-2.6.h

ldflags-y += --strip-debug

modules:
	$(MAKE) -C $(KERNEL_OUT) M=`pwd` ARCH=$(ARCH) CROSS_COMPILE=$(CROSS_COMPILE) modules

clean:
	$(MAKE) -C $(KERNEL_OUT) M=`pwd` ARCH=$(ARCH) CROSS_COMPILE=$(CROSS_COMPILE) clean

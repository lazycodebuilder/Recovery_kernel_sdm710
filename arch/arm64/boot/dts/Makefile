#ifndef VENDOR_EDIT
#PengNan@BSP.CHG.Basic 2019/03/15 modify for 18097
#dts-dirs += al
#dts-dirs += altera
#dts-dirs += amd
#dts-dirs += amlogic
#dts-dirs += apm
#dts-dirs += arm
#dts-dirs += broadcom
#dts-dirs += cavium
#dts-dirs += exynos
#dts-dirs += freescale
#dts-dirs += hisilicon
#dts-dirs += marvell
#dts-dirs += mediatek
#dts-dirs += nvidia
#dts-dirs += renesas
#dts-dirs += rockchip
#dts-dirs += socionext
#dts-dirs += sprd
#dts-dirs += xilinx
#dts-dirs += lg
#dts-dirs += zte
#else


ifeq ($(CONFIG_BRAND_SHOW_FLAG), realme)
dts-dirs += qcom

#endif
subdir-y	:= $(dts-dirs)

dtstree		:= $(srctree)/$(src)

dtb-$(CONFIG_OF_ALL_DTBS) := $(patsubst $(dtstree)/%.dts,%.dtb, $(foreach d,$(dts-dirs), $(wildcard $(dtstree)/$(d)/*.dts)))

always		:= $(dtb-y)

targets += dtbs

DTB_NAMES := $(subst $\",,$(CONFIG_BUILD_ARM64_APPENDED_DTB_IMAGE_NAMES))
ifneq ($(DTB_NAMES),)
DTB_LIST := $(addsuffix .dtb,$(DTB_NAMES))
else
DTB_LIST := $(dtb-y)
endif
targets += $(DTB_LIST)

dtbs: $(addprefix $(obj)/, $(DTB_LIST))

clean-files := dts/*.dtb *.dtb

#
# arch/m68knommu/Makefile
#
# This file is subject to the terms and conditions of the GNU General Public
# License.  See the file "COPYING" in the main directory of this archive
# for more details.
#
# (C) Copyright 2002, Greg Ungerer <gerg@snapgear.com>
#

KBUILD_DEFCONFIG := m5208evb_defconfig

platform-$(CONFIG_M68328)	:= 68328
platform-$(CONFIG_M68EZ328)	:= 68EZ328
platform-$(CONFIG_M68VZ328)	:= 68VZ328
platform-$(CONFIG_M68360)	:= 68360
platform-$(CONFIG_M5206)	:= 5206
platform-$(CONFIG_M5206e)	:= 5206e
platform-$(CONFIG_M520x)	:= 520x
platform-$(CONFIG_M523x)	:= 523x
platform-$(CONFIG_M5249)	:= 5249
platform-$(CONFIG_M527x)	:= 527x
platform-$(CONFIG_M5272)	:= 5272
platform-$(CONFIG_M528x)	:= 528x
platform-$(CONFIG_M5307)	:= 5307
platform-$(CONFIG_M532x)	:= 532x
platform-$(CONFIG_M5407)	:= 5407
PLATFORM := $(platform-y)

board-$(CONFIG_PILOT)		:= pilot
board-$(CONFIG_UC5272)          := UC5272
board-$(CONFIG_UC5282)          := UC5282
board-$(CONFIG_UCSIMM)		:= ucsimm
board-$(CONFIG_UCDIMM)		:= ucdimm
board-$(CONFIG_UCQUICC)		:= uCquicc
board-$(CONFIG_DRAGEN2)		:= de2
board-$(CONFIG_ARNEWSH)		:= ARNEWSH
board-$(CONFIG_FREESCALE)	:= FREESCALE
board-$(CONFIG_M5235EVB)	:= M5235EVB
board-$(CONFIG_M5271EVB)	:= M5271EVB
board-$(CONFIG_M5275EVB)	:= M5275EVB
board-$(CONFIG_M5282EVB)	:= M5282EVB
board-$(CONFIG_ELITE)		:= eLITE
board-$(CONFIG_NETtel)		:= NETtel
board-$(CONFIG_SECUREEDGEMP3)	:= MP3
board-$(CONFIG_CLEOPATRA)	:= CLEOPATRA
board-$(CONFIG_senTec)		:= senTec
board-$(CONFIG_SNEHA) 	        := SNEHA
board-$(CONFIG_M5208EVB)	:= M5208EVB
board-$(CONFIG_MOD5272)		:= MOD5272
board-$(CONFIG_AVNET)           := AVNET
board-$(CONFIG_SAVANT)		:= SAVANT
BOARD := $(board-y)

model-$(CONFIG_RAMKERNEL)	:= ram
model-$(CONFIG_ROMKERNEL)	:= rom
MODEL := $(model-y)

#
# Some code support is grouped together for a common cpu-subclass (for
# example all ColdFire cpu's are very similar). Determine the sub-class
# for the selected cpu. ONLY need to define this for the non-base member
# of the family.
#
cpuclass-$(CONFIG_M5206)	:= coldfire
cpuclass-$(CONFIG_M5206e)	:= coldfire
cpuclass-$(CONFIG_M520x)	:= coldfire
cpuclass-$(CONFIG_M523x)	:= coldfire
cpuclass-$(CONFIG_M5249)	:= coldfire
cpuclass-$(CONFIG_M527x)	:= coldfire
cpuclass-$(CONFIG_M5272)	:= coldfire
cpuclass-$(CONFIG_M528x)	:= coldfire
cpuclass-$(CONFIG_M5307)	:= coldfire
cpuclass-$(CONFIG_M532x)	:= coldfire
cpuclass-$(CONFIG_M5407)	:= coldfire
cpuclass-$(CONFIG_M68328)	:= 68328
cpuclass-$(CONFIG_M68EZ328)	:= 68328
cpuclass-$(CONFIG_M68VZ328)	:= 68328
cpuclass-$(CONFIG_M68360)	:= 68360
CPUCLASS := $(cpuclass-y)

ifneq ($(CPUCLASS),$(PLATFORM))
CLASSDIR := arch/m68knommu/platform/$(cpuclass-y)/
endif

export PLATFORM BOARD MODEL CPUCLASS

#
# Some CFLAG additions based on specific CPU type.
#
cflags-$(CONFIG_M5206)		:= $(call cc-option,-mcpu=5206,-m5200)
cflags-$(CONFIG_M5206e)		:= $(call cc-option,-m5206e,-m5200)
cflags-$(CONFIG_M520x)		:= $(call cc-option,-mcpu=5208,-m5200)
cflags-$(CONFIG_M523x)		:= $(call cc-option,-mcpu=523x,-m5307)
cflags-$(CONFIG_M5249)		:= $(call cc-option,-mcpu=5249,-m5200)
cflags-$(CONFIG_M5271)		:= $(call cc-option,-mcpu=5271,-m5307)
cflags-$(CONFIG_M5272)		:= $(call cc-option,-mcpu=5271,-m5200)
cflags-$(CONFIG_M5275)		:= $(call cc-option,-mcpu=5275,-m5307)
cflags-$(CONFIG_M528x)		:= $(call cc-option,-m528x,-m5307)
cflags-$(CONFIG_M5307)		:= $(call cc-option,-m5307,-m5200)
cflags-$(CONFIG_M532x)		:= $(call cc-option,-mcpu=532x,-m5307)
cflags-$(CONFIG_M5407)		:= $(call cc-option,-m5407,-m5200)
cflags-$(CONFIG_M68328)		:= -m68000
cflags-$(CONFIG_M68EZ328)	:= -m68000
cflags-$(CONFIG_M68VZ328)	:= -m68000
cflags-$(CONFIG_M68360)		:= -m68332

KBUILD_AFLAGS += $(cflags-y)

KBUILD_CFLAGS += $(cflags-y)
KBUILD_CFLAGS += -D__linux__
KBUILD_CFLAGS += -DUTS_SYSNAME=\"uClinux\"

head-y := arch/m68knommu/platform/$(cpuclass-y)/head.o

core-y	+= arch/m68knommu/kernel/ \
	   arch/m68knommu/mm/ \
	   $(CLASSDIR) \
	   arch/m68knommu/platform/$(PLATFORM)/
libs-y	+= arch/m68knommu/lib/

archclean:


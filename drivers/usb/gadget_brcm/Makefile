#
# USB peripheral controller drivers
#
ifeq ($(CONFIG_USB_GADGET_DEBUG),y)
	EXTRA_CFLAGS		+= -DDEBUG
endif


ifeq ($(CONFIG_USB_GADGET_DWC_OTG),y)
# EXTRA_CFLAGS			+= -DDEBUG -DDWC_DEVICE_ONLY
EXTRA_CFLAGS                  +=  -DDWC_DEVICE_ONLY
endif

obj-$(CONFIG_USB_DUMMY_HCD)	+= dummy_hcd.o
obj-$(CONFIG_USB_NET2280)	+= net2280.o
obj-$(CONFIG_USB_AMD5536UDC)	+= amd5536udc.o
obj-$(CONFIG_USB_PXA25X)	+= pxa25x_udc.o
obj-$(CONFIG_USB_PXA27X)	+= pxa27x_udc.o
obj-$(CONFIG_USB_GOKU)		+= goku_udc.o
obj-$(CONFIG_USB_OMAP)		+= omap_udc.o
obj-$(CONFIG_USB_LH7A40X)	+= lh7a40x_udc.o
obj-$(CONFIG_USB_S3C2410)	+= s3c2410_udc.o
obj-$(CONFIG_USB_DWC_OTG) := dwc_otg.o
dwc_otg-y			         := dwc_otg_driver.o dwc_otg_attr.o dwc_otg_cil.o dwc_otg_cil_intr.o dwc_otg_pcd.o dwc_otg_pcd_intr.o  dwc_otg_hcd.o dwc_otg_hcd_intr.o dwc_otg_hcd_queue.o
obj-$(CONFIG_USB_AT91)		+= at91_udc.o
obj-$(CONFIG_USB_ATMEL_USBA)	+= atmel_usba_udc.o
obj-$(CONFIG_USB_FSL_USB2)	+= fsl_usb2_udc.o
obj-$(CONFIG_USB_M66592)	+= m66592-udc.o

#
# USB gadget drivers
#
C_UTILS =	composite.o usbstring.o config.o epautoconf.o

g_zero-objs			:= zero.o f_sourcesink.o f_loopback.o $(C_UTILS)
g_ether-objs			:= ether.o u_ether.o f_subset.o f_ecm.o $(C_UTILS)

g_serial-objs			:= serial.o u_serial.o f_acm.o f_serial.o $(C_UTILS)
g_midi-objs			:= gmidi.o usbstring.o config.o epautoconf.o
gadgetfs-objs			:= inode.o
g_file_storage-objs		:= file_storage.o usbstring.o config.o \
					epautoconf.o
g_printer-objs			:= printer.o usbstring.o config.o \
					epautoconf.o
g_cdc-objs			:= cdc2.o u_ether.o f_ecm.o \
					u_serial.o f_acm.o $(C_UTILS)
g_android-objs		:= android.o f_adb.o f_mass_storage.o \
				u_serial.o f_acm.o f_obex.o u_ether.o $(C_UTILS)

ifeq ($(CONFIG_USB_ETH_RNDIS),y)
	g_ether-objs		+= f_rndis.o rndis.o 
	g_android-objs	+=  f_rndis.o rndis.o 
endif
 
obj-$(CONFIG_USB_ZERO)		+= g_zero.o
obj-$(CONFIG_USB_ETH)		+= g_ether.o
obj-$(CONFIG_USB_GADGETFS)	+= gadgetfs.o
obj-$(CONFIG_USB_FILE_STORAGE)	+= g_file_storage.o
obj-$(CONFIG_USB_G_SERIAL)	+= g_serial.o
obj-$(CONFIG_USB_G_PRINTER)	+= g_printer.o
obj-$(CONFIG_USB_MIDI_GADGET)	+= g_midi.o
obj-$(CONFIG_USB_CDC_COMPOSITE) += g_cdc.o
obj-$(CONFIG_USB_ANDROID)	+= g_android.o
obj-m += brcm_test_drv.o
obj-m += brcm_switch.o


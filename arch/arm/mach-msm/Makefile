obj-y += io.o memory.o

ifdef CONFIG_ARCH_MSM8X60
obj-y += dma-8x60.o timer-8x60.o clock-core.o clock-voter.o
obj-$(CONFIG_MSM_WATCHDOG) += msm_watchdog.o
obj-$(CONFIG_MSM_WATCHDOG) += htc_watchdog_monitor.o
else
obj-y += dma.o timer.o clock.o
endif

ifndef CONFIG_ARCH_MSM8X60
obj-y += irq.o devices.o pmic.o vreg.o
endif
obj-y += pwrtest.o
obj-$(CONFIG_ARCH_QSD8X50) += sirc.o
obj-y += proc_comm.o
obj-$(CONFIG_ARCH_MSM_ARM11) += acpuclock-arm11.o idle.o
obj-$(CONFIG_ARCH_QSD8X50) += arch-init-scorpion.o acpuclock-scorpion.o
obj-$(CONFIG_ARCH_MSM7X30) += acpuclock-7x30.o internal_power_rail.o
obj-$(CONFIG_ACPUCLOCK_DEBUG) += acpuclock_debug.o
obj-$(CONFIG_ARCH_MSM7X30) += clock-7x30.o arch-init-7x30.o socinfo.o
obj-$(CONFIG_ARCH_MSM7X30) += spm.o

ifdef CONFIG_ARCH_MSM8X60
obj-$(CONFIG_CPU_V7) += idle-v7-8x60.o msm_fault_handlers.o
else
obj-$(CONFIG_CPU_V7) += idle-v7.o msm_fault_handlers.o
endif

obj-y += nand_partitions.o
obj-y += drv_callback.o
obj-y += radio_feedback.o
obj-$(CONFIG_ARCH_QSD8X50) += pmic.o htc_wifi_nvs.o htc_bluetooth.o

obj-$(CONFIG_SMP) += headsmp.o platsmp.o
obj-$(CONFIG_ARCH_MSM8X60) += devices-msm8x60.o clock-local.o clock-8x60.o acpuclock-8x60.o clock-debug.o socinfo.o
obj-$(CONFIG_ARCH_MSM8X60) += clock-rpm.o spm.o restart.o mpm.o mpp.o
obj-$(CONFIG_ARCH_MSM8X60) += subsystem-fatal-8x60.o
obj-$(CONFIG_ARCH_MSM8X60) += saw-regulator.o
obj-$(CONFIG_ARCH_MSM8X60) += rpm-regulator.o
obj-$(CONFIG_ARCH_MSM8X60) += footswitch-8x60.o
obj-$(CONFIG_ARCH_MSM8X60) += sysinfo-8x60.o
ifeq ($(CONFIG_ARCH_MSM8X60_LTE),y)
obj-$(CONFIG_MSM_SCM) += scm-lte.o
else
obj-$(CONFIG_MSM_SCM) += scm.o
endif
obj-$(CONFIG_MSM_SCM) += scm-boot.o htc_simlock-8x60.o scm-log.o
obj-$(CONFIG_MSM_SECURE_IO) += scm-io.o
obj-$(CONFIG_MSM_PIL) += peripheral-loader.o
obj-$(CONFIG_MSM_PIL) += peripheral-reset.o
obj-$(CONFIG_MSM_DSPS) += msm_dsps.o
obj-$(CONFIG_MSM_FIQ_SUPPORT) += fiq_glue.o
obj-$(CONFIG_MACH_TROUT) += board-trout-rfkill.o

ifdef CONFIG_MSM_NONSMD_PACKET_FILTER
obj-$(CONFIG_MSM_SMD) += htc_port_list_lte.o
else
obj-$(CONFIG_MSM_SMD) += htc_port_list.o
endif

obj-$(CONFIG_ARCH_MSM7X30) += rpc_hsusb.o

obj-y += remote_spinlock.o

ifdef CONFIG_ARCH_MSM8X60
quiet_cmd_mkrpcsym = MKCAP   $@
	cmd_mkrpcsym = $(PERL) $(srctree)/$(src)/mkrpcsym.pl $< $@

target += smd_rpc_sym.c
$(obj)/smd_rpc_sym.c: $(src)/smd_rpc_sym $(src)/mkrpcsym.pl
	$(call if_changed,mkrpcsym)

ifeq ($(CONFIG_ARCH_MSM8X60_LTE),y)
obj-$(CONFIG_ARCH_MSM8X60_LTE) += 8x60-lte/
else
obj-y += modem_notifier.o
obj-$(CONFIG_MSM_SMD_LOGGING) += smem_log-8x60.o
obj-$(CONFIG_MSM_SMD) += smd-8x60.o smd_debug-8x60.o
obj-$(CONFIG_MSM_SMD_TTY) += smd_tty-8x60.o
obj-$(CONFIG_MSM_SMD_QMI) += smd_qmi-8x60.o

obj-$(CONFIG_MSM_SMD_PKT) += smd_pkt-8x60.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter-8x60.o
obj-$(CONFIG_MSM_SMD_NMEA) += smd_nmea-8x60.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_device-8x60.o
obj-$(CONFIG_DEBUG_FS) += smd_rpc_sym.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_servers-8x60.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_clients-8x60.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_xdr-8x60.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += rpcrouter_smd_xprt-8x60.o
endif

obj-$(CONFIG_MSM_RPC_PING) += ping_mdm_rpc_client-8x60.o ping_apps_server-8x60.o
obj-$(CONFIG_MSM_RPC_OEM_RAPI) += oem_rapi_client-8x60.o
obj-$(CONFIG_MSM_RPC_WATCHDOG) += rpc_dog_keepalive-8x60.o
obj-$(CONFIG_MSM_RPCSERVER_WATCHDOG) += rpc_server_dog_keepalive-8x60.o
obj-$(CONFIG_MSM_RPCSERVER_TIME_REMOTE) += rpc_server_time_remote-8x60.o
obj-$(CONFIG_MSM_RPCSERVER_HANDSET) += rpc_server_handset-8x60.o

else
# non MSM8X60 (MSM7x30, MSM7x30_LTE, QSD8X50)

ifeq ($(CONFIG_ARCH_MSM7X30_LTE),y)
obj-$(CONFIG_ARCH_MSM7X30_LTE) += 7x30-lte/
else
# non MSM8X60/MSM7x30_LTE (MSM7x30, QSD8X50)
obj-$(CONFIG_ARCH_MSM7X30) += rpc_pmapp.o smd_rpcrouter_clients.o
obj-$(CONFIG_MSM_SMD) += smd.o smd_debug.o
obj-$(CONFIG_MSM_SMD) += smem_log.o
obj-$(CONFIG_MSM_SMD) += last_radio_log.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_device.o

ifdef CONFIG_PROC_COMM_7X30
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter-7x30.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_servers-7x30.o
else
ifndef CONFIG_ARCH_MSM7X30
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_servers.o
else
# non MSM8X60/MSM7X30/MSM7x30_LTE (QSD8X50)
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter-7x30.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_servers-7x30.o
endif
endif

obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_xdr.o
obj-$(CONFIG_MSM_RPCSERVERS) += rpc_server_dog_keepalive.o
obj-$(CONFIG_MSM_RPCSERVERS) += rpc_server_time_remote.o
obj-$(CONFIG_MSM_SMD) += smd_tty.o smd_qmi.o
endif
endif

obj-$(CONFIG_MSM_DALRPC) += dal.o
obj-$(CONFIG_MSM_DALRPC_TEST) += dal_remotetest.o
obj-$(CONFIG_ARCH_MSM7X30) += dal_axi.o
obj-$(CONFIG_MSM_ADSP) += qdsp5/
obj-$(CONFIG_MSM_ADSP_COMP) += qdsp5_comp/
obj-$(CONFIG_MSM7KV2_AUDIO) += qdsp5v2/
obj-$(CONFIG_MSM7KV2_1X_AUDIO) += qdsp5v2_1x/
obj-$(CONFIG_QSD_AUDIO) += qdsp6/
obj-$(CONFIG_MSM8X60_AUDIO) += qdsp6v2/
obj-$(CONFIG_MSM8X60_AUDIO) += htc_acoustic_8x60.o
obj-$(CONFIG_MSM8X60_AUDIO_LTE) += qdsp6v3/
obj-$(CONFIG_MSM8X60_AUDIO_LTE) += htc_acoustic_8x60.o
obj-$(CONFIG_MSM_HW3D) += hw3d.o

ifdef CONFIG_PM
	ifdef CONFIG_ARCH_MSM8X60
		obj-y += pm-8x60.o
	else
		obj-y += pm.o
	endif
endif

ifdef CONFIG_ARCH_MSM8X60
	obj-$(CONFIG_CPU_IDLE) += cpuidle.o
endif

obj-$(CONFIG_CPU_FREQ) += cpufreq.o

ifndef CONFIG_ARCH_MSM8X60
obj-$(CONFIG_HTC_ACOUSTIC) += htc_acoustic.o
endif

obj-$(CONFIG_HTC_ACOUSTIC_QSD) += htc_acoustic_qsd.o
obj-$(CONFIG_MSM7KV2_AUDIO) += htc_acoustic_7x30.o htc_acdb_7x30.o
obj-$(CONFIG_MSM7KV2_1X_AUDIO) += htc_acoustic_7x30.o htc_acdb_7x30.o
obj-$(CONFIG_SENSORS_AKM8976) += htc_akm_cal.o

obj-$(CONFIG_MACH_MAHIMAHI) += board-mahimahi.o board-mahimahi-panel.o
obj-$(CONFIG_MACH_MAHIMAHI) += board-mahimahi-keypad.o board-mahimahi-mmc.o
obj-$(CONFIG_MACH_MAHIMAHI) += board-mahimahi-rfkill.o htc_wifi_nvs.o
obj-$(CONFIG_MACH_MAHIMAHI) += board-mahimahi-wifi.o board-mahimahi-audio.o
obj-$(CONFIG_MACH_MAHIMAHI) += msm_vibrator.o
obj-$(CONFIG_MACH_MAHIMAHI) += board-mahimahi-microp.o
obj-$(CONFIG_MACH_MAHIMAHI) += htc_acoustic_qsd.o
obj-$(CONFIG_MACH_MAHIMAHI) += board-mahimahi-flashlight.o

obj-$(CONFIG_MACH_INCREDIBLEC) += board-incrediblec.o panel-samsungwvga-tl2796a.o panel-sonywvga-s6d16a0x21.o board-incrediblec-tv.o
obj-$(CONFIG_MACH_INCREDIBLEC) += board-incrediblec-keypad.o board-incrediblec-mmc.o
obj-$(CONFIG_MACH_INCREDIBLEC) += board-incrediblec-rfkill.o board-incrediblec-audio.o
obj-$(CONFIG_MACH_INCREDIBLEC) += board-incrediblec-wifi.o htc_awb_cal.o
obj-$(CONFIG_MACH_INCREDIBLEC) += board-incrediblec-microp.o
obj-$(CONFIG_MACH_INCREDIBLEC) += proc_engineerid.o
obj-$(CONFIG_MACH_SUPERSONIC) += board-supersonic.o board-supersonic-panel.o
obj-$(CONFIG_MACH_SUPERSONIC) += board-supersonic-keypad.o board-common-wimax.o board-supersonic-mmc.o
obj-$(CONFIG_MACH_SUPERSONIC) += board-supersonic-rfkill.o board-supersonic-audio.o
obj-$(CONFIG_MACH_SUPERSONIC) += board-supersonic-wifi.o htc_awb_cal.o
obj-$(CONFIG_MACH_SUPERSONIC) += board-supersonic-microp.o
obj-$(CONFIG_MACH_OBOEA) += board-oboea.o board-oboea-panel.o
obj-$(CONFIG_MACH_OBOEA) += board-oboea-keypad.o board-common-wimax.o board-oboea-mmc.o
obj-$(CONFIG_MACH_OBOEA) += board-oboea-rfkill.o board-oboea-audio.o
obj-$(CONFIG_MACH_OBOEA) += board-oboea-wifi.o htc_awb_cal.o
obj-$(CONFIG_MACH_OBOEA) += board-oboea-microp.o
obj-$(CONFIG_MACH_OBOEA) += board-oboea-gsm-radio.o
obj-$(CONFIG_MACH_BRAVO) += board-bravo.o panel-samsungwvga-tl2796a.o panel-sonywvga-s6d16a0x21.o
obj-$(CONFIG_MACH_BRAVO) += board-bravo-keypad.o board-bravo-mmc.o
obj-$(CONFIG_MACH_BRAVO) += board-bravo-rfkill.o
obj-$(CONFIG_MACH_BRAVO) += board-bravo-audio.o board-bravo-wifi.o htc_awb_cal.o
obj-$(CONFIG_MACH_BRAVO) += board-bravo-microp.o
obj-$(CONFIG_MACH_BRAVOC) += board-bravoc.o panel-samsungwvga-tl2796a.o panel-sonywvga-s6d16a0x21.o
obj-$(CONFIG_MACH_BRAVOC) += board-bravoc-keypad.o board-bravoc-mmc.o
obj-$(CONFIG_MACH_BRAVOC) += board-bravoc-rfkill.o board-bravoc-audio.o
obj-$(CONFIG_MACH_BRAVOC) += board-bravoc-wifi.o htc_awb_cal.o
obj-$(CONFIG_MACH_BRAVOC) += board-bravoc-microp.o

# MSM7x30 boards
obj-$(CONFIG_ARCH_MSM7X30) += panel-samsungwvga-tl2796a.o panel-samsungwvga-s6e63m0.o panel-sonywvga-s6d16a0x21-7x30.o
obj-$(CONFIG_ARCH_MSM7X30) += htc_wifi_nvs.o htc_awb_cal.o
obj-$(CONFIG_MACH_VISION)+= board-vision.o
obj-$(CONFIG_MACH_VISION)+= board-vision-keypad.o
obj-$(CONFIG_MACH_VISION)+= board-vision-microp.o
obj-$(CONFIG_MACH_VISION)+= board-vision-audio.o
obj-$(CONFIG_MACH_VISION)+= board-vision-mmc.o board-vision-wifi.o
obj-$(CONFIG_MACH_VISION)+= board-vision-rfkill.o htc_bluetooth.o

obj-$(CONFIG_MACH_LEXIKON)+= board-lexikon.o
obj-$(CONFIG_MACH_LEXIKON)+= board-lexikon-keypad.o
obj-$(CONFIG_MACH_LEXIKON)+= board-lexikon-microp.o
obj-$(CONFIG_MACH_LEXIKON)+= board-lexikon-audio.o
obj-$(CONFIG_MACH_LEXIKON)+= board-lexikon-mmc.o board-lexikon-wifi.o
obj-$(CONFIG_MACH_LEXIKON)+= board-lexikon-rfkill.o
obj-$(CONFIG_MACH_LEXIKON)+= board-lexikon-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_LEXIKONCT)+= board-lexikonct.o
obj-$(CONFIG_MACH_LEXIKONCT)+= board-lexikonct-keypad.o
obj-$(CONFIG_MACH_LEXIKONCT)+= board-lexikonct-microp.o
obj-$(CONFIG_MACH_LEXIKONCT)+= board-lexikonct-audio.o
obj-$(CONFIG_MACH_LEXIKONCT)+= board-lexikonct-mmc.o board-lexikonct-wifi.o
obj-$(CONFIG_MACH_LEXIKONCT)+= board-lexikonct-rfkill.o
obj-$(CONFIG_MACH_LEXIKONCT)+= board-lexikonct-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_SPEEDY)+= board-speedy.o
obj-$(CONFIG_MACH_SPEEDY)+= board-speedy-keypad.o
obj-$(CONFIG_MACH_SPEEDY)+= board-speedy-microp.o
obj-$(CONFIG_MACH_SPEEDY)+= board-speedy-audio.o
obj-$(CONFIG_MACH_SPEEDY)+= board-common-wimax.o board-speedy-mmc.o board-speedy-wifi.o
obj-$(CONFIG_MACH_SPEEDY)+= board-speedy-rfkill.o
obj-$(CONFIG_MACH_SPEEDY)+= board-speedy-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_KINGDOM)+= board-kingdom.o
obj-$(CONFIG_MACH_KINGDOM)+= board-kingdom-keypad.o
obj-$(CONFIG_MACH_KINGDOM)+= board-kingdom-microp.o
obj-$(CONFIG_MACH_KINGDOM)+= board-kingdom-audio.o
obj-$(CONFIG_MACH_KINGDOM)+= board-common-wimax.o board-kingdom-mmc.o board-kingdom-wifi.o
obj-$(CONFIG_MACH_KINGDOM)+= board-kingdom-rfkill.o
obj-$(CONFIG_MACH_KINGDOM)+= board-kingdom-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_MECHA)+= board-mecha.o
obj-$(CONFIG_MACH_MECHA)+= board-mecha-keypad.o
obj-$(CONFIG_MACH_MECHA)+= board-mecha-microp.o
obj-$(CONFIG_MACH_MECHA)+= board-mecha-audio.o
obj-$(CONFIG_MACH_MECHA)+= board-mecha-mmc.o board-mecha-wifi.o
obj-$(CONFIG_MACH_MECHA)+= board-mecha-rfkill.o
obj-$(CONFIG_MACH_MECHA)+= board-mecha-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_GLACIER)+= board-glacier.o
obj-$(CONFIG_MACH_GLACIER)+= board-glacier-keypad.o
obj-$(CONFIG_MACH_GLACIER)+= board-glacier-microp.o
obj-$(CONFIG_MACH_GLACIER)+= board-glacier-audio.o
obj-$(CONFIG_MACH_GLACIER)+= board-glacier-mmc.o board-glacier-wifi.o
obj-$(CONFIG_MACH_GLACIER)+= board-glacier-rfkill.o
obj-$(CONFIG_MACH_GLACIER)+= htc_fmtx_rfkill.o
obj-$(CONFIG_MACH_GLACIER)+= board-glacier-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_SAGA)+= board-saga.o
obj-$(CONFIG_MACH_SAGA)+= board-saga-keypad.o
obj-$(CONFIG_MACH_SAGA)+= board-saga-audio.o
obj-$(CONFIG_MACH_SAGA)+= board-saga-mmc.o board-saga-wifi.o
obj-$(CONFIG_MACH_SAGA)+= board-saga-rfkill.o
obj-$(CONFIG_MACH_SAGA)+= htc_fmtx_rfkill.o
obj-$(CONFIG_MACH_SAGA)+= board-saga-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_ICON)+= board-icon.o
obj-$(CONFIG_MACH_ICON)+= board-icon-keypad.o
obj-$(CONFIG_MACH_ICON)+= board-icon-audio.o
obj-$(CONFIG_MACH_ICON)+= board-icon-mmc.o board-icon-wifi.o
obj-$(CONFIG_MACH_ICON)+= board-icon-rfkill.o
obj-$(CONFIG_MACH_ICON)+= htc_fmtx_rfkill.o
obj-$(CONFIG_MACH_ICON)+= board-icon-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_SPADE)+= board-spade.o
obj-$(CONFIG_MACH_SPADE)+= board-spade-keypad.o
obj-$(CONFIG_MACH_SPADE)+= board-spade-microp.o
obj-$(CONFIG_MACH_SPADE)+= board-spade-audio.o
obj-$(CONFIG_MACH_SPADE)+= board-spade-mmc.o board-spade-wifi.o htc_awb_cal.o
obj-$(CONFIG_MACH_SPADE)+= board-spade-rfkill.o htc_bluetooth.o board-spade-panel.o

obj-$(CONFIG_MACH_FLYER)+= board-flyer.o
obj-$(CONFIG_MACH_FLYER)+= board-flyer-keypad.o
obj-$(CONFIG_MACH_FLYER)+= board-flyer-microp.o
obj-$(CONFIG_MACH_FLYER)+= board-flyer-audio.o
obj-$(CONFIG_MACH_FLYER)+= board-flyer-mmc.o board-flyer-wifi.o htc_awb_cal.o
obj-$(CONFIG_MACH_FLYER)+= board-flyer-rfkill.o htc_bluetooth.o board-flyer-panel.o

obj-$(CONFIG_MACH_EXPRESS)+= board-express.o panel-lgwsvga-ld070ws1-7x30.o
obj-$(CONFIG_MACH_EXPRESS)+= board-express-keypad.o
obj-$(CONFIG_MACH_EXPRESS)+= board-express-microp.o
obj-$(CONFIG_MACH_EXPRESS)+= board-express-audio.o
obj-$(CONFIG_MACH_EXPRESS)+= board-common-wimax.o board-express-mmc.o board-express-wifi.o htc_awb_cal.o
obj-$(CONFIG_MACH_EXPRESS)+= board-express-rfkill.o htc_bluetooth.o board-express-panel.o

obj-$(CONFIG_MACH_EXPRESS_KT)+= board-express-kt.o panel-lgwsvga-ld070ws1-7x30.o
obj-$(CONFIG_MACH_EXPRESS_KT)+= board-express-kt-keypad.o
obj-$(CONFIG_MACH_EXPRESS_KT)+= board-express-kt-microp.o
obj-$(CONFIG_MACH_EXPRESS_KT)+= board-express-kt-audio.o
obj-$(CONFIG_MACH_EXPRESS_KT)+= board-common-wimax.o board-express-kt-mmc.o board-express-kt-wifi.o htc_awb_cal.o
obj-$(CONFIG_MACH_EXPRESS_KT)+= board-express-kt-rfkill.o htc_bluetooth.o board-express-kt-panel.o

obj-$(CONFIG_MACH_EXPRESS_H)+= board-express-h.o panel-lgwsvga-ld070ws1-7x30.o
obj-$(CONFIG_MACH_EXPRESS_H)+= board-express-h-keypad.o
obj-$(CONFIG_MACH_EXPRESS_H)+= board-express-h-microp.o
obj-$(CONFIG_MACH_EXPRESS_H)+= board-express-h-audio.o
obj-$(CONFIG_MACH_EXPRESS_H)+= board-express-h-mmc.o board-express-h-wifi.o htc_awb_cal.o
obj-$(CONFIG_MACH_EXPRESS_H)+= board-express-h-rfkill.o htc_bluetooth.o board-express-h-panel.o

obj-$(CONFIG_MACH_DYNASTY)+= board-dynasty.o
obj-$(CONFIG_MACH_DYNASTY)+= board-dynasty-keypad.o
obj-$(CONFIG_MACH_DYNASTY)+= board-dynasty-microp.o
obj-$(CONFIG_MACH_DYNASTY)+= board-dynasty-mmc.o board-dynasty-wifi.o htc_awb_cal.o
obj-$(CONFIG_MACH_DYNASTY)+= board-dynasty-rfkill.o htc_bluetooth.o

obj-$(CONFIG_MACH_VIVO)+= board-vivo.o
obj-$(CONFIG_MACH_VIVO)+= board-vivo-keypad.o
obj-$(CONFIG_MACH_VIVO)+= board-vivo-audio.o
obj-$(CONFIG_MACH_VIVO)+= board-vivo-mmc.o board-vivo-wifi.o
obj-$(CONFIG_MACH_VIVO)+= board-vivo-rfkill.o
obj-$(CONFIG_MACH_VIVO)+= board-vivow-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_VIVOW)+= board-vivow.o
obj-$(CONFIG_MACH_VIVOW)+= board-vivow-keypad.o
obj-$(CONFIG_MACH_VIVOW)+= board-vivow-audio.o
obj-$(CONFIG_MACH_VIVOW)+= board-vivow-mmc.o board-vivow-wifi.o
obj-$(CONFIG_MACH_VIVOW)+= board-vivow-rfkill.o
obj-$(CONFIG_MACH_VIVOW)+= board-vivow-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_VIVOW_CT)+= board-vivow.o
obj-$(CONFIG_MACH_VIVOW_CT)+= board-vivow-keypad.o
obj-$(CONFIG_MACH_VIVOW_CT)+= board-vivow-audio.o
obj-$(CONFIG_MACH_VIVOW_CT)+= board-vivow-mmc.o board-vivow-wifi.o
obj-$(CONFIG_MACH_VIVOW_CT)+= board-vivow-rfkill.o
obj-$(CONFIG_MACH_VIVOW_CT)+= board-vivow-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_TAG)+= board-tag.o
obj-$(CONFIG_MACH_TAG)+= board-tag-keypad.o
obj-$(CONFIG_MACH_TAG)+= board-tag-audio.o
obj-$(CONFIG_MACH_TAG)+= board-tag-mmc.o board-tag-wifi.o
obj-$(CONFIG_MACH_TAG)+= board-tag-rfkill.o
obj-$(CONFIG_MACH_TAG)+= board-tag-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_TAGH)+= board-tagh.o
obj-$(CONFIG_MACH_TAGH)+= board-tagh-keypad.o
obj-$(CONFIG_MACH_TAGH)+= board-tagh-audio.o
obj-$(CONFIG_MACH_TAGH)+= board-tagh-mmc.o board-tagh-wifi.o
obj-$(CONFIG_MACH_TAGH)+= board-tagh-rfkill.o
obj-$(CONFIG_MACH_TAGH)+= board-tagh-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_BLISS)+= board-bliss.o
obj-$(CONFIG_MACH_BLISS)+= board-bliss-keypad.o
obj-$(CONFIG_MACH_BLISS)+= board-bliss-audio.o
obj-$(CONFIG_MACH_BLISS)+= board-bliss-mmc.o board-bliss-wifi.o
obj-$(CONFIG_MACH_BLISS)+= htc_sleep_clk.o htc_fast_clk_7k.o board-bliss-rfkill.o
obj-$(CONFIG_MACH_BLISS)+= board-bliss-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_BLISSC)+= board-blissc.o
obj-$(CONFIG_MACH_BLISSC)+= board-blissc-keypad.o
obj-$(CONFIG_MACH_BLISSC)+= board-blissc-audio.o
obj-$(CONFIG_MACH_BLISSC)+= board-blissc-mmc.o board-blissc-wifi.o
obj-$(CONFIG_MACH_BLISSC)+= htc_sleep_clk.o htc_fast_clk_7k.o board-blissc-rfkill.o
obj-$(CONFIG_MACH_BLISSC)+= board-blissc-panel.o htc_bluetooth.o

obj-$(CONFIG_MACH_RUNNYMEDE)+= board-runnymede.o
obj-$(CONFIG_MACH_RUNNYMEDE)+= board-runnymede-keypad.o
obj-$(CONFIG_MACH_RUNNYMEDE)+= board-runnymede-audio.o
obj-$(CONFIG_MACH_RUNNYMEDE)+= board-runnymede-mmc.o board-runnymede-wifi.o
obj-$(CONFIG_MACH_RUNNYMEDE)+= htc_sleep_clk.o board-runnymede-rfkill.o htc_bdaddress.o
obj-$(CONFIG_MACH_RUNNYMEDE)+= board-runnymede-panel.o htc_bluetooth.o

# MSM7200A boards
obj-$(CONFIG_MACH_HERO) += board-hero.o board-hero-panel.o board-hero-keypad.o
obj-$(CONFIG_MACH_HERO) += board-hero-rfkill.o
obj-$(CONFIG_MACH_HERO) += board-hero-mmc.o board-hero-wifi.o htc_wifi_nvs.o htc_awb_cal.o

# MSM7225 boards
obj-$(CONFIG_MACH_BUZZ) += board-buzz.o board-buzz-panel.o board-buzz-keypad.o board-buzz-microp.o
obj-$(CONFIG_MACH_BUZZ) += board-buzz-rfkill.o board-buzz-mmc.o board-buzz-wifi.o
obj-$(CONFIG_MACH_BEE) += board-bee.o board-bee-panel.o board-bee-keypad.o board-bee-microp.o
obj-$(CONFIG_MACH_BEE) += board-bee-rfkill.o board-bee-mmc.o board-bee-wifi.o

# MSM7227 boards
obj-$(CONFIG_MACH_LEGEND) += board-legend-rfkill.o
obj-$(CONFIG_MACH_LEGEND) += board-legend.o board-legend-keypad.o board-legend-panel.o
obj-$(CONFIG_MACH_LEGEND) += board-legend-mmc.o board-legend-wifi.o board-legend-microp.o
obj-$(CONFIG_MACH_LATTE) += board-latte-rfkill.o
obj-$(CONFIG_MACH_LATTE) += board-latte.o board-latte-keypad.o board-latte-panel.o
obj-$(CONFIG_MACH_LATTE) += board-latte-mmc.o board-latte-wifi.o board-latte-microp.o
obj-$(CONFIG_MACH_LIBERTY) += board-liberty-rfkill.o htc_bluetooth.o
obj-$(CONFIG_MACH_LIBERTY) += board-liberty.o board-liberty-keypad.o board-liberty-panel.o
obj-$(CONFIG_MACH_LIBERTY) += board-liberty-mmc.o board-liberty-wifi.o board-liberty-microp.o
obj-$(CONFIG_MACH_MARVEL) += board-marvel-rfkill.o htc_bluetooth.o
obj-$(CONFIG_MACH_MARVEL) += board-marvel.o board-marvel-keypad.o board-marvel-panel.o
obj-$(CONFIG_MACH_MARVEL) += board-marvel-mmc.o board-marvel-wifi.o board-marvel-microp.o
obj-$(CONFIG_MACH_MARVELC) += board-marvelc-rfkill.o htc_bluetooth.o
obj-$(CONFIG_MACH_MARVELC) += board-marvelc.o board-marvelc-keypad.o board-marvelc-panel.o
obj-$(CONFIG_MACH_MARVELC) += board-marvelc-mmc.o board-marvelc-wifi.o board-marvelc-microp.o
obj-$(CONFIG_MACH_ICONG) += board-icong-rfkill.o htc_bluetooth.o
obj-$(CONFIG_MACH_ICONG) += board-icong.o board-icong-keypad.o board-icong-panel.o
obj-$(CONFIG_MACH_ICONG) += board-icong-mmc.o board-icong-wifi.o board-icong-microp.o
obj-$(CONFIG_MACH_CHACHA) += board-chacha-rfkill.o htc_bluetooth.o
obj-$(CONFIG_MACH_CHACHA) += board-chacha.o board-chacha-keypad.o board-chacha-panel.o
obj-$(CONFIG_MACH_CHACHA) += board-chacha-mmc.o board-chacha-wifi.o board-chacha-microp.o

# MSM7600 boards
obj-$(CONFIG_MACH_DESIREC) += board-desirec.o board-desirec-panel.o board-desirec-keypad.o
obj-$(CONFIG_MACH_DESIREC) += board-desirec-rfkill.o
obj-$(CONFIG_MACH_DESIREC) += board-desirec-mmc.o board-desirec-wifi.o htc_wifi_nvs.o
obj-$(CONFIG_MACH_HEROC) += board-heroc.o board-heroc-panel.o board-heroc-keypad.o
obj-$(CONFIG_MACH_HEROC) += board-heroc-rfkill.o
obj-$(CONFIG_MACH_HEROC) += board-heroc-mmc.o board-heroc-wifi.o htc_wifi_nvs.o

# MSM8x60 boards
obj-$(CONFIG_MACH_PYRAMID) += board-pyramid.o
obj-$(CONFIG_MACH_PYRAMID) += board-pyramid-keypad.o
obj-$(CONFIG_MACH_PYRAMID) += board-pyramid-audio.o
obj-$(CONFIG_MACH_PYRAMID) += htc_bdaddress.o htc_sleep_clk.o board-pyramid-rfkill.o
obj-$(CONFIG_MACH_PYRAMID) += board-pyramid-mmc.o board-pyramid-wifi.o
obj-$(CONFIG_MACH_PYRAMID) += display/pyramid-panel.o
obj-$(CONFIG_MACH_SHOOTER) += board-shooter.o board-shooter-audio.o
obj-$(CONFIG_MACH_SHOOTER) += htc_bdaddress.o htc_sleep_clk.o board-shooter-rfkill.o
obj-$(CONFIG_MACH_SHOOTER) += board-common-wimax.o board-shooter-mmc.o board-shooter-wifi.o
obj-$(CONFIG_MACH_SHOOTER) += board-shooter-keypad.o
obj-$(CONFIG_MACH_SHOOTER) += display/shooter-panel.o
obj-$(CONFIG_MACH_SHOOTER_CT) += board-shooter_ct.o board-shooter_ct-audio.o
obj-$(CONFIG_MACH_SHOOTER_CT) += htc_bdaddress.o htc_sleep_clk.o board-shooter_ct-rfkill.o
obj-$(CONFIG_MACH_SHOOTER_CT) += board-shooter_ct-mmc.o board-shooter_ct-wifi.o
obj-$(CONFIG_MACH_SHOOTER_CT) += board-shooter_ct-keypad.o
obj-$(CONFIG_MACH_SHOOTER_CT) += display/shooter_ct-panel.o
obj-$(CONFIG_MACH_RIDER) += board-rider.o
obj-$(CONFIG_MACH_RIDER) += board-rider-audio.o
obj-$(CONFIG_MACH_RIDER) += htc_bdaddress.o htc_sleep_clk.o board-rider-rfkill.o
obj-$(CONFIG_MACH_RIDER) += board-common-wimax.o board-rider-mmc.o board-rider-wifi.o
obj-$(CONFIG_MACH_RIDER) += board-rider-keypad.o
obj-$(CONFIG_MACH_RIDER) += display/rider-panel.o
obj-$(CONFIG_MACH_SHOOTER_K) += board-shooter_k.o board-shooter_k-audio.o
obj-$(CONFIG_MACH_SHOOTER_K) += htc_bdaddress.o htc_sleep_clk.o board-shooter_k-rfkill.o
obj-$(CONFIG_MACH_SHOOTER_K) += board-common-wimax.o board-shooter_k-mmc.o board-shooter_k-wifi.o
obj-$(CONFIG_MACH_SHOOTER_K) += board-shooter_k-keypad.o
obj-$(CONFIG_MACH_SHOOTER_K) += display/shooter_k-panel.o
obj-$(CONFIG_MACH_SHOOTER_U) += board-shooter_u.o board-shooter_u-audio.o
obj-$(CONFIG_MACH_SHOOTER_U) += htc_bdaddress.o htc_sleep_clk.o board-shooter_u-rfkill.o
obj-$(CONFIG_MACH_SHOOTER_U) += board-shooter_u-mmc.o board-shooter_u-wifi.o
obj-$(CONFIG_MACH_SHOOTER_U) += board-shooter_u-keypad.o
obj-$(CONFIG_MACH_SHOOTER_U) += display/shooter_u-panel.o
obj-$(CONFIG_MACH_DOUBLESHOT) += board-doubleshot.o
obj-$(CONFIG_MACH_DOUBLESHOT) += board-doubleshot-audio.o
obj-$(CONFIG_MACH_DOUBLESHOT) += board-doubleshot-keypad.o
obj-$(CONFIG_MACH_DOUBLESHOT) += board-doubleshot-microp.o
obj-$(CONFIG_MACH_DOUBLESHOT) += htc_bdaddress.o htc_sleep_clk.o board-doubleshot-rfkill.o htc_fmtx_rfkill.o
obj-$(CONFIG_MACH_DOUBLESHOT) += board-doubleshot-mmc.o board-doubleshot-wifi.o
obj-$(CONFIG_MACH_DOUBLESHOT) += display/doubleshot-panel.o
obj-$(CONFIG_MACH_LEAD) += board-lead.o
obj-$(CONFIG_MACH_LEAD) += board-lead-audio.o
obj-$(CONFIG_MACH_LEAD) += board-lead-keypad.o
obj-$(CONFIG_MACH_LEAD) += htc_bdaddress.o htc_sleep_clk.o board-lead-rfkill.o htc_fmtx_rfkill.o
obj-$(CONFIG_MACH_LEAD) += board-lead-mmc.o board-lead-wifi.o
obj-$(CONFIG_MACH_VERDI) += board-verdi.o
obj-$(CONFIG_MACH_VERDI) += board-verdi-keypad.o
obj-$(CONFIG_MACH_VERDI) += board-verdi-audio.o
obj-$(CONFIG_MACH_VERDI) += htc_bdaddress.o htc_sleep_clk.o board-verdi-rfkill.o
obj-$(CONFIG_MACH_VERDI) += board-verdi-mmc.o board-verdi-wifi.o
obj-$(CONFIG_MACH_VERDI_LTE) += board-verdi-lte.o
obj-$(CONFIG_MACH_VERDI_LTE) += board-verdi-lte-keypad.o
obj-$(CONFIG_MACH_VERDI_LTE) += board-verdi-lte-audio.o
obj-$(CONFIG_MACH_VERDI_LTE) += htc_bdaddress.o htc_sleep_clk.o board-verdi-lte-rfkill.o
obj-$(CONFIG_MACH_VERDI_LTE) += board-verdi-lte-mmc.o board-verdi-lte-wifi.o
obj-$(CONFIG_MACH_VERDI_LTE) += htc_simhotswap.o
obj-$(CONFIG_MACH_HOLIDAY) += board-holiday.o
obj-$(CONFIG_MACH_HOLIDAY) += board-holiday-audio.o
obj-$(CONFIG_MACH_HOLIDAY) += board-holiday-keypad.o
obj-$(CONFIG_MACH_HOLIDAY) += display/holiday-panel.o
obj-$(CONFIG_MACH_HOLIDAY) += htc_bdaddress.o htc_sleep_clk.o board-holiday-rfkill.o htc_fmtx_rfkill.o
obj-$(CONFIG_MACH_HOLIDAY) += board-holiday-mmc.o board-holiday-wifi.o
obj-$(CONFIG_MACH_VIGOR) += board-vigor.o
obj-$(CONFIG_MACH_VIGOR) += board-vigor-audio.o
obj-$(CONFIG_MACH_VIGOR) += board-vigor-keypad.o
obj-$(CONFIG_MACH_VIGOR) += htc_bdaddress.o htc_sleep_clk.o board-vigor-rfkill.o htc_fmtx_rfkill.o
obj-$(CONFIG_MACH_VIGOR) += board-vigor-mmc.o board-vigor-wifi.o
obj-$(CONFIG_MACH_RUBY) += board-ruby.o
obj-$(CONFIG_MACH_RUBY) += board-ruby-audio.o
obj-$(CONFIG_MACH_RUBY) += board-ruby-keypad.o
obj-$(CONFIG_MACH_RUBY) += display/ruby-panel.o
obj-$(CONFIG_MACH_RUBY) += htc_bdaddress.o htc_sleep_clk.o htc_fast_clk_8k.o board-ruby-rfkill.o
obj-$(CONFIG_MACH_RUBY) += board-ruby-mmc.o board-ruby-wifi.o

obj-$(CONFIG_ARCH_MSM7X00A) += msm_vibrator.o devices_htc.o
obj-$(CONFIG_ARCH_MSM7225) += msm_vibrator.o devices_htc.o htc_wifi_nvs.o htc_awb_cal.o htc_bluetooth.o
obj-$(CONFIG_ARCH_MSM7227) += msm_vibrator.o devices_htc.o htc_wifi_nvs.o htc_awb_cal.o
obj-$(CONFIG_ARCH_QSD8X50) += msm_vibrator.o devices_htc.o
obj-$(CONFIG_ARCH_MSM7X30) += msm_vibrator.o devices_htc.o
obj-$(CONFIG_ARCH_MSM8X60) += devices_htc.o htc_wifi_nvs.o htc_awb_cal.o
obj-$(CONFIG_ARCH_MSM_FLASHLIGHT) += msm_flashlight.o

obj-$(CONFIG_TROUT_BATTCHG_DOCK) += htc_one_wire.o
obj-$(CONFIG_TROUT_BATTCHG) += htc_battery_trout.o
obj-$(CONFIG_HTC_BATTCHG) += htc_battery.o
obj-$(CONFIG_HTC_BATT_CORE) += htc_battery_core.o
obj-$(CONFIG_HTC_BATT8x60) += htc_battery_8x60.o
obj-$(CONFIG_HTC_PWRSINK) += htc_pwrsink.o
obj-$(CONFIG_MSM_RMT_STORAGE_SERVER) += rmt_storage_server.o
#
# wait for user-space rmt_storage daemon ready
ifeq ($(CONFIG_ARCH_MSM8X60),y)
obj-$(CONFIG_MSM_RMT_STORAGE_CLIENT) += rmt_storage_client-8x60.o
else
obj-$(CONFIG_MSM_RMT_STORAGE_CLIENT) += rmt_storage_client.o
endif
ifeq ($(CONFIG_MSM_SSBI),y)
obj-$(CONFIG_PMIC8058) += pmic8058-mpp.o
else
ifeq ($(CONFIG_ARCH_MSM8X60),y)
obj-$(CONFIG_PMIC8058) += pmic8058-gpio-8x60.o pmic8058-mpp-8x60.o
else
obj-$(CONFIG_PMIC8058) += pmic8058-gpio.o pmic8058-mpp.o
endif
endif
obj-$(CONFIG_MSM_NPA) += npa.o npa_resources.o msm_pm_qos.o msm_reqs.o
obj-$(CONFIG_MSM_NPA_REMOTE) += npa_remote.o
obj-$(CONFIG_MSM_NPA_REMOTE_ONCRPC) += npa_remote_rpc_client.o

obj-$(CONFIG_PERFLOCK) += perflock.o
obj-$(CONFIG_PERFLOCK) += htc_set_perflock.o
obj-$(CONFIG_MICROP_COMMON) += atmega_microp_common.o
obj-$(CONFIG_TOUCHSCREEN_TSSC_MANAGER) += htc_tp_cal.o

obj-$(CONFIG_HTC_HEADSET_MGR) += htc_headset_mgr.o
obj-$(CONFIG_HTC_HEADSET_H2W) += htc_headset_h2w.o
obj-$(CONFIG_HTC_HEADSET_GPIO) += htc_headset_gpio.o
obj-$(CONFIG_HTC_HEADSET_MICROP) += htc_headset_microp.o
obj-$(CONFIG_HTC_HEADSET_PMIC) += htc_headset_pmic.o
obj-$(CONFIG_HTC_HEADSET_MISC) += htc_headset_misc.o
obj-$(CONFIG_HTC_HEADSET_8X60) += htc_headset_8x60.o

obj-$(CONFIG_HTC_EXTDIAG) += htc_extdiag.o

obj-$(CONFIG_HTC_ACCESSORY_ONEWIRE) += htc_onewire.o

obj-$(CONFIG_MSM_RPM) += rpm.o rpm_resources.o
obj-$(CONFIG_MSM_RPM_STATS_LOG) += rpm_stats.o
obj-$(CONFIG_MSM_RPM_LOG) += rpm_log.o
obj-$(CONFIG_MSM_XO) += msm_xo.o
obj-$(CONFIG_MSM_BUS_SCALING)	+= msm_bus_core.o msm_bus_fabric.o msm_bus_board_8660.o
ifdef CONFIG_MSM_BUS_SCALING
obj-$(CONFIG_DEBUG_FS) += msm_bus_dbg.o
endif

obj-$(CONFIG_SMMU)		+= iommu.o iommu_dev.o
obj-$(CONFIG_SMMU_8X60)		+= devices-msm8x60-iommu.o

ifdef CONFIG_VCM
obj-$(CONFIG_ARCH_MSM8X60) += board-msm8x60-vcm.o
endif

obj-$(CONFIG_ARCH_MSM8X60) += gpiomux-8x60.o gpiomux-v2.o gpiomux.o
ifdef CONFIG_MSM_V2_TLMM
obj-y	+= gpio-v2.o
else
obj-y	+= gpio.o generic_gpio.o
endif
obj-$(CONFIG_MSM_SLEEP_STATS) += msm_sleep_stats.o
obj-$(CONFIG_MSM_SHOW_RESUME_IRQ) += msm_show_resume_irq.o
obj-$(CONFIG_MACH_MAHIMAHI) += board-mahimahi-tpa2018d1.o
obj-$(CONFIG_MACH_MAHIMAHI) += board-mahimahi-smb329.o

obj-$(CONFIG_ARCH_MSM_SCORPION) += pmu.o
obj-$(CONFIG_ARCH_MSM_SCORPIONMP) += pmu.o

ifeq ($(CONFIG_ARCH_MSM8X60),y)
obj-$(CONFIG_MSM8X60_SSBI) += ssbi_8x60.o
else
obj-$(CONFIG_MSM_SSBI) += ssbi.o
endif

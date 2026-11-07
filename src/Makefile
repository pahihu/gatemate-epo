IMAGE = risk.img
CP = cp

all: load-bin prom.mem

Modules.bin: Modules/Kernel.Mod Modules/Files.Mod Modules/FileDir.Mod Modules/Modules.Mod $(IMAGE)
	$(RM) $@
	(cd Modules; omake)
	$(CP) Modules/$@ .

load-bin: Modules.bin $(IMAGE)
	ORL Load Modules.bin $(IMAGE)

# prom.mem: prom/prom.mod
# 	$(RM) $@
# 	(cd prom; omake)
# 	$(CP) prom/$@ .
prom.mem: BootLoad/BootLoad.mem
	$(RM) $@
	$(CP) BootLoad/BootLoad.mem $@
	unix2dos $@

BootLoad/BootLoad.mem: BootLoad/BootLoad.Mod
	(cd BootLoad; omake BootLoad.mem)

risk.img: $(ADIR)/EO/RISC.img
	$(RM) $@
	$(CP) $< $@

boot: Modules.bin prom.mem
	ORTool0 Execute prom.mem/sv

clean:
	$(RM) Modules.bin prom.mem
	$(RM) Oberon.Log
	(cd BootLoad; omake clean)
	(cd Modules; omake clean)

# vim:set ts=2 sw=2 noet:

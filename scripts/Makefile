PREFIX=/usr
ETCDIR=/etc

# locate the config directory of the init system
SYSTEMD := $(shell ls -d $(DESTDIR)$(ETCDIR)/systemd/system 2>/dev/null | sed "s@^$(DESTDIR)@@g")
SYSVINIT := $(shell ls -d $(DESTDIR)$(ETCDIR)/init.d 2>/dev/null | sed "s@^$(DESTDIR)@@g")

all:
	@echo "'make install' to install scripts"

install:
# conditionally install init services
ifdef SYSVINIT
	install -d $(DESTDIR)$(SYSVINIT)
	install -m 0755 piaware-rc-script $(DESTDIR)$(SYSVINIT)/piaware
endif
ifdef SYSTEMD
	install -d $(DESTDIR)$(SYSTEMD)
	install piaware.service $(DESTDIR)$(SYSTEMD)/piaware.service
endif

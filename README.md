# dvb-config
Config files and shell scripts to enable multicast distribution of Saorview DVB muxes on a lan, using a couple of RTLSDR DVB-T USB sticks, dvblast and minisapserver.

#installaction/usage

1. Install dependencies

`apt install dvb-apps dvblast w-scan minisapserver`

2. edit `bin/mux1.sh` and `bin/mux2.sh` to reflect actual frequencies of those muxes in your area (see transmitters for a hint, or use a dvb scanning tool)

3. edit config/*.service files for the correct paths and copy to `/lib/systemd/system/`

4. run `sudo systemctl enable` for each service to start at boot time.

5. edit /etc/default/minisapserver:

	DAEMON_OPTS="-f /PATH TO PROJECT/saorview-dvb-config/config/sap.cfg"
	RUN="yes"
6. reboot

7. Using VLC on another computer on the same LAN, select a stream from the items in ' Network streams (SAP)'

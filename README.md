# pi-kvf  
Stroyming av KVF til RPI

RPI imager (set wifi config, set default brúkaranavn til "user" og okkurt rímuligt password)

Raspberry PI 4 - Raspberry Pi OS Lite (64Bit)

sudo apt install vlc --no-install-recommends

sudo nano /etc/systemd/system/kvf.service

[Unit]  
Description=Start Video Playback at Boot Time  
After=network.target  

[Service]  
ExecStartPre=/bin/sleep 10   
ExecStart=cvlc -f --play-and-exit --no-video-title-show rtmp://live.kringvarp.fo/kvf/_definst_/1080.stream --loop   
Restart=on-failure  
RestartSec=5  
User=user  

[Install]  
WantedBy=multi-user.target  


sudo systemctl daemon-reload  
sudo systemctl enable kvf.service  
sudo systemctl restart kvf.service  

apt install watchdog  
systemctl enable watchdog  

check watchdog device status:  
wdctl  

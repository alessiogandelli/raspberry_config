# raspberry_config

## connect to raspberry 
use [ZeroTier](https://my.zerotier.com) create an account and connect your raspberry and your pc 

- install zerotier 
- connect to network
- approve device on web app

ssh@the.ip.you.find



its main purpose is to keep alive different telegram bots

in the folder **telegram_bot** there are all the cloned repository 

in the folder **scripts** there is one bash script for each bot 

## Running on boot 
i want theese scripts run when i turn on the raspberry i have used systemd


 create the file 
 
		sudo nano /lib/systemd/system/chess.service

paste in that file 

		[Unit]
		Description=whateveryouwant
		After=network.target
		[Service]
		ExecStart=/home/pi/dev/script/yourscript.sh
		Restart=always
		Restart=on-failure
		RestartSec=30s
		User=pi
		[Install]
		WantedBy=multi-user.target

 enable it 
 
		sudo systemctl enable bottana.service


try it 

		sudo systemctl start chess.service
		sudo systemctl stop chess.service

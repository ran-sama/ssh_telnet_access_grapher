# ssh_telnet_access_grapher
Display attacks against your server in a graphic CIDR block representation (test logged 76000 attacks originating from 10804 unique IPs, duplicate lines removed).

![alt text](https://raw.githubusercontent.com/ran-sama/ssh_telnet_access_grapher/master/images/example_updated.png)
![alt text](https://raw.githubusercontent.com/ran-sama/ssh_telnet_access_grapher/master/images/diagram.png)

## Build the ipv4-heatmap binary:
```
git clone https://github.com/hrbrmstr/ipv4-heatmap
```

## Add the required lines to your (user) crontab:
sudo crontab -u pi -e
```
@reboot python /home/pi/ssh.py &
@reboot python /home/pi/telnet.py &
```

## Run the heatmapper .sh-file with watch if you prefer:
```
tmux new -s watch
watch -n 1800 ./heatmapper.sh
```

## Experimental
Only optional for using multiprocessing, log with:
```
python combined.py >> /media/mystick/combined.txt
```
Generate PNG:
```
#!/bin/bash
ipv4-heatmap -i -P viridis -f ~/LiberationSans-Regular.ttf -a classful.annotations -o /media/mystick/combined.png < /media/mystick/combined.txt
exit 0
```

## License
Licensed under the WTFPL license.

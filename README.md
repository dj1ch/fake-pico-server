# fake-pico-server
## a raspberry pi pico honeypot, that pretends to be a linux server.

### Intro
This pretends to be a debian 12 server. I would host this on some sort of port for your server, but as soon as attackers log in they will be put into a serial shell(hosted on your own server), which is on the raspberry pi pico. It will troll them by saying "command not found" as they attempt to do things on it. After a couple seconds, the pico will start counting, really fast. This might confuse the attacker. If you want to, you can mess with the python to make it a server using the pico w, although I use the regular pico. 

### What you need
- a raspberry pi pico
- circuitpython firmware
- another pc to copy the files onto the pico

### Install guide
- download the code.py from the [releases tab](/releases)
- copy them onto the pico
- plug the pico into your server
- set a cronjob to run `minicom -D /dev/ttyACM0` (minicom must be installed, along with user in dialout group)
ex:
```shell 
@reboot minicom -D /dev/ttyACM0
```
- wait for the light on the pico to turn on and stay on, as this means the 'troll' is running

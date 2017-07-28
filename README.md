# radiCALe_respawner
radiCALe 1.1.x respawner script 

### what?
an init.d script to check if radiCALe daemon is accepting SSL connections: if not, it kills and respawns the process  
tested on 1.1.x, it uses openSSL and works only if 'ssl=true' in radicale/config

### why?
radiCALe is a CalDAV and CardDAV server  
as many of you have experienced, radiCALe daemon may freeze randomly after some time: when (sh)it happens, only way is to kill -9 it and restart  
the only way to avoid this issue is to run it behind a dedicated web server  

as I am running it on a cheap nas (dns-320L with alt-f firmware) which simply hasn't the cpu power to run an httpd, I modified an user posted init.d script with a respawn function  
then I put everything in crontab to make sure it can be restarted every hour  

### install
edit as you wish 
put the script in /etc/init.d/ and chmod +x
set up a cronjob (recommended every hour): 
```
/etc/init.d/S80radicale respawn
```
to suppress info/error messages add:
```
>/dev/null 2>/dev/null
```

### links
http://radicale.org  
http://github.com/Kozea/Radicale/issues/266  
thanks to the author of original post:
http://groups.google.com/forum/#!topic/alt-f/vGUpfxmpfuQ  

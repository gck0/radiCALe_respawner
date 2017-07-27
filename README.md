# radiCALe_respawner
radiCALe 1.1.x/SSL init.d respawner script

tested on 1.1.x, works only if using SSL

radiCALe is a CalDAV and CardDAV server
as many of you have experienced, radiCALe daemon may freeze after some time when not running behind a dedicated web server: when (sh)it happens, only way is to kill -9 it and restart

as I am running it on a cheap nas which simply hasn't the cpu power to run an httpd, I modified an user posted init.d with a respawn function
then I put everything in crontab to make sure it can be restarted every hour

the respawn function uses openssl to check if the daemon accepts connections, so it does work only if radicale uses ssl

### install
edit as you wish
put the script in /etc/init.d/
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
http://groups.google.com/forum/#!topic/alt-f/vGUpfxmpfuQ  

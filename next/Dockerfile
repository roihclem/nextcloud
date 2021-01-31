#take nextcloud official image
FROM nextcloud:18.0.3-apache


#install ARIA2S
RUN apt-get update ; \
   apt-get install aria2 sudo; \
   mkdir /var/log/aria2c /var/local/aria2c; \
   touch /var/log/aria2c/aria2c.log; \
   touch /var/local/aria2c/aria2c.sess; \
   chown www-data.www-data -R /var/log/aria2c /var/local/aria2c; \
   chmod 770 -R /var/log/aria2c /var/local/aria2c; \
   sudo -u www-data aria2c \
       --enable-rpc \
       --rpc-allow-origin-all \
       -c \
       -D \
       --log=/var/log/aria2c/aria2c.log \
       --check-certificate=false \
       --save-session=/var/local/aria2c/aria2c.sess \
       --save-session-interval=2 \
       --continue=true \
       --input-file=/var/local/aria2c/aria2c.sess \
       --rpc-save-upload-metadata=true \
       --force-save=true \
       --log-level=warn \
       --rpc-listen-all=false

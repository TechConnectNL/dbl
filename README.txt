INSTALL:

sudo -i
cd /config/scripts
curl 'https://community.ubnt.com/ubnt/attachments/ubnt/USG/66463/17/getBlacklistHosts.V8.3.zip' > getBlacklistHosts.zip

unzip getBlacklistHosts.zip

rm getBlacklistHosts.zip

chmod +x getBlacklistHosts.sh

./getBlacklistHosts.sh

From here, edit getBlacklistHosts.conf and add/edit dnswhitelist.txt, file after that:
./getBlacklistHosts.sh

Don't forget to install config.gateway.json

Removal:
sudo -i
configure
delete system task-scheduler task hostblacklist
commit
save
exit

sudo -i
rm /etc/dnsmasq.d/blackhost*
/etc/init.d/dnsmasq force-reload
exit

sudo -i
rm /var/log/getBlackListHosts.log
rm /config/scripts/dnswhitelist
rm /config/scripts/dnsblacklist
rm /config/scripts/getBlacklistHosts.oldcount
rm /config/scripts/getBlacklistHosts.currentcount
rm /config/scripts/BlacklistHistoryCount.txt
rm /config/scripts/getBlacklistHosts.sh
rm /config/scripts/getBlacklistHosts.conf
rm /config/scripts/nonFilteredHosts
rm /config/scripts/filteredHosts
rm /config/scripts/finalHosts
rm /tmp/tmp.gzippedhosts.tar.gz
rm /etc/dnsmasq.d/getBlacklistOptions.conf
rm /config/scripts/getBlacklistPostRun.sh
exit

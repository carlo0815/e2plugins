+ **EPG - download & replace**

   - simple enigma2 plugin to download & replace '/etc/enigma2/epg.dat' file
   - best would be to upload '/etc/enigma2/epg.dat' file to some free file hosting server from another set-top box, where the EPG-Refresh plugin is always active to create fresh EPG data for all channels (not just those that the set-top box user has watched over the last few days)
   - to upload '/etc/enigma2/epg.dat' file to some server, for example once every 2-3 days, it is advisable to use the bash script 'epg_upload.sh', which is located in the plugin folder - schedule it to run via CRON service eg. every night or after completing the EPG-Refresh plugin task
   - How-To install the plugin EpgDownloadReplace:
   ``` 
       plugin_dir=/usr/lib/enigma2/python/Plugins/Extensions/EpgDownloadReplace
       mkdir -p $plugin_dir $plugin_dir/images
       for f in plugin.py __init__.py; do
         wget -O $plugin_dir/$f --no-check-certificate https://github.com/s3n0/e2plugins/raw/master/EpgDownloadReplace/src/$f
       done
       for f in plugin.png btn_red.png btn_green.png btn_yellow.png btn_blue.png ; do
         wget -O $plugin_dir/images/$f --no-check-certificate https://github.com/s3n0/e2plugins/raw/master/EpgDownloadReplace/src/images/$f
       done
       init 4 && sleep 5 && init 3
   ```
   - How-To remove the plugin EpgDownloadReplace:
   ``` 
       rm -fr /usr/lib/enigma2/python/Plugins/Extensions/EpgDownloadReplace
       init 4 && sleep 5 && init 3
   ```

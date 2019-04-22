# netscaler-ansible-backup
Automatic backup &amp; export for Citrix NetScaler

Most tasks are run through REST API (ansible's _uri_ module). Exporting the file is done via _ssh_citrix_adc_ because no similar API functionality exists currently.

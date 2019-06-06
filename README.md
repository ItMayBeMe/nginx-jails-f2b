# A collection of Fail2Ban jails for Nginx

This repo contains a collection of filters to match certain criteria in Nginx logs.



## Enabling a jail

To enable a jail, first copy the filter `.conf` file into your *filter.d* directory, an then create a configuration file in your *jail.d* directory and add the jail you want.

For example, to enable the `nginx-badbots` jail, create a file named `nginx-badbots.conf` in Fail2Ban's jail.d directory, and add the following :

```ini
[nginx-badbots]

enabled  = true
port     = http,https
# This line is not required anymore in the latest f2b releases
filter   = nginx-badbots
logpath  = /var/log/nginx/*access.log
# The number of time a given IP may match the filter during `bantime` seconds before
# being banned
maxretry = 1
# The duration of the ban in seconds (86400 seconds is equal to 24 hours)
bantime = 86400

```

After enabling the jail, don't forget to reload Fail2Ban with `sudo fail2ban-client reload`



## Requesting a new filter

If you need a filter that is not present in this repo, you can always open an issue, and I will maybe create it.

You way as well submit your own filters through push requests.


# Exodus Mobile App Tracker DNS block list 

Tracker domains exported from https://etip.exodus-privacy.eu.org/trackers/all, deduplicated and staged for importation as a AdGuard DNS Filter list. The majority of this list should block the most prolific mobile application advertising, user-tracking and usage-reporting endpoints. 
 
## Installation

Should be able to add [this list's raw](https://raw.githubusercontent.com/Tuathghal/Exodus-MobileApp-Trackers-DNS-List/refs/heads/main/Trackers-Cleaned.txt) in the AdGuard DNS filter GUI. However, as it scales, you'll likely need to SSH into your router or DNS server, stop the AdGuard service, wget your list in ```/etc/AdGuardHome/data/filters```, rename it a memorable number like ```mv Trackers-Cleaned.txt 67.txt```, then ```cd ../..``` to get back to ```/etc/AdGuardHome/``` and reference ```id: 67``` when defining the new tracker list in the ```config.yaml```. 

For GL.iNet routers, follow [this helpful post](https://www.reddit.com/r/Adguard/comments/1di09ch/psa_glinet_router_ax1300_slate_with_firmware_4516/).

So ```config.yaml``` should look like:

```
 filters:                                                                                      

  - enabled: true                                                                             

url: https://adguardteam.github.io/AdGuardSDNSFilter/Filters/filter.txt

name: AdGuard DNS filter                                                                  

id: 1                                                                                     

  - enabled: true                                                                             

url: https://cdn.jsdelivr.net/gh/hagezi/dns-blocklists@latest/adblock/light.txt

name: Hagezi Pro DNS filter                                                               

id: 2   

. . .

url: https://raw.githubusercontent.com/Tuathghal/Exodus-MobileApp-Trackers-DNS-List/refs/heads/main/Trackers-Cleaned.txt

name: Tuathghal's Exdous Mobile App Tracker DNS blocklist

id: 67

```

## Updating

I'll update periodically; my workflow is really just exporting the master list from Exodus, data-preparing and then deconflicting and merging anything new.

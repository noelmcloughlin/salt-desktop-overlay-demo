# Demonstration: salt-desktop integration

status: immature

# Salt

Bootstrap salt if necessary.
```
curl -o salter.sh https://raw.githubusercontent.com/saltstack-formulas/salt-desktop/master/installer.sh && sudo bash salter.sh -i bootstrap && sudo bash salter.sh -i salt `
```

# Procedure

1. Fork your salt-project.
   
   For the demo I used a random, but excellent, salt-project at: https://github.com/eligundry/salt.eligundry.com and renamed repo as "salt-desktop-overlay-demo" to avoid confusion.

2. Make your repo compatible with salter
```
 git clone https://github.com/noelmcloughlin/salt.eligundry.com salt-desktop-overlay-demo
 cd salt-desktop-overlay-demo/
 mv pillar configs/
 mv salt profiles
 mkdir scripts/
 curl -o scripts/overlay-salt.sh https://raw.githubusercontent.com/saltstack-formulas/salt-desktop/master/contrib/overlay-salt.sh
 curl -o scripts/installer.sh https://raw.githubusercontent.com/saltstack-formulas/salt-desktop/master/installer.sh
```

3. Overlay salt-desktop
```
sudo bash ./scripts/overlay-salt.sh
```

# Use salt-desktop

The overlay script copied your states/pillars here:
```
    vi ./scripts/installer.sh

    ..etc..
    ### YOUR STUFF HERE ###
    your['states']="${SALTFS}/community/your/file_roots"
    your['pillars']="${SALTFS}/community/your/pillar_roots"
```

Now your states are available (demo)-
` sudo salter.sh -i 'media-center' -u eligundry `


References:
 1. salt.eligundry.com: https://github.com/noelmcloughlin/salt.eligundry.com
 2. salt-desktop guide: https://github.com/saltstack-formulas/salt-desktop/blob/master/README.rst#integration-recommendation

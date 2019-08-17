# Demonstration: salter integration

status: immature

# Salt

Bootstrap salt if necessary.
```
curl -o salter.sh https://raw.githubusercontent.com/saltstack-formulas/salter/master/installer.sh && sudo bash salter.sh -i bootstrap && sudo bash salter.sh -i salt `
```

# Procedure

1. Fork your salt-project.
   
   For the demo I used a random, but excellent, salt-project at: https://github.com/eligundry/salt.eligundry.com and renamed repo as "salter-overlay-demo" to avoid confusion.

2. Make repo compatible with salter
```
 git clone https://github.com/noelmcloughlin/salt.eligundry.com salter-overlay-demo
 cd salter-overlay-demo/
 mv pillar configs/
 mv salt profiles
 mkdir scripts/
 curl -o scripts/overlay-salt.sh https://raw.githubusercontent.com/saltstack-formulas/salter/master/contrib/overlay-salt.sh
 curl -o scripts/installer.sh https://raw.githubusercontent.com/saltstack-formulas/salter/master/installer.sh
```

3. Overlay salter
```
sudo bash ./scripts/overlay-salt.sh
```

# Use salter

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
 2. salter guide: https://github.com/saltstack-formulas/salter/blob/master/README.rst#integration-recommendation

#------------------------------------------
# Demonstration: salt-desktop integration
#------------------------------------------
status: immature

1. Fork your salt-project - this exercise uses https://github.com/eligundry/salt.eligundry.com

2. Overlay salt-destkop manually

```
 git clone https://github.com/noelmcloughlin/salt.eligundry.com
 cd salt.eligundry.com/
 mv pillar configs/
 mv salt profiles
 mkdir scripts/
 curl -o scripts/overlay-salt.sh https://raw.githubusercontent.com/saltstack-formulas/salt-desktop/master/contrib/overlay-salt.sh
 curl -o scripts/installer.sh https://raw.githubusercontent.com/saltstack-formulas/salt-desktop/master/installer.sh
```

3. Personalize your project:

```
    vi ./scripts/installerr.sh

    ... etc ...
    solution['entity']="eligundry"
    solution['repo']="salt.eligundry.com"
    solution['alias']="eligundry"
    solution['targets']="linux-desktop|linux|mac|media-center|server|shared|thinkpad"
```

4. Commit and push.

5. Now ensure salt-desktop is integrated into your system
```
curl -o salter.sh https://raw.githubusercontent.com/noelmcloughlin/salt.eligundry.com/master/scripts/installer.sh && sudo bash salter.sh -i bootstrap && sudo bash salter.sh -i salt `
```

You can now use salt-desktop to run you states-

```
sudo salter.sh -i 'media-center' -u eligundry
```


References:
 1. salt.eligundry.com: https://github.com/noelmcloughlin/salt.eligundry.com
 2. salt-desktop guide: https://github.com/saltstack-formulas/salt-desktop/blob/master/README.rst#integration-recommendation

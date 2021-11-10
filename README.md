# dxatscale release log

# November 21

## [sfpowerkit](https://github.com/Accenture/sfpowerkit/)

v3.3.4 features the following fixes and enhancements

### ⭐ : Enhancements
- feat(pmd): bump PMD to 6.39.0 and add missing rules

### :beetle: Bug Fixes

- fix: Package valid command exit code when package flag is given [#586](https://github.com/Accenture/sfpowerkit/pull/586)
- fix: Profile user permission not being pulled down correctly during retrieve  [#577](https://github.com/Accenture/sfpowerkit/issues/577)

### :heart: Contributors

We'd like to thank all the contributors who worked on this release!

- [@genoud](https://github.com/genoud)
- [@rody](https://github.com/rody)

## [sfpowerscripts](https://github.com/Accenture/sfpowerscripts/)

- We have refactored Install Packages and Create Packages to make maintenance easier ( #731. #746  and #743). 
- There is a breaking change in the pool schema, Pools will succeed on deployment errors by default, as many of you have asked us to make the maintenance easier and this is the default approach followed on many projects (#755)

### :star: Enhancements
* Added headers to all commands with sfpowerscripts version and release (#735)


### :lady_beetle:  Bug Fixes
* assignPermSetsPostDeployment to be executed after postDeploymentScript (#729)
* Remove sfpowerscripts orchestrator constructs from unlocked package (#738)
* Fix profile redeployment for source package installations (#744)
* 'default' folder not getting deployed on aliasified packages (#753)
* Fix apex test metrics being reported incorrectly (#750)
* Fix Typo in pool list command (#714)
* Hold a deployment of package till permission set groups are updated (#732) 


**Full Changelog**: https://github.com/Accenture/sfpowerscripts/compare/@dxatscale/sfpowerscripts@8.5.3...@dxatscale/sfpowerscripts@9.3.6

## [docker-sfpowerscripts](https://github.com/dxatscale/docker-sfpowerscripts)

Docker Images updated for November Release

- sfpowerscripts - 9.3.6
- sfpowerkit - 3.3.4

**Full Changelog**: https://github.com/dxatscale/docker-sfpowerscripts/compare/October21.3...November21

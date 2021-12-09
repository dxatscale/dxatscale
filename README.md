# DX@Scale release log

Please note only major releases will be published. Hotfix release will be updated in individual repositories release notes.

# December 21

# [sfpowerscripts](https://github.com/Accenture/sfpowerscripts/)

December 21 (v10.2.0) features the following features and fixes

## 💣  Breaking Changes
- For wider compatibility across build systems, we have changed execution of scripts using shell as opposed to bash. Refer to the issue raised by @gretarvp [#745](https://github.com/Accenture/sfpowerscripts/issues/745). Any specific pre/post scripts using bash specific commands/features must be refactored.
- We have deprecated npmTag across all the stages. Please utilize LATEST_GIT_TAG or LATEST_TAG in release definition files [#687](https://github.com/Accenture/sfpowerscripts/issues/687)
- Package diff check no longer builds packages when there is a change in scratch org configuration. Users are recommended to update version numbers of the package that need to be rebuilt. [#780](https://github.com/Accenture/sfpowerscripts/issues/780)

## :star: New Features
- sfpowerscripts is now able to validate dependencies in 'validate' stage, surfacing dependency issues early. This is an 'alpha' feature and we are collecting feedback across projects. Please check additional options in the validate command to enable this feature. We will be iterating on this feature in subsequent releases [#764](https://github.com/Accenture/sfpowerscripts/issues/764)
- vlocity record based configuration is now supported as a data package [#633](https://github.com/Accenture/sfpowerscripts/issues/633). Read more about how to use vlocity here [data-packages](https://sfpowerscripts.dxatscale.io/v/release-december-21/faq/package-types/data-packages)


## :beetle: Bug Fixes
- Fix an issue with workitem metrics being reported incorrectly in a release [#777](https://github.com/Accenture/sfpowerscripts/pull/777)
- Dry Run in release command is installing package dependencies [#774](https://github.com/Accenture/sfpowerscripts/issues/774)
- Test Class parser doesn't detect classes with SOQL Queries UPDATE VIEWSTAT & UPDATE TRACKING [#724](https://github.com/Accenture/sfpowerscripts/issues/724)
- validateAgainstOrg no longer utilizes diffCheck, removing any needs of workaround [#754](https://github.com/Accenture/sfpowerscripts/issues/754)


**Full Changelog**: https://github.com/Accenture/sfpowerscripts/compare/@dxatscale/sfpowerscripts@9.3.6...@dxatscale/sfpowerscripts@10.2.0


# [sfpowerkit](https://github.com/Accenture/sfpowerkit/)

December21(v3.4.0) features the following fixes and enhancements

## ⭐ : Enhancements
* A new banner for every command in sfpowerkit that make its easy to report issues @henry88lay in https://github.com/Accenture/sfpowerkit/pull/598. To disable this header please  use `export SFPOWERKIT_NOHEADER=true`

## :beetle: Bug Fixes
* Fixed a regression Bad XML format for packaging permissions when downloading profiles in new versions [#596]

## Other Announcements
* Updated to use the latest apex-parser 2.11.0 fixing some issues with test class detection @aly76 in https://github.com/Accenture/sfpowerkit/pull/595
(https://github.com/Accenture/sfpowerkit/issues/596)  by @genoud in https://github.com/Accenture/sfpowerkit/pull/597

* Update npm-dependencies throughout by @azlam-abdulsalam in https://github.com/Accenture/sfpowerkit/pull/599


**Full Changelog**: https://github.com/Accenture/sfpowerkit/compare/v3.3.4...v3.4.2



# [docker-sfpowerscripts](https://github.com/dxatscale/docker-sfpowerscripts)

Docker Images updated for December Release

- sfdx-cli - 7.129.0
- sfpowerscripts - 10.2.0
- sfpowerkit - 3.4.2
- sfdmu - 4.10.3
- sfdx-browserforce-plugin - 2.7.1
- vlocity - 1.14.16

**Full Changelog**: https://github.com/dxatscale/docker-sfpowerscripts/compare/November21...December21





# November 21

# [sfpowerkit](https://github.com/Accenture/sfpowerkit/)

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

# [sfpowerscripts](https://github.com/Accenture/sfpowerscripts/)

- We have refactored Install Packages and Create Packages to make maintenance easier   [#731](https://github.com/Accenture/sfpowerscripts/pull/731) [#746](https://github.com/Accenture/sfpowerscripts/pull/746)  and [#743](https://github.com/Accenture/sfpowerscripts/pull/743). 
- There is a breaking change in the pool schema, Pools will succeed on deployment errors by default, as many of you have asked us to make the maintenance easier and this is the default approach followed on many projects [#755](https://github.com/Accenture/sfpowerscripts/pull/755)

### :star: Enhancements
* Added headers to all commands with sfpowerscripts version and release [#735](https://github.com/Accenture/sfpowerscripts/pull/735)


### :lady_beetle:  Bug Fixes
* assignPermSetsPostDeployment to be executed after postDeploymentScript [#729](https://github.com/Accenture/sfpowerscripts/issues/729)
* Remove sfpowerscripts orchestrator constructs from unlocked package [#738](https://github.com/Accenture/sfpowerscripts/pull/738)
* Fix profile redeployment for source package installations [#744](https://github.com/Accenture/sfpowerscripts/issues/744)
* 'default' folder not getting deployed on aliasified packages [#753](https://github.com/Accenture/sfpowerscripts/issues/753)
* Fix apex test metrics being reported incorrectly [#750](https://github.com/Accenture/sfpowerscripts/pull/750)
* Fix Typo in pool list command [#714](https://github.com/Accenture/sfpowerscripts/issues/714)
* Hold a deployment of package till permission set groups are updated [#732](https://github.com/Accenture/sfpowerscripts/issues/732)


**Full Changelog**: https://github.com/Accenture/sfpowerscripts/compare/@dxatscale/sfpowerscripts@8.5.3...@dxatscale/sfpowerscripts@9.3.6

# [docker-sfpowerscripts](https://github.com/dxatscale/docker-sfpowerscripts)

Docker Images updated for November Release

- sfpowerscripts - 9.3.6
- sfpowerkit - 3.3.4

**Full Changelog**: https://github.com/dxatscale/docker-sfpowerscripts/compare/October21.3...November21

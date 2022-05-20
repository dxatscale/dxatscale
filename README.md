# DX@Scale Release Log


Please note only major releases will be published. Hotfix releases will be updated in each individual repository's release notes.

# May 22

## [sfpowerscripts](https://github.com/Accenture/sfpowerscripts/)

sfpowerscripts(v13.6.16) features the following

⭐ New Features
- Introducing fast feedback mode, Now run your validation checks more faster by selectively deploying only the changed components of the package and triggering only the impacted test class. Read the decision record [here](https://github.com/Accenture/sfpowerscripts/blob/develop/decision%20records/validate/002-fast-feedback.md). You can turn on fast feedback by adding the --fastfeedback flag in the validate command. We believe this change along with upcoming changes in 'prepare' will ensure the validation experience remains performant.

![image](https://user-images.githubusercontent.com/59901319/169443653-48a51288-4811-477c-88e4-3373bcb93cbc.png)


- We would like to thank @nawforce for his amazing work on [apex-link](https://github.com/nawforce/apex-link) and [apex-parser](https://github.com/nawforce/apex-parser) which powers our apex related workflows.

⭐ Enhancements
- Minor enhancements to logging to be more descriptive especially with aliasified folders
- Refactoring to core libs for easier maintenance

🪲 Bug Fixes
- fix paths to pre and post deployment scripts when executed without repository - [Fix #954](https://github.com/Accenture/sfpowerscripts/pull/954) 
- support publishing artifacts greater than 5 MB - [Issue #967]( https://github.com/Accenture/sfpowerscripts/issues/967)
- sfdx sfpowerscripts:orchestrator:prepare shows errors in GitHub-Action - [Issue #955](https://github.com/Accenture/sfpowerscripts/issues/955)
- Fail to fetch requested information when query is too long - [Issue #860](https://github.com/Accenture/sfpowerscripts/issues/860)
- Display folder used while deploying to an org in aliasified mode
- Publish to tag packages that are successfully published even when other packages are failed
- Fix log times to display milliseconds, when source packages are being built. It usually displays as 00:00:00

:blue_book: [Full Change Log](https://github.com/Accenture/sfpowerscripts/compare/April22-2...@dxatscale/sfpowerscripts@13.6.16 ) 

## [sfpowerkit](https://github.com/Accenture/sfpowerkit/)

sfpowerkit (v4.2.8) features the following

### Notice
This version of sfpowerkit continues to use better-sqlite to do caching during profile reconciliation. Due to usage of this dependency, while installing sfpowerkit, you need to have node-gyp installed on your docker image/machine. Refer to issues [#645](https://github.com/Accenture/sfpowerkit/issues/645) and [#646](https://github.com/Accenture/sfpowerkit/issues/646). We are analyzing on how we can better address this. PR's are welcome

To install **node-gyp**, please follow the instructions [here](https://github.com/nodejs/node-gyp).

🪲 Bug Fixes
- Fix reconcile for child metadata (e.g. Custom Fields) - [Issue #662](https://github.com/Accenture/sfpowerkit/issues/662)
- Fix if some tags are not available
- Fix where files with special characters were not merged properly - [Issue #583](https://github.com/Accenture/sfpowerkit/issues/583)
- Fix where reconcile was removing a valid layout type - [Issue #669](https://github.com/Accenture/sfpowerkit/issues/669)

## [docker-sfpowerscripts](https://github.com/Accenture/sfpowerscripts/)

Docker Images are now published from sfpowerscripts repository. The recommended container registry going forward would be ghcr.io. You can read more about using the latest docker images [here](https://docs.dxatscale.io/v/release-may-22/projects/sfpowerscripts/docker-images).

- sfdx-cli - 7.145.0
- sfpowerscripts - 13.6.16
- sfpowerkit - 4.2.8
- pmd - 6.39.0
- sfdmu - 4.13.0
- vbt - 1.15.2
- sfdx-browserforce-plugin - 2.8.0

The images are available at the following [link](https://github.com/orgs/dxatscale/packages/container/package/sfpowerscripts). 


# April 22

## [sfpowerscripts](https://github.com/Accenture/sfpowerscripts/)

sfpowerscripts(v13+) features the following:

## 💣  Breaking Changes
- Changes to the SFDX CLI source tracking [#817](https://github.com/Accenture/sfpowerscripts/issues/817), Require **sfdx-cli 7.144.2** and above. We now support the latest [source tracking enhancements](https://github.com/forcedotcom/cli/issues/1258) released by the salesforce cli team.
- We are migrating sfpowerscripts to utilize underlying libraries open source by salesforce cli team, as opposed to wrapping around cli commands. We have completed the migration for most of the areas. You can read more about it [here](https://github.com/Accenture/sfpowerscripts/blob/develop/decision%20records/004-cli-to-libs.md). 

## ⭐  New Features
 -  During validate, sfpowerscripts will automatically retry test class that fail in asynchronous mode to be executed synchronously. You can read the decision record on how it works [here]( https://github.com/Accenture/sfpowerscripts/blob/develop/decision%20records/validate/001-automated-apex-testing-retry.md) 
 - Introducing 'testSynchronous' , a new property which will let sfpowerscripts know that whether to execute a particular package in synchronous mode. This allows validation to be run in different modes for different packages
 - The following diagram depicts the new features in sfpowerscripts for Apex Test Validation Process![ApexTestInPackage](https://user-images.githubusercontent.com/59901319/163011363-f081c2e2-ec6b-45ce-9662-2ab14add5290.png)
 - In addition, refer to the article on [Salesforce Apex Test Execution Performance Tuning](https://medium.com/@dieffrei/salesforce-apex-test-execution-performance-tuning-d38974a413ee) for a deeper dive into the topic.
 - Signed Docker Images served from ghcr.io. Read more on it [here](https://docs.dxatscale.io/v/release-april-22/projects/sfpowerscripts/docker-images)

## ⭐  Enhancements

- Add an option to Pool Configuration for Scratch Org creation time [#903](https://github.com/Accenture/sfpowerscripts/pull/903)
- Add an environment variable SPFOWERSCRIPTS_DEFAULT_SHELL to select shell [#873](https://github.com/Accenture/sfpowerscripts/pull/873)
- Clear code coverage and existing test result before test execution [#871](https://github.com/Accenture/sfpowerscripts/pull/871)
- Add support for diffcheck parameter in validateAgainstOrg command [#800](https://github.com/Accenture/sfpowerscripts/issues/800)
- Improved display of contents of a package [#553](https://github.com/Accenture/sfpowerscripts/issues/553)


## :beetle: Bug Fixes

- Display artifacts installed in the order of committed [#929](https://github.com/Accenture/sfpowerscripts/pull/929)
- Remove unsupported entities from sfdx-project.json  [#921](https://github.com/Accenture/sfpowerscripts/pull/921)
- Prepare command failing due timeout [#893](https://github.com/Accenture/sfpowerscripts/issues/893)
- Override API version for unlocked and source package installation [#885](https://github.com/Accenture/sfpowerscripts/pull/885)
- Error Plugin: `@dxatscale`/sfpowerscripts: Cannot find module 'node:process' [#874](https://github.com/Accenture/sfpowerscripts/issues/874)
- Orchestrator Deploy Error TypeError: Cannot read properties of null (reading 'match') [#872](https://github.com/Accenture/sfpowerscripts/issues/872)
- Fail to Install sfpowerscripts in a 'M1' ARM powered Mackbook [#864](https://github.com/Accenture/sfpowerscripts/issues/864)
- Fix for misleading error message for prepare cmd [#851](https://github.com/Accenture/sfpowerscripts/pull/851)
- orchestrator validate step getting different code coverage from the same ci pool [#836](https://github.com/Accenture/sfpowerscripts/issues/836)
- Add support for api version in source convert [#884](https://github.com/Accenture/sfpowerscripts/pull/884)

## [sfpowerkit](https://github.com/Accenture/sfpowerkit/)

sfpowerkit (v4.2+) features the following

## Notice

This version of sfpowerkit  continues to use better-sqlite to do caching during profile reconciliation. Due to usage of this dependency, while installing sfpowerkit, you need to have node-gyp installed on your docker image/machine.  Refer to issues #645 and #646. We are analyzing on  how we can better address this. PR's are welcome

To install node-gyp, please follow the instructions [here](https://github.com/nodejs/node-gyp).


## ⭐  Enhancements
*  Update in logger used to a simpler one, you will notice a change in the format and colors [#633](https://github.com/Accenture/sfpowerkit/pull/633)
* Ability to specify prefix for ScratchOrg's Aliases [#648](https://github.com/Accenture/sfpowerkit/pull/648)
* Remove Requirement for MetadataAPI access in [#642](https://github.com/Accenture/sfpowerkit/issues/642). Thanks @yippie for raising this issue
## :beetle: Bug Fixes
* Fix for sfpowerkit:source:profile:reconcile -s fails with error: Cannot read property 'getUsername' of undefined [#637](https://github.com/Accenture/sfpowerkit/issues/637).  @busybox0  @lram-11

** Full Changelog**: https://github.com/Accenture/sfpowerkit/compare/v4.1.5...v4.2.5


## [docker-sfpowerscripts](https://github.com/Accenture/sfpowerscripts/)

Docker Images are now published from sfpowerscripts repository. The recommended container registry going forward would be ghcr.io. You can read more about using the latest docker images [here](https://docs.dxatscale.io/v/release-april-22/projects/sfpowerscripts/docker-images).

- sfdx-cli - 7.145.0
- sfpowerscripts - 13.0.11
- sfpowerkit - 4.2.5
- pmd - 6.39.0
- sfdmu - 4.13.0
- vbt - 1.15.2
- sfdx-browserforce-plugin - 2.8.0

The images are available at the following address. https://github.com/orgs/dxatscale/packages/container/package/sfpowerscripts

## [dxatscale-template](https://github.dev/dxatscale/dxatscale-template)

DX@Scale templates (April-22) have the following updates

- Utilize [ghcr.io](https://github.com/features/packages) as the default registry
- Change on authentication approach used in github templates [#21](https://github.com/dxatscale/dxatscale-template/pull/21)


# February 22

## [sfpowerscripts](https://github.com/Accenture/sfpowerscripts/)

February 22 (v10.2.13) features the following fixes. We have also updated to the latest npm dependencies.

## :beetle: Bug Fixes
* fix: validation of artifact source repo by @aly76 in https://github.com/Accenture/sfpowerscripts/pull/812
* fix(create-unlocked-package): provide valid error message when package creation is timing out by @azlam-abdulsalam in https://github.com/Accenture/sfpowerscripts/pull/832
* fix(npm-scope): converts npm scope to lowercase during publish and fetch by @azlam-abdulsalam in https://github.com/Accenture/sfpowerscripts/pull/833



**Full Changelog**: https://github.com/Accenture/sfpowerscripts/compare/@dxatscale/sfpowerscripts@9.3.6...@dxatscale/sfpowerscripts@10.2.0


## [sfpowerkit](https://github.com/Accenture/sfpowerkit/)

February 22 for sfpowerkit(v4.1.3) features the following changes.

We have changed the way profile:reconcile works under the hood to make it more faster during bulk reconcile operation.  Please do let us know if there are any regressions, though we have taken all cares to test it. Refer to #629 #622.  We also have updated npm dependencies used by sfpowerkit in line with latest 'snyk|dependabot' reviews

## ⭐  Enhancements
* Enable Parallel Reconciling of Profiles by @azlam-abdulsalam in https://github.com/Accenture/sfpowerkit/pull/629

## :beetle: Bug Fixes
* Fix a typo on alias flag to fetch command in README.md file by @henry88lay in https://github.com/Accenture/sfpowerkit/pull/619
* Refactor/eslint fixes by @henry88lay in https://github.com/Accenture/sfpowerkit/pull/621
* Remove 'beta' from readme for sfpowerkit:source:apextest:list by @henry88lay in https://github.com/Accenture/sfpowerkit/pull/623
* Fixed path/link for profile retrieve and reconcile by @jjminer in https://github.com/Accenture/sfpowerkit/pull/627
* Refactor/style clean up by @henry88lay in https://github.com/Accenture/sfpowerkit/pull/628
* Remove salesforce alm dependency by @henry88lay in https://github.com/Accenture/sfpowerkit/pull/630


**Full Changelog**: https://github.com/Accenture/sfpowerkit/compare/v4.0.3...v4.1.3


## [sfp-cli](https://github.com/Accenture/sfpowerscripts/tree/develop/packages/sfp-cli)

We are releasing a beta version of the CLI for developers who utilizes DX@Scale in their projects. We hope this would simplify adoption of DX@Scale practices in your projects by combining git and sfdx into a single worflow


## [docker-sfpowerscripts](https://github.com/dxatscale/docker-sfpowerscripts)


Docker Images updated for February Release

- sfdx-cli - 7.136.2
- sfpowerscripts - 10.2.13
- sfpowerkit - 4.1.3
- sfdmu - 4.12.7
- sfdx-browserforce-plugin - 2.8.0
- vlocity - 1.14.19

**Full Changelog**: https://github.com/dxatscale/docker-sfpowerscripts/compare/December21...February22



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

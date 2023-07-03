# DX@Scale Release Log


Please note only major releases will be published. Hotfix releases will be updated in each individual repository's release notes.

# June 23

## dxatscale-template

All the templates have been updated to use the new sf plugin and also revised with breaking changes in sfpowerscripts, where sfpowerscripts is no longer a sfdx plugin and has to be used as direct cli command

## sfpowerscripts

sfpowerscripts v22.5.5  features the following 

## 💣 Breaking Change ##

### Transition from sfdx plugin to npm module:

sfpowerscripts has transitioned from a Salesforce DX plugin to an npm module. It should now be installed using the command` npm i -g @dxatscale/sfpowerscripts.` The commands can be used directly, e.g.` sfpowerscripts orchestrator:build ---`. For a shorter alias, use sfp instead of sfpowerscripts.

### sfpowerscripts is now independent of sfpowerkit

The new sfpowerscripts no longer relies on sfpowerkit for functionality. Any functionality that sfpowerscripts used to depend on sfpowerkit has been ported over.

### Deprecations

- This version discontinues the sfp-cli due to low usage. 
- The commands sfpowerscripts analyze:pmd and sfpowerscripts package:valid are no longer available. 
-  vbt cli is no longer available in the docker image


## Enhancements

**Support for Picklist Deployment**

sfpowerscripts now supports picklist deployment. This feature addresses Salesforce's limitation of not allowing picklist values to be deployed during unlocked package upgrades.  Read more about it here https://medium.com/@gnemiq/deploy-picklists-from-unlocked-packages-102c1366664f

**Support for Branches in package depdency** (https://github.com/dxatscale/sfpowerscripts/issues/1270 )

sfpowerscripts now supports branch attributes in dependencies, picking up the right dependencies of external packages from the right branches when being installed



**Introduction of a 'Diff' Package Type**

sfpowerscripts now offers a 'Diff' package type designed to facilitate organizations' transition from a monolithic structure to a modular DX@Scale model. A Diff package captures the differences in unpackaged metadata from the previous deployment, deploying only the delta. This approach allows unpackaged sections of the project to be deployed alongside packaged modules in a controlled manner . 

Please note, this feature is still in early development, Please reach out if you have queries on how to use it


## :beetle: Bug Fixes

* fix(apexlink): direct conversion to json breaks on large packages by @azlam-abdulsalam in https://github.com/dxatscale/sfpowerscripts/pull/1306
* fix(schema):  new attributes in sfdx-project.json will result in warning as opposed to errors https://github.com/dxatscale/sfpowerscripts/issues/1329
* fix(orginfo): add front door display url to logint to the sandbox (https://github.com/dxatscale/sfpowerscripts/commit/0562998b25f480e6d8d0050ea0902d31ff250906)
* fix(analyzer): display the analyzer being used in pre/post analyzers 
* fix(sfpowerscripts):  validate not reporting additional tags
Validate and validateAgainstOrg was not reporting metrics correctly,  as it was not hooked up with proper events. This  change request fixes the same and also passes in release config




## New Contributors
* @marcelosousa made their first contribution in https://github.com/dxatscale/sfpowerscripts/pull/1319

**Full Changelog**: https://github.com/dxatscale/sfpowerscripts/compare/@dxatscale/sfpowerscripts@21.1.0...@dxatscale/sfpowerscripts@22.5.5




# April 23

## sfpowerscripts

sfpowerscripts (v21.1.0) features the following changes

💣 Breaking Change
validate command will now respect aliasified packages. This means aliasified packages which do not have a default directory will fail during validation. To fix this, either ignore the package or add a default directory to the aliasified package which is the contents that you want to deploy to the scratch origin

Enhancements
feat(validate): validate will no longer display deployment options #1295
feat(metrics): new splunk metrics sender by @Rocko1204 in #1297
🪲 Bug Fixes
fix(links): add $schema properties #1203
fix(fht): rollbackOnError need to be true for production #1299
fix(validate): aliasified packages are ignored in validate by #1293
New Contributors
@Rocko1204 made their first contribution in #1297
Full Changelog: https://github.com/dxatscale/sfpowerscripts/compare/@dxatscale/sfpowerscripts@20.30.4...@dxatscale/sfpowerscripts@21.1.0

# March 23

## dxatscale-template

## :star: New Features (Beta)
- *feat(VS Code Tasks): Custom vscode tasks to **Fetch new Scratch Org** and **Pull your changes from the Scratch Org** are available to be tested.  Any feedbacks or contributions back to improving the tasks are welcomed from the community.  
- To start using, clone the latest main branch and go to **Command Palette** and enter `>Tasks: Run Task` and select one of the new tasks.
- Thanks to @eneag-sf for the contributions.

## sfpowerscripts

sfpowerscripts (v20.30.3) introduces the following  new features more towards bringing release configuration everywhere. Release configuration can now be applied in prepare, build and deploy providing more flexibility  especially when you have multiple independent teams 

## :star: New Features
- **feat(deploy): deploy to support release config**  https://github.com/dxatscale/sfpowerscripts/pull/1264

Deploy command now has an option to support release config, Thanks @alanjaouen  for providing a detailed analysis on why this is required

<img width="811" alt="image" src="https://user-images.githubusercontent.com/43767972/229249266-32b818dc-5fda-4257-bb5b-c5c5ddec8e0a.png">

-  **feat(build): add support for release config to build**  https://github.com/dxatscale/sfpowerscripts/pull/1272
-  **feat(deploy): enable source tracking support for deploy command** https://github.com/dxatscale/sfpowerscripts/pull/1273
-  **feat(publish): Add new flag to delete Git tags by age and limit minimum** https://github.com/dxatscale/sfpowerscripts/pull/1275

## :beetle: Bug Fixes
* fix(prepare): ensure prepare in build mode respects releaseconfig by @azlam-abdulsalam in https://github.com/dxatscale/sfpowerscripts/pull/1281
* fix(delete): Fix typo in message for when no Scratch Orgs are found by @JoeffreyChaucer in https://github.com/dxatscale/sfpowerscripts/pull/1283
* fix(fetch): SFDX Org List recognizes fetched scratch orgs as non-scratch orgs. Thanks @petter-eikeland  for following it up.

## New Contributors
* @JoeffreyChaucer made their first contribution in https://github.com/dxatscale/sfpowerscripts/pull/1275

**Full Changelog**: https://github.com/dxatscale/sfpowerscripts/compare/@dxatscale/sfpowerscripts@20.26.3...@dxatscale/sfpowerscripts@20.30.3

# February 23

## sfpowerscripts


February 23(v20.26.2) is all about quality of life improvements! We believe these enhancements will make your experience a bit more friendly.


## :star: New Features

- **feat(validate): display info about the org that is used for validation** [#1239](https://github.com/dxatscale/sfpowerscripts/pull/1239)

Displays information about the org that is used for validation.  Use `--orginfo`  flag to  display information to authenticate to the org that is  being currently used by the validate job. If you are using -x flag, the information is valid only during the life of the current running job

![image](https://user-images.githubusercontent.com/43767972/222339994-bf519c4c-30f8-4626-b46f-53cb39e3a5e9.png)


- **feat(validate): disable parallel testing using a flag** [#1255](https://github.com/dxatscale/sfpowerscripts/pull/1255)

Now you can disable parallel testing during validate across all packages using a new flag in `--disableparalleltesting`. Useful for scenarios when you are running full suite of tests across all the packages in a repo such as in nightly jobs and where do you need that additional consistency.   This is also quite useful when you are recfactoring into writing better tests

- **feat(validate): disable source package override in validate commands [#1240]**

Use `--disablesourcepkgoverride` in validate to build and install unlocked packages in your project as such, instead of using source packages (metadata api) while validating your packages. This will give you more accurate behaviour especially when used on a sandbox. (validateAgainstOrg). 

- **feat(pool): recover orphaned scratch orgs** [#1234](https://github.com/dxatscale/sfpowerscripts/pull/1234)

sfpowerscripts will not utilize the description field of ScratchOrgInfo object to identify scratch orgs that are created.  Using this information, the `pool: delete` command  when coupled with `--orphans` flag can help you delete scratch orgs that were created but never got associated to any pools. The output is also prettified by classifying the operation

![image](https://user-images.githubusercontent.com/43767972/222340600-48a0da37-4de4-43b7-b47d-866e88b6fd0c.png)

- **feat(prepare):  Add the ability to increment retry counts in prepare** [#1233]

You can attempt more retries for packages installation in prepare by adding a   ``maxRetryCount`` in your pool config. sfpowerscripts will now retry the package installation  the number of times specified by this option.  By default it always attempt for 2 installations during prepare

- feat(fetch) :  Display error messages when  fetching dev Scratch Org Pool in different git Repository for sfdx Project [#1251]
- feat(prepare):  prevent from downloading / creating artifacts that are not used while preparing without installAll  [#1223](https://github.com/dxatscale/sfpowerscripts/pull/1223)

## :beetle: Bug Fixes

- fix(validate):  fix for validate  failing  in individual mode due to missing dependencies #1241
- [fix(apextests): fix apex tests trigger crashing on unlocked packages](https://github.com/dxatscale/sfpowerscripts/commit/4fb3874de75b03cb75707aa7a1e0bb05f34d1b93)
- fix(fetch): sfpowerscripts:pool:fetch --json returns non-json [#1254](https://github.com/dxatscale/sfpowerscripts/issues/1254)
- fix(external-dependencies):  add support for detecting  package ids with 15 chars  and skipping it [#1244](https://github.com/dxatscale/sfpowerscripts/issues/1244)
- fix(logs): add/remove misplaced spaces and typo [(https://github.com/dxatscale/sfpowerscripts/actions/runs/4310619443/jobs/7519233163#step:4:37)](https://github.com/dxatscale/sfpowerscripts/pull/1236)
- fix(logs): add/remove misplaced spaces [#1231](https://github.com/dxatscale/sfpowerscripts/pull/1231)
- fix(logs): fix typo on promote message in release/deploy

## sfp-cli

We are reviving sfp-cli, as a unified cli for sfpowerscripts and other functionality to come.  The repository is migrated to the sfpowerscripts repository and is operated as a project in the same mono repository space. The current version is still incredibly early in development, and we will be pushing in changes faster to stabilize.

⚠️ Warning
sfp-cli is still unstable and is not recommended to be in use as a daily driver. Rest assured we are furiously working on it for making it prime time

## :heart: Contributors

We'd like to thank all the contributors who worked on this release!

- [@michallachowski](https://github.com/michallachowski)
- [@alanjaouen](https://github.com/alanjaouen)

# January 23

## [Craft-First](https://github.com/Craft-First)

Craft-first is a collection of open source production ready libraries and frameworks built on our experience in delivering large and complex Salesforce programs.

We are excited to release our first set of Open Source Frameworks that can be leveraged on your Salesforce Programs. Please feel free to use them on your new green field projects and/or retrofit it in your existing orgs.

## :new: Frameworks
- [Lightweight trigger framework](https://github.com/Craft-First/sfdc-trigger-framework) - Lightweight metadata driven trigger framework for Salesforce.
- [Trigger Bypass Strategy](https://github.com/Craft-First/sfdc-trigger-bypass-strategy) - This package implements a simple bypass strategy for the [sfdc-trigger-framework](https://github.com/Craft-First/sfdc-trigger-framework) based on a custom setting to define whether or not a specific trigger handler should be bypassed.
- [Feature Management Library for Salesforce](https://github.com/Craft-First/sfdc-feature-management) - This library provides a consistent way to check if a given feature is enabled in Salesforce.

## [sfpowerscripts](https://github.com/dxatscale/sfpowerscripts/)

First release of 2023 is out (v20.19.6) and is packed with goodies. Read  about the new features/enhancements and bug fixes. We hope it improves your dx@scale experience significantly.  

## :star: New Features

- sfpowerscripts now support for declarative field history tracking and feed tracking. Read more on how to use this feature [here](https://docs.dxatscale.io/sfpowerscripts/metadata-specific-support)  @MengAQi  has written a blog which details more on how this functionality work under the hoods. Check out the article [here](https://medium.com/@gnemiq/declarative-configuration-for-field-history-tracking-d63525a5e7b2)
-  Missed declaring a package dependency? sfpowerscripts now feature a transitive dependency resolution which fills in the gaps.  Don't like it, use ``disableTransitiveDependencyResolver:false`` to turn this feature off.  Read more about the feature here
      ```
      "plugins": {
              "sfpowerscripts": {
                  "disableTransitiveDependencyResolver": true
              }
      ```
-  3 New additional commands to help with dependency management, with more enhancements slated for upcoming releases. These commands are in the dependency topic 

| Commmand            | Description                                                                                                                                       |   
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| dependency: expand   | Expand the dependency list in sfdx-project.json file for each package, fix the gap of dependencies from its dependent packages                    |   
| dependency: shrink   | Shrink the dependency list in sfdx-project.json file for each package, remove duplicate dependencies that already exist in its dependent packages |   
| dependency: install | Install all the external dependencies of a given project                                                                                          |  


## :star: Enhancements

- Add support for sfpowerscripts orchestrator extensions to unlocked packages [#1204](https://github.com/dxatscale/sfpowerscripts/issues/1204)
- Additional parameters to pre/post script to manipulate contents of a package [#1196](https://github.com/dxatscale/sfpowerscripts/issues/1196)
- Publish command to push only packages version tags [#1183](https://github.com/dxatscale/sfpowerscripts/issues/1183)
- Create scratch orgs in parallel during prepare [#1142](https://github.com/dxatscale/sfpowerscripts/issues/1142)
- More concise logs, by removing borders around tables

## :beetle: Bug Fixes

- pool. Available metrics not reporting poolname [#1214](https://github.com/dxatscale/sfpowerscripts/issues/1214)
- Unpackaged metadata not provided to sfdx build in newest sfpowerscripts version [#1202](https://github.com/dxatscale/sfpowerscripts/issues/1202)
- GitLab NPM Scope adds second @ in orchestrator:release [#1200](https://github.com/dxatscale/sfpowerscripts/issues/1200)
- releasedefinition:generate does not generate "promotePackagesBeforeDeploymentToOrg" attributes correctly to Release Definition File [#1180](https://github.com/dxatscale/sfpowerscripts/issues/1180)
- Quickbuild command is not respecting .forceIgnore specific file [#1178](https://github.com/dxatscale/sfpowerscripts/issues/1178)
- Publish command tags HEAD instead of artifact commit ID [#983](https://github.com/dxatscale/sfpowerscripts/issues/983)


## New Contributors
* @gz77a made their first contribution in https://github.com/dxatscale/sfpowerscripts/pull/1181

**Full Changelog**: https://github.com/dxatscale/sfpowerscripts/compare/@dxatscale/sfpowerscripts@20.2.11...@dxatscale/sfpowerscripts@20.19.6

## [sfpowerkit](https://github.com/dxatscale/sfpowerkit)

sfpowerkit(v6.1.0) - January 23

## :boom: Deprecation Notice - March 2023
Added deprecation notice on commands as sfpowerkit is being discontinued in March 2023 completely. Please keep an eye on the repo for alternate suggestions and commands


# November 22

## [sfpowerscripts](https://github.com/dxatscale/sfpowerscripts/)

sfpowerscripts(v20.2.6) features the following

## 💣  Breaking Changes

-  **Additional new modes for validate command [#1133]** 

We heard you loud and clear, that you need flexibility with validate command depending on the type of repository and project configuration.  On some projects you would need to limit your validation boundary, only validate a changed package etc, we support it all. Read more [here](https://docs.dxatscale.io/v/release-november-22/sfpowerscripts/validate#validate-modes).

Unfortunately, that means we had to break up the command line parameters, a new flag called mode is added (defaults to thorough) to access other modes

-  **NPM Scope Names [#1168]** 

This release breaks the behaviour of how we handle scope names for NPM Package Registries. Please review and update your YAML configuration files in your pipelines if you encounter any issues authenticating to your package registry with the scope using the '@' and remove the '@' prefix as needed in your environment variables to ensure orchestrator commands execute successfully.  We are working to bring back functionality to handle this and make it uniform across platforms in the near future.

## :star: New Features

- **Create pools with a set of specified artifacts[#978]**

Utilize [release config](https://docs.dxatscale.io/v/release-november-22/sfpowerscripts/release/release-definition-generator#config-file) to limit the artifacts installed in scratch orgs and use the same in validate command. We would also like to thank @domrycz  for  contributing majority code for the feature and testing the early releases


- ****[Beta]** '~~validate' to identify~~ fix incorrect transitive dependencies [#855](https://github.com/dxatscale/sfpowerscripts/issues/855).** 

Add  enableTransitiveDependencyResolver:true, to the plugins section of sfdx-project.json will enable this feature. 

```
 "plugins": {
        "sfpowerscripts": {
            enableTransitiveDependencyResolver:true // enable transitive dependency resolution 
            "ignoreFiles": {
                "prepare": ".forceignore",
                "validate": ".forceignore",
                "quickbuild": "forceignores/.quickbuildignore",
                "build": "forceignores/.buildignore"
            }
        }
    }

```

- **Utilize packaging lib for all package related operations, this removes the dependency on sfdx-cli  [#1121](https://github.com/dxatscale/sfpowerscripts/issues/1121).**


## :star: Enhancements
- Prepare command creates too many Scratch Orgs when using snapshot pool [#1105](https://github.com/dxatscale/sfpowerscripts/issues/1105)  Thanks  @domrycz  for figuring out the missed scenario


## :beetle: Bug Fixes

- Issue when publishing "big" artifacts [#1149](https://github.com/dxatscale/sfpowerscripts/issues/1149). Thanks to @alanjaouen for raising the issue as well as PR to fix it
- Artifacts aren't pulled correctly releasedefinition:generate [#1140](https://github.com/dxatscale/sfpowerscripts/issues/1140) @Schuchie 
- Scratch Org Pool creation script failing "Unable to execute command .. Error: Can't find package id for dependency: 04txxxx" [#1113](https://github.com/dxatscale/sfpowerscripts/issues/1113)[eneag-sf] @eneag-sf
- Update core libs to fix 'org not found' issues during lengthy deployments

Full Change Log: https://github.com/dxatscale/sfpowerscripts/compare/@dxatscale/sfpowerscripts@19.7.3...@dxatscale/sfpowerscripts@20.2.6

## [sfpowerkit](https://github.com/dxatscale/sfpowerkit)

sfpowerkit(v6.0.1) features the following

## What's Changed
* [#744]-Getting text 'Config folder does not exists, Creating Folder' with --json param by @VertikaGoyal in https://github.com/dxatscale/sfpowerkit/pull/745


**Full Changelog**: https://github.com/dxatscale/sfpowerkit/compare/v6.0.0...v6.0.1



# September 22

## [sfpowerscripts](https://github.com/dxatscale/sfpowerscripts/)

sfpowerscripts(v19.7.3) features the following

## :star: New Features

-  **Support for multiple release definitions**
   
   Release command now supports multiple release definition as input. This allows a release manager to composite releases from different domains more easily and release them in a single transaction.


## :star: Enhancements

-  **Ability to skip all external package dependencies while generating a release definition** 

     When you are generating release definitions using multiple filters to composited later, external package dependencies might get repeated and it may also not be required for every files. Now release definition generator have an additional parameter 
 ```excludeAllPackageDependencies:<boolean>``` to skip package dependencies being added to  generated release defnitions.

-  **Utilize sfdx cli docker image as the base and minor docker improvements**
      
     We are switching to utilising sfdx-cli as the base docker image. This reduces the image size and provides better stability in fixating on the version of the cli

-  **Makes logs more concise and easy to read**
   
     Logs have been made much more concise to read and interpret in various commands. This will help in readability 

-  **Auto Log Grouping**

    Logs are now automatically grouped for Github Actions, Gitlab, Buildkite and Azure Pipelines even if the '-g (loggroup)' flag is not used

## :beetle: Bug Fixes

-  **Release fails if its unable to push a changelog**
-  **If 2 failing test methods have the same name, they get removed from test results (#1111)**  Thanks @Chiqqn and @domrycz  for raising the issue and fixing the same
-  **Incorrect Error Handling on Deployment Failure during validate (#1123)**  

**Full Changelog**: https://github.com/dxatscale/sfpowerscripts/compare/@dxatscale/sfpowerscripts@19.4.1...@dxatscale/sfpowerscripts@19.7.3

## [sfpowerkit](https://github.com/dxatscale/sfpowerkit)

sfpowerkit(v6.0.0) features the following

## :warning: Deprecation 
sfpowerkit:org:destruct is deprecated in this release and will no longer be supported as per deprecation notice here: https://github.com/dxatscale/sfpowerkit/issues/722 

## :beetle: Bug Fixes
* Remove typo from help command for sfdx sfpowerkit:source:profile:merge fixes in issue https://github.com/dxatscale/sfpowerkit/issues/693

## New Contributors
* @davidzheng1310 made their first contribution. Thanks David!! :dancer: :boom:

**Full Changelog**: https://github.com/dxatscale/sfpowerkit/compare/v5.0.0...v6.0.0

# August 22

## [sfpowerscripts](https://github.com/dxatscale/sfpowerscripts/)

## :star: New Features

-  **Generate Release Definition  Automatically**

Last release we announced a beta version of 'releasedefinition:generate'. While the idea was solid, the command lacked flexibility and it was put back to the drawing board. This release we have created a whole new of way interacting with the command. Read more about it in the descision record [here](https://github.com/dxatscale/sfpowerscripts/blob/b644a3c8de458b39f6e0a6174255b3b1d54da85f/decision%20records/release/006-release-defn-generator.md) .  Documentation is updated on how to use this command as well. Check out the link [here](https://docs.dxatscale.io/sfpowerscripts/release/release-definition-generator). Thanks to @Schuchie  for the feedback

- **Support for Distinct Scratch Org Definitions**

You might need to use this feature very rarely, but if the need arises, you have it. This feature allows a user to specify a unique scratch org config file for building a package. When the feature is enabled and the package name is matched, the build command will use specified config file for that package. Read more about it [here](https://docs.dxatscale.io/sfpowerscripts/build-and-quick-build#distinct-scratch-org-definition)

## :star: Enhancements

- **Enhanced Package Dependencies Installation**

sfpowerscripts no longer utilise the 'sfpowerkit:package:dependencies:install' to install dependencies. A new implementation is being utilised by validate/prepare/release commands. This command utilise the same dependency resolver used by package and removes lot of technical debt. 

- **Change in dependencies installation order**

validate will no longer install all the external dependencies upfront.  External dependencies will only be installed if the required package has to be validated and it will be installed just in time. This will make help with further increasing the speed of validate especially in thorough mode and change in package dependencies


- **Skip package installations if a higher version is already installed**

sfpowerscripts will now skip external dependencies such as managed package thats gets automatically upgraded in the target org.  Unfortunately this can only work after noticing a failed installation in the org and reading the error message. Read more about the discussion here (https://github.com/dxatscale/sfpowerkit/issues/602)

```
Installing Package Salesforce CPQ in buildbot@dxatscale.io.hotfix
A higher version of this package is already installed and can't be downgraded, skipping
```

- **Add support for multiple work item filters in changelog**

Release definition files now support  multiple work item filters, using the `workItemFilters', which expect an array of regex pattern filters. The changelog will pick up work items that match all the patterns


## :beetle: Bug Fixes

* We have fixed few internal defects as well

**Full Changelog**: https://github.com/dxatscale/sfpowerscripts/compare/@dxatscale/sfpowerscripts@18.1.5...@dxatscale/sfpowerscripts@19.4.1


## [sfpowerkit](https://github.com/dxatscale/sfpowerkit)

sfpowerkit (v5.0.0) features the following

## :beetle: Bug Fixes
* fix: Issue #713 where profile:reconcile was removing <userLicense> tag incorrectly by @genoud in https://github.com/dxatscale/sfpowerkit/pull/715
* fix: Issue #694 impacting tab visibilities on profile:reconcile command  by @genoud in https://github.com/dxatscale/sfpowerkit/pull/711
* fix: Issue #727 where permissions for VF pages were returning an error for the profile:merge command by @VertikaGoyal
* fix: Issue #729 where a scratch org alias is not returned to be used in script execution 

## :warning: Deprecation 
sfpowerkit:org:manifest:build is deprecated in this release and will no longer be supported as per deprecation notice here: https://github.com/dxatscale/sfpowerkit/issues/644 

## Contributors
* @VertikaGoyal made their first contribution in https://github.com/dxatscale/sfpowerkit/pull/727 :eyes: :eyes: :boom:
* @genoud as always, the profile master has saved the day :balloon: :tada:

**Full Changelog**: https://github.com/dxatscale/sfpowerkit/compare/v4.2.13...v4.2.14

# July 22

## [sfpowerscripts](https://github.com/dxatscale/sfpowerscripts/)

## :star: New Features
![image](https://user-images.githubusercontent.com/43767972/180698282-75b9a719-8585-4722-b6c2-853bc476eaea.png)

- Handle Entitlements with ease, sfpowerscripts now feature a smart entitlement filtering. To read more on how it works. Follow the link [here](https://medium.com/@gnemiq/salesforce-entitlement-handling-9e69735e3687) . Thanks @MengSQi for helping us with the implementation
- Support .NEXT for Source/Data Packages [#1065](https://github.com/dxatscale/sfpowerscripts/issues/1065).  .NEXT will be replaced by build number during the build of source/data packages. This would remove the validation errors when you have forgotten to set the last digit as '0'
- Hooks for "Prepare" command via scripts [#991](https://github.com/dxatscale/sfpowerscripts/issues/991). This allows to tweak the prepared scratch orgs further. Read more [here](https://docs.dxatscale.io/v/release-july-22/sfpowerscripts/orchestrator/prepare#executing-a-custom-script) 
- **[BETA Feature]** Now generate release definition based on a source org. Try this [command](https://docs.dxatscale.io/sfpowerscripts/command-glossary#sfdx-sfpowerscripts-releasedefinition-generate-n-less-than-string-greater-than-or-n-less-than-string) out and keep the feedbacks coming. 
![image](https://user-images.githubusercontent.com/43767972/180698890-6395a2aa-8ef5-4df4-9d1e-1ec5988de275.png)

## :beetle: Bug Fixes
- Fix for #1075  skipTesting is not respected when optimizedDeployment is false. Thanks to @sumanth-bolledla-acn  for the extensive tests on this one
- Fix for #942  scratch org creation now supports ObjectSettings
- Fix for #1085 Downgrade sfdx data plugin to 2.0.0 in docker image 
- Fix for #1086 to changelog: generate command 

## ⚠️  Local Installation Advice (if not using docker)
We have migrated the  underlying libraries to utilize **@salesforce/core v3 and @jsforce: 2.0.0**. Please uninstall existing plugin before installing the newer version.



**Full Changelog**: https://github.com/dxatscale/sfpowerscripts/compare/@dxatscale/sfpowerscripts@15.3.2...@dxatscale/sfpowerscripts@18.1.5


# June 22

## [sfpowerscripts](https://github.com/dxatscale/sfpowerscripts/)

sfpowerscripts(v15.3.2) features the following

## ⭐   New Feature

- sfpowerscripts is now able to use multiple stages for prepare. This will help you to circumvent timeouts on cloud hosted agents of most ci/cd platforms. Read on more about the feature [here](https://docs.dxatscale.io/v/release-june-22/sfpowerscripts/orchestrator/prepare#using-prepare-in-multiple-stages).  <br><br>Also check the [decision record](https://github.com/dxatscale/sfpowerscripts/blob/main/decision%20records/prepare/002-prepare-daisy-chaining.md) to understand the reasoning.<br><br>
![image](https://user-images.githubusercontent.com/43767972/174704029-08f82cfb-40b6-4513-8e93-1bcc412c20d6.png)


## ⭐   Enhancements

- Return unused/rolled back scratch orgs to the pool [#989](https://github.com/dxatscale/sfpowerscripts/issues/989). For this enhancement to work, please ensure `sfpower-scratchorg-pool` package is updated. Read on the instruction on how to update [here](https://github.com/dxatscale/sfpower-scratchorg-pool#upgrading-from-110-1-to-200-1)
- Add info about optimised deployment during deployment https://github.com/dxatscale/sfpowerscripts/pull/994
- Add support for unpackaged metadata in unlocked packages [#958](https://github.com/dxatscale/sfpowerscripts/issues/958)
- Ignore packages without a package name attribute [#842](https://github.com/dxatscale/sfpowerscripts/issues/842)
- Log resolved package dependencies during build https://github.com/dxatscale/sfpowerscripts/pull/1058
- Additional metrics for individual scratch orgs in pool. Check [metrics docs](https://docs.dxatscale.io/v/release-june-22/sfpowerscripts/metrics-and-dashboards) for details


## :beetle: Bug Fixes
- No clear error when package name exceeds 38 characters [#998](https://github.com/dxatscale/sfpowerscripts/issues/998)
- Provide more descriptive error message when it is unable to compute diff during build [#965](https://github.com/dxatscale/sfpowerscripts/issues/965)
- Warning message is not displayed when tests are skipped explicitly  [#919](https://github.com/dxatscale/sfpowerscripts/issues/919)
- Incorrect Dependencies might be used during build stage [#496](https://github.com/dxatscale/sfpowerscripts/issues/496)
- No Metrics while using fast feedback

## :heavy_exclamation_mark: Deprecation Warning
- Docker Images are now published and maintained in sfpowerscripts repository. Ensure that you update your ci/cd templates to reference the [github registry container](https://github.com/dxatscale/sfpowerscripts/pkgs/container/sfpowerscripts) going forward.  Future releases will no longer support [docker hub container](https://hub.docker.com/r/dxatscale/sfpowerscripts) updates and potentially remove it completely.


**Full Changelog**: https://github.com/dxatscale/sfpowerscripts/compare/@dxatscale/sfpowerscripts@13.6.22...@dxatscale/sfpowerscripts@15.3.2


## [sfp-cli](https://github.com/dxatscale/sfp-cli/)

sfp-cli(v3.1.0) updated with several bug fixes and added a shortcut to force push changes to the org


# May 22

## [sfpowerscripts](https://github.com/dxatscale/sfpowerscripts/)

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

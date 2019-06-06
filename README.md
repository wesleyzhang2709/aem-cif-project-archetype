[![CircleCI](https://circleci.com/gh/adobe/aem-cif-project-archetype.svg?style=svg)](https://circleci.com/gh/adobe/aem-cif-project-archetype)

# CIF Project Archetype
This archetype creates a minimal Adobe Experience Manager CIF project as a starting point for your own projects. The properties that must be provided when using this archetype allow to name as desired all parts of this project.

This project is based on [aem-project-archetype](https://github.com/adobe/aem-project-archetype).


---
⚠️ **IMPORTANT** ⚠️

This project was not released yet. Also the [CIF core components](https://github.com/adobe/aem-core-cif-components) project which this project depends on was not released yet. 

For being able to build the archetype, make sure you checkout and build the CIF core components project locally first.

Please follow the steps described in the [Building](#building) section to create a project from this archetype.

---


## Provided Maven profiles
The generated maven project support different deployment profiles when running the Maven install goal `mvn install` within the reactor.

Id                        | Description
--------------------------|------------------------------
autoInstallBundle         | Install core bundle with the maven-sling-plugin to the felix console
autoInstallPackage        | Install the ui.content and ui.apps content package with the content-package-maven-plugin to the package manager to default author instance on localhost, port 4502. Hostname and port can be changed with the aem.host and aem.port user defined properties. 
autoInstallPackagePublish | Install the ui.content and ui.apps content package with the content-package-maven-plugin to the package manager to default publish instance on localhost, port 4503. Hostname and port can be changed with the aem.host and aem.port user defined properties.

## Usage
To use a released version of this archetype use the following Maven command:
```bash
mvn archetype:generate \
    -DarchetypeGroupId=com.adobe.commerce.cif \
    -DarchetypeArtifactId=cif-project-archetype \
    -DarchetypeVersion=1-SNAPSHOT
```

Where `1-SNAPSHOT` is the archetype version number that you want to use (see archetype versions below).

### Available properties

Name                      | Default | Description
--------------------------|---------|--------------------
groupId                   |         | Base Maven groupId
artifactId                |         | Base Maven ArtifactId
version                   |         | Version
package                   |         | Java Source Package
appsFolderName            |         | /apps folder name
artifactName              |         | Maven Project Name
componentGroupName        |         | AEM component group name
contentFolderName         |         | /content folder name
confFolderName            |         | /conf folder name
packageGroup              |         | Content Package Group name
siteName                  |         | AEM site name
optionAemVersion          |  6.5.0  | Target AEM version
optionIncludeExamples     |    y    | Include Component Library examples

Note: If the archetype is executed in interactive mode the first time properties with default  values can't be changed (see 
[ARCHETYPE-308](https://issues.apache.org/jira/browse/ARCHETYPE-308) for more details). The value can be  changed when the property 
confirmation at the end is denied and the questionnaire gets repeated or by passing the parameter in the command line (e.g. 
`-DoptionIncludeExamples=n`).

### Requirements
The latest version of the archetype has the following requirements

* Adobe Experience Manager 6.4 SP4 or higher
* Apache Maven (3.3.9 or newer)
* Adobe Public Maven Repository in maven settings, see [Knowledge Base](https://helpx.adobe.com/experience-manager/kb/SetUpTheAdobeMavenRepository.html) article for details.

For a list of supported AEM versions of previous archetype versions, see [historical supported AEM versions](VERSIONS.md).

## Building
To compile and use an edge, local version of this archetype:
```bash
mvn clean install
```

Then change to the directory in which you want to create the project and run:
```bash
mvn archetype:generate \
    -DarchetypeGroupId=com.adobe.commerce.cif \
    -DarchetypeArtifactId=cif-project-archetype \
    -DarchetypeVersion=1-SNAPSHOT
```
     
Side note: The profile "adobe-public" must be activated when using profiles like "autoInstallPackage" mentioned above.

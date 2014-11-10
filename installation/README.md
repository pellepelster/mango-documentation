# Installation

## Prerequisites

This chapter will give you an overview of the steps needed to get started with the Mango framework.
Mango tries to minimize it's prerequisites to ease and speed up the inital setup, so the only thing you have to do to get started is to prepare yourEclipse IDE and install the Mango IDE support for Eclipse.
To set up Eclipse you have two options, you can either install everything needed by hand or just download a prebuilt Eclipse distribution containing everything needed, including Mango.

### Prebuilt Eclipse distribution
If you want to start with a prebuilt Eclipse just download the right one for your environment, unzip it, and you are ready to go!

| 64 bit | 32 bit |
| -- | -- |
| [Linux 64 bit](http://zoidberg.pelle.io/jenkins/job/mango-ci-eclipse-distributions/lastSuccessfulBuild/artifact/mango-eclipse-linux-gtk-x86_64.tar.gz) | [Linux 32 bit](http://zoidberg.pelle.io/jenkins/job/mango-ci-eclipse-distributions/lastSuccessfulBuild/artifact/mango-eclipse-linux-gtk-x86.tar.gz) |
| [OS X 64 bit](http://zoidberg.pelle.io/jenkins/job/mango-ci-eclipse-distributions/lastSuccessfulBuild/artifact/mango-eclipse-macosx-cocoa-x86_64.tar.gz) | [OS X 32 bit](http://zoidberg.pelle.io/jenkins/job/mango-ci-eclipse-distributions/lastSuccessfulBuild/artifact/mango-eclipse-macosx-cocoa-x86.tar.gz) |
| [Windows 64 bit](http://zoidberg.pelle.io/jenkins/job/mango-ci-eclipse-distributions/lastSuccessfulBuild/artifact/mango-eclipse-win32-x86_64.zip) | [Windows 32 bit](http://zoidberg.pelle.io/jenkins/job/mango-ci-eclipse-distributions/lastSuccessfulBuild/artifact/mango-eclipse-win32-x86.zip)


### Manual Installation

If you go for manual installation, just add the update sites for the needed prerequisites to your Eclipse IDEand install the required software.

#### Xtext

Because Mango’s DSL is based on Xtext, you obviously need to have Xtext installed in your Eclipse IDE, see [here](http://www.eclipse.org/Xtext/download.html) for detailed instructions or simply use Xtext’s release update site: http://download.eclipse.org/modeling/tmf/xtext/updates/composite/releases/

#### Eclipse Gradle Integration (optional)

Because Mango’s building is Gradle based, it’s a good idea to install Spring’s Gradle integration from its update site http://dist.springsource.com/release/TOOLS/gradle. This step is optional, you can of course just use Gradle from the command line.

#### Mango IDE support

Of course you will need Mango itself. Currently there is only a CI update site available at http://zoidberg.pelle.io/~mango-ci/updatesite/.

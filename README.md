#Tizen
##1) Introduction

Tizen is an open and flexible operating system built from the ground up to address the needs of all stakeholders of the mobile and connected device ecosystem, including device manufacturers, mobile operators, application developers and independent software vendors (ISVs). Tizen is developed by a community of developers, under open source governance, and is open to all members who wish to participate.

The Tizen operating system comes in multiple profiles to serve different industry requirements. The current Tizen profiles are Tizen IVI (in-vehicle infotainment), Tizen Mobile, Tizen TV, and Tizen Wearable. In addition to that, as of Tizen 3.0, all profiles are built on top of a common, shared infrastructure called Tizen Common.

With Tizen, a device manufacturer can begin with one of these profiles and modify it to serve their own needs, or use the Tizen Common base to develop a new profile to meet the memory, processing and power requirements of any device and quickly bring it to market.

Mobile operators can work with device partners to customize the operating system and user experience to meet the needs of specific customer segments or demographics.

For application developers and ISVs, Tizen offers the power of native application development with the flexibility of unparalleled HTML5 support. Tizen also offers the potential for application developers to extend their reach to new “smart devices” running Tizen, including wearables, consumer electronics (TVs, gaming consoles, DVRs, etc.), cars and appliances. 

The Tizen project resides within the Linux Foundation and is governed by a Technical Steering Group. The Technical Steering Group is the primary decision-making body for the open source project, with a focus on platform development and delivery, along with the formation of working groups to support device verticals.

The Tizen Association has been formed to guide the industry role of Tizen, including gathering of requirements, identification and facilitation of service models, and overall industry marketing and education.

To learn more about Tizen please visit website https://www.tizen.org/


##2) Gerrit to Github Mirroring

The objective of this task is to make sure latest buildable Tizen repositories are available in Github for developers. So developers can fork any repo and  experiment or contribute to Tizen development. Latest buildable code can be downloaded by repo tool using manifest files in the "manifest" repo.

Tizen has multiple profiles mobile, wearable, tv , common and ivi. Presently Tizen mobile profile reposotories are mirrored from gerrit to github.

Currently mirroring of repos happens in following cases

1) A jenkin job mirrors Tizen mobile repositories to github once in a day regularly. Please refer mobile.xml for complete list of repos
2) When a SR is accepted , OBS makes a build and snapshot is created.. The repos in manifest xml of snapshot are synced to Github and the manifest file is added to this repo

A github repo is created first time for a gerrit repo when mirroring happens. For subsequent requests only delta changes are synced to github repo.

##3) How to Clone Tizen Source
This section describes how to clone Tizen source over HTTPS, including the following:
  - Cloning specific project over HTTPS
  - Cloning all projects over HTTPS

###3.1) Cloning specific project over HTTPS
To clone specific project over HTTPS, perform the following procedure:

Confirm the package name by searching it on Tizen Project List (https://github.com/tizenorg) or by opening the following URL in browser

https://api.github.com/orgs/tizenorg/repos

Clone the required package by executing the following command:

$ git clone \[-b \<Branch\>\] https://github.com/tizenorg/\[\<Github_Project\>\]  \[\<Local_Directory\>\]

An example is shown below:

$ git clone -b tizen_2.0 https://github.com/tizenorg/tools.image-configurations 
###3.2) Cloning all projects over HTTPS
This section describes how to clone source of all projects over HTTPS, including the following:

  - Cloning the latest source of all projects over HTTPS
  - Cloning the daily/weekly release source of all projects over HTTPS
  
To prepare for cloning, perform the following procedure:

1. Create ~/bin/ subdirectory, include it in PATH, and then switch to it by executing the following commands:

        $ mkdir ~/bin/
        $ PATH=~/bin:$PATH

2. Download the repo script by executing the following command:

        $ curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo

3. Change the attribute of repo to make it executable by executing the command:

        $ sudo chmod a+x ~/bin/repo

4. Create a new directory for Tizen and then switch to it by executing the following commands:

        $ mkdir ~/<Tizen_Project>
        $ cd ~/<Tizen_Project>


####3.2.1) Cloning the Latest Source of All Projects over HTTPS

To clone the latest source of all projects over HTTPS, perform the following procedure:

  1. Initialize the repository by executing one of the following commands, as appropriate:
  
    <b>Tizen 3.0</b>
    - Common
          - $ repo init -u https://github.com/tizenorg/manifest -b master -m common.xml
    - IVI
          - $ repo init -u https://github.com/tizenorg/manifest -b master -m ivi.xml
    - Mobile
          - $ repo init -u https://github.com/tizenorg/manifest -b master -m mobile.xml
    - Wearable
          - $ repo init -u https://github.com/tizenorg/manifest -b master -m wearable.xml
    
  2. Synchronize the repository by executing the following command:
          
           $ repo sync


####3.2.2) Cloning the daily/weekly release source of all projects over HTTPS  
Tizen mobile is taken as example in this section.

To clone the release source of all projects over SSH, perform the following procedure:

1. Initialize the original repository by executing the following command:

    $ repo init -u https://github.com/tizenorg/manifest/ -b master -m releases/daily/tizen/mobile/tizen-mobile_20160416.1_arm-wayland.xml

  Upon successful initialization, the ~/<Tizen_Project>/.repo/manifests/ directory is available and ready for use.

2. Synchronize the repository by executing the following command:

    $ repo sync

##4) Pull Request and merging the code to Gerrit
--------------------------------------------
TBD

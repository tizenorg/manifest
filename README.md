Gerrit to Github Mirroring
---------------------------
The objective of this task is to make sure latest buildable Tizen repositories are available in Github for developers. So developers can fork any repo and  experiment or contribute to Tizen development. Latest buildable code can be downloaded by repo tool using manifest files in the "manifest" repo.

Tizen has multiple profiles mobile, wearable, tv , common and ivi. Presently Tizen mobile profile reposotories are mirrored from gerrit to github.

Currently mirroring of repos happens in following cases

1) A jenkin job mirrors Tizen mobile repositories to github once in a day regularly. Please refer mobile.xml for complete list of repos
2) When a SR is accepted , OBS makes a build and snapshot is created.. The repos in manifest xml of snapshot are synced to Github and the manifest file is added to this repo

A github repo is created first time for a gerrit repo when mirroring happens. For subsequent requests only delta changes are synced to github repo.

Downloading repos using manifest
----------------------------------
Install repo tool. Refer http://source.android.com/source/downloading.html#installing-repo for download instructions.

To download Tizen mobile repositories
repo init -u  https://github.com/tizenorg/manifest/ -m mobile.xml

To download Tizen mobile snapshot repositories
repo init -u https://github.com/tizenorg/manifest/ -m tizen-mobile_20160402.2_arm64-wayland.xml 

Adding a new repo to Mobile profile
-------------------------------------------
When a new repo is added in Gerrit for Tizen mobile profile then same repo should be added in mobile.xml. Otherwise the new repo is not synched to Github.

Pull Request and merging the code to Gerrit
--------------------------------------------
TBD

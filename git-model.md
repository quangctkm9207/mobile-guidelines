# Git Branching Model
It is based on [Vincent Driessen's Model](http://nvie.com/posts/a-successful-git-branching-model/).  

### How to start a new version
* Checkout `develop` branch: `$ git checkout develop`.
* Change configuration to `debug` mode if needed. (i.e: app name, id, host url, etc).
* Create new `feature-x` or `fix-bug-x` branch from 'develop': i.e: `$ git checkout -b feature-x develop`.
* When complete that new feature or bug fix, merge its branch back to `develop` branch and delete it. i.e:
    * `$ git merge --no-ff feature-x`.
    * `$ git branch -d feature-x`.

### How to release a new version  
When all next version's features are completed and codes are ready for new release.  

* Make sure all of feature branches are merged into `develop` branch.
* Create new `release-x` branch. i.e: `$ git checkout -b release-1.1.0 develop`.
* Change configuration to `release` mode if needed. (i.e: app name, id, host url, etc).
* Increase **version** name and **build** number (in General Project Setting for iOS, in app's build.gradle for Android).
* Update 'CHANGELOG.md'.
* Create new commit: `$ git commit -a -m "Prepare version 1.1.0"`
* Merge `release-x` branch to `master` branch and tag new release. i.e:  
    * `$ git checkout master`
    * `$ git merge --no-ff release-1.1.0`
    * Solve conflicts(if any) and commit.
    * `$ git tag -a v1.1.0`
    * `$ git push`
    * `$ git push --tags`
* Build and publish on store:
    * iOS: Build, archive, validate and upload new archive to App Store.  
    * Android: Build, generate signed APK and upload to Google Play.
* Merge `release-x` branch to `develop`.  
    * `$ git checkout develop`.
    * `$ git merge --no-ff release-1.1`.
    * Solve conflicts(if any) and commit.
    * `$ git push`
    * `$ git push --tags`
 * Delete `release-x` branch.
    * `$ git branch -d release-1.1`.

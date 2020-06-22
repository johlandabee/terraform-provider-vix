### Thanks for your interest in contributing to this project and for taking the time to read this guide.

## Code of conduct
*Taken from http://libvirt.org/governance.html with minor adjustments.*

The open source community covers people from a wide variety of countries, backgrounds and positions. This global diversity is a great strength for this project, but can also lead to communication issues, which may in turn cause unhappiness. To maximize happiness of the project community taken as a whole, all members (whether users, contributors or committers) are expected to abide by the project's code of conduct. At a high level the code can be summarized as "be excellent to each other". Expanding on this:

**Be respectful:** disagreements between people are to be expected and are usually the sign of healthy debate and engagement. Disagreements can lead to frustration and even anger for some members. Turning to personal insults, intimidation or threatening behavior does not improve the situation. Participants should thus take care to ensure all communications / interactions stay professional at all times.

**Be considerate:** remember that the community has members with a diverse background many of whom have English as a second language. What might appear impolite, may simply be a result of a lack of knowledge of the English language. Bear in mind that actions will have an impact on other community members and the project as a whole, so take potential consequences into account before pursuing a course of action.

**Be forgiving:** humans are fallible and as such prone to make mistakes and inexplicably change their positions at times. Don't assume that other members are acting with malicious intent. Be prepared to forgive people who make mistakes and assist each other in learning from them. Playing a blame game doesn't help anyone.

## Issues
* Before reporting an issue make sure you search first if anybody has already reported a similar issue and whether or not it has been fixed.
* Make sure your issue report sufficiently details the problem.
* Include code samples reproducing the issue.
* Please do not derail or troll issues. Keep the discussion on topic and respect the Code of conduct.
* Please do not open issues for personal support requests, use the [mailing list](https://groups.google.com/group/govix) instead.
* If you want to tackle any open issue, make sure you let people know you are working on it.

## Development workflow
Go is unlike any other language in that it forces a specific development workflow and project structure. Trying to fight it is useless, frustrating and time consuming. So, you better be prepare to adapt your workflow when contributing to Go projects.

### Prerequisites
* **Go**: To install Go please follow its installation guide at https://golang.org/doc/install
* **Git:**
   * **Debian-based distros:** `apt-get install git-core`
   * **OSX:** `brew install git`
* **VMware Fusion, Workstation, Player or Server:** https://my.vmware.com/web/vmware/downloads
* **VMware VIX SDK:** https://www.vmware.com/support/developer/vix-api/. For OSX, it comes bundled with VMware Fusion already.

### Pull Requests
* Please be generous describing your changes.
* Although it is highly suggested to include tests, they are not a hard requirement in order to get your contributions accepted.
* Keep pull requets small so core developers can review them quickly.
* Unlike other projects, we are not going to nitpick your contributions. If your pull request is correct, we are going to merge and address the small details by ourselves. There is no point on delaying contributions due to little and unimportant details.

### Workflow for third-party code contributions
* In Github, fork `https://github.com/hooklift/govix` to your own account
* Get the package using "go get": `go get github.com/hooklift/govix`
* Move to where the package was cloned: `cd $GOPATH/src/github.com/hooklift/govix`
* Add a git remote pointing to your own fork: `git remote add downstream git@github.com:<your_account>/govix.git`
* Create a branch for making your changes, then commit them.
* Push changes to downstream repository, this is your own fork: `git push <mybranch> downstream`
* In Github, from your fork, create the Pull Request and send it upstream.
* You are done.


### Workflow for core developers
Since core developers usually have access to the upstream repository, there is no need for having a workflow like the one for thid-party contributors.

* Get the package using "go get": `go get github.com/hooklift/govix`
* Create a branch for making your changes, then commit them.
* Push changes to the repository: `git push origin <mybranch>`
* In Github, create the Pull Request from your branch to master.
* Before merging into master, wait for at least two developers to code review your contribution.


### To keep in mind when running tests or applications
So far, we haven't been able to figure out how to statically compile libvix inside govix binaries. So, you will have to work around, hinting the linker by setting the environment variable `LD_LIBRARYPATH` in Linux,  `DYLD_LIBRARY_PATH` in OSX or `PATH` in Windows.

## Debugging
### Enabling debug logs
#### OSX
`echo "vix.debugLevel = \"9\"" >> ~/Library/Preferences/VMware\ Fusion/config`


### Logs
* **OSX:** `~/Library/Logs/VMware/*.log`
* **Linux:** `/tmp/vmware-<username>/vix-<pid>.log`
* **Windows:** `%TEMP%\vmware-<username>\vix-<pid>.log`

### Multithreading

The Vix library is intended for use by multi-threaded clients. Vix shared
objects are managed by the Vix library to avoid conflicts between threads.
Clients need only be responsible for protecting user-defined shared data.

## Resources

* **Configuration Maximums:** http://www.vmware.com/pdf/vsphere5/r50/vsphere-50-configuration-maximums.pdf
* **VMX Parameters:** http://faq.sanbarrow.com/index.php?sid=1504158&lang=en&action=show&cat=2
* **VMware VIX Forum:** https://developercenter.vmware.com/forums?id=2417
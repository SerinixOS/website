---
title: Using the Unstable Collection
description: |
  Guide on enabling and disabling carbonOS's unstable software collection, and
  important details to keep in mind
os_version: "2022.3"
---

The unstable software collection (aka repository) contains the latest changes and
features that will be coming in the next stable version of carbonOS. However, as
the name suggests, this collection comes with no stability guarantees. Proceed at
your own risk. If you're interested in the latest and greatest upcoming features,
you can test them here and your feedback will help find and fix bugs before they
can make their way into a stable release.

To prevent accidental activation of this unstable collection, carbonOS does not
include the necessary configuration to just enable it with `updatectl`. Some
setup is required first. Follow these steps:

1. Make sure your system is up-to-date
2. **Disable secure boot!** The releases in the unstable repository are not
   signed with the necessary keys to ensure the function of secure boot, so
   your system *will not boot an unstable version* unless secure boot is disabled
3. Open the terminal and enter a root shell by running `pkexec` and typing
   in your credentials at the prompt
4. Run `curl https://repo.carbon.sh/remote-unstable.conf > /etc/ostree/remotes.d/carbon-unstable.conf`.
   This downloads and installs a configuration file that adds the unstable repository
   to the system's list of collections
5. Run `curl https://repo.carbon.sh/gpg/unstable.gpg | ostree remote gpg-import carbon-unstable --stdin`.
   This downloads and trusts the GPG key that is used to verify the integrity of
   the releases in the unstable collection
6. Run `exit` to leave the root shell
7. Run `updatectl switch --collection sh.carbon.Unstable` to download and deploy
   the latest unstable version
8. Reboot your system. You should now be configured to use the unstable collection!

The unstable collection uses a "rolling" release model, with updates being
published approximately daily. I highly recommend making sure that you keep
the system no more than a few days out of date

#### Switching back

If you'd like to revert back to the stable carbonOS repository, please note
that you will be *downgrading* software versions, which always runs the risk
of file format incompatibilities (i.e. a newer version of a program generated
a new file format that an older version of the same program cannot handle). I
suggest switching back to the stable repository only once the version you've
been testing is released to the stable branch.

To switch back to the stable repository, just run 
`updatectl switch --collection sh.carbon.Stable` and reboot.

#### Installing beta apps

If you're interested in testing unstable releases of carbonOS, you may also
want to test unstable releases of your apps. To enable beta versions in the
Software app, open a terminal and run this command:
`flatpak remote-add flathub-beta https://flathub.org/beta-repo/flathub-beta.flatpakrepo`.
You should now be able to select the `flathub-beta` source in the Software app
to install beta versions of your software.


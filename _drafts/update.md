---
title: "Major Rework in Progress!"
author: Adrian Vovk
---

I haven't posted any updates about carbonOS recently, but the project is still alive and well!
This post details the ongoing redesign of carbonOS, including work I've completed over the
last couple of months, upstream contributions, and the work still left to do.

# Part 1: The Technology

Technical innovation was always one of carbonOS's driving principles. As an independent distribution,
we are free to diverge from the norm and implement unique solutions that other distros will have difficulty
replicating.

Much of my work over the last few months has been a complete overhaul of carbonOS's underlying tech

### Status Quo

TODO
- Discuss carbonOS ostree base, + limitations
- Discuss ChromeOS
- Define immutable, atomic
- Compare other distros to carbonOS's new approach to immutability/atomicity

### UKIs, DDIs, and TPMs

TODO
- ELI5 UKIS, and DDIs
- Discuss how ostree was dropped, and carbonOS switched to these concepts
- ELI5 TPM
- Discuss how carbonOS is now using the TPM to encrypt your data
- Discuss how carbonOS is the first general-purpose distro to fully adhere to uapi-group specs. Mention GNOME OS as the exception, but it's not intended to be general purpose
- Link to uapi-group specs and mention (REDACTED)

### System Updates

TODO
- Discuss how systemd-sysupdate works
- Discuss work that has been completed for systemd-sysupdated
- Discuss work that still needs to be done to integrate gnome-software w/ sysupdated
- Link to systemd-sysupdated PR

### Installer

TODO
- Discuss how we don't have an installer yet
- Discuss my ideas w.r.t `systemd-installer-generator`
- Mention that it all still needs some work to be finished
- Link to my systemd-installer-generator PR

### Homed

TODO
- ELI5 what homed is and why we want it
- Describe the work that I will be doing
- (REDACTED)

### Preinstalled Flatpaks

TODO
- Explain why we want these
- Explain how this will let me slim down carbonOS
- Explain the challenges
    - How do we ship the preinstalled Flatpaks such that they're not a huge waste of space?
    - Finding a way to share the generic Flatpak runtimes
    - Finding a way to separate out the hardware-specific runtimes (i.e. GPU-specific GL drivers, etc) into a different install

---

# Part 2: The Project

TODD

#### Boards and Variants

TODO
- Explain how we split up the project into boards/variants
- Explain the benfit: makes it much easier to support custom devices

#### Buildstream 2

TODO
- Explain that we ported to bst2
- Beneifts:
    - Much faster
    - Much better system for artifact caching
    - `git_repo` plugin
- Mention that fixed various long-standing warnings

#### CI

TODO
- Explain that we'll be implementing CI
- Explain how git_repo allows us to make nightly builds of carbonOS with the latest versions of everything
- Mention OpenQA, and how it's a stretch goal

#### Hosting

TODO
- Explain how Fosshost died
- Explain how our infrastructure is still (somehow) running on their servers
- Mention that this is still a big open question
    - We need CDN
    - We need file hosting. Hopefully something I can rsync the files to upload

---

# Final Comments

#### Attributions

I'd like to thank a couple of people and organizations for making everything I've talked about here possible:

- Lennart Poettering, Daan De Meyer, and the rest of the systemd maintainers and contributors: for the amazing
  work designing and implementing all these new technologies that carbonOS now relies on
- Sonny Piers, The GNOME Foundation, GNOME OS contributors, and other GNOME Project contributors: for the
  very warm welcome into my growing role in the GNOME community, for the help and guidance, and for
  (REDACTED)
- The BuildStream maintainers and contributors: for developing such a robust and flexible build tool.
  BuildStream 2 is awesome!
- The Linux Foundation Travel Fund: for their generous sponsorship of my upcoming travel to
  [All Systems Go!](https://all-systems-go.io/) and surrounding conferences
- The Ohio State University: for their generous academic scholarship, that has afforded me a summer of
  unemployment and thus allowed me to focus on all of this development!

#### Contributing

If you're interested in contributing, there are many different ways you can!
If you'd like to test out carbonOS, you can download it [here](/download).
If you'd like to contribute code or translation, check out the
[source code]({{ site.external_urls.git }})
and join the development channel:
[#carbonOS-devel on Matrix](https://matrix.to/#/#carbonOS-devel:matrix.org).
Thank you!


<!-- TODO: Get rid of redactions once I can talk about the things -->

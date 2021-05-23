# improved-broccoli
This is where @solvaholic is learning how to build MarlinFirmware/Marlin

## This is a work in progress

The contents of this repository are incomplete, they will change without notice, and they may not be fit for any sort of use whatsoever.

That said, you're welcome to copy, fork, or contribute and use it any way you like according to the terms of [its license](/LICENSE).

If you have feedback, are aware of a related project, or have suggestions for improving this one, I'd love to [hear from you](https://github.com/solvaholic/improved-broccoli/issues/new/choose) :bow:

## MarlinFirmware/Marlin

[MarlinFirmware/Marlin](https://github.com/MarlinFirmware/Marlin) (Marlin) is firmware you can run on your 3D printer, sortof the printer's operating system. I don't totally get how the pieces fit together, but someone I know uses it.

## Building firmware

I'm excited to learn about 3D printing. And I'm curious what it takes to build and install firmware. So I'm learning how to build and install Marlin.

Marlin looks to be written in C++. Don't know C or C++? That's OK. To build Marlin you don't need to know either: Marlin provides [example configurations](https://github.com/MarlinFirmware/Marlin#example-configurations) and clear, easy to follow [build instructions](https://github.com/MarlinFirmware/Marlin#building-marlin-20).

Those instructions will have you use [the Arduino IDE](https://www.arduino.cc/en/software) or [the PlatformIO IDE for VSCode](https://platformio.org/install/ide?install=vscode). I dislike installing and updating software, though, and I plan to store my Marlin configuration in a Git repository on GitHub.com.

## Why use a Git repository?

[Git](http://git-scm.com) provides an environment and tools for managing different versions of anything written in text files. Git is popular, which yields lots of community support. And, for me, Git is easy to use. It can be difficult to learn, and there are a tonne of helpful resources and people you can learn from.

If you're new to Git, or still learning, read _Ry's Git Tutorial_, a free Kindle ebook available [on amazon.com](https://www.amazon.com/Rys-Git-Tutorial-Ryan-Hodson-ebook/dp/B00QFIA5OC). Read it and do the exercises. It's quick, requires very little prior knowledge, and will help you learn and practice all the basic Git motions.

If you use Git and have any questions about why something happens the way it does, read [_Commits are snapshots, not diffs_](https://github.blog/2020-12-17-commits-are-snapshots-not-diffs/) on GitHub's blog. If that post doesn't all make sense to you that is OK: Read it all the way through, and set a reminder to read it again in a month.

## Why use GitHub.com?

For me this is easy: Nearly all the work I do using computers lives on GitHub.com. Some folks have reasons to choose different Git hosting options. Do what's right for you.

GitHub provides integrated tools for everything I've wanted to do with source code: Share, discuss, manage, test, build, secure, deploy .. plus: Anything a computer can do with your code, you can automate it all within GitHub's platform.

Hosting Git repositories on GitHub.com lets me use all their features and APIs, including [GitHub Actions](https://docs.github.com/actions), without having to host apps, install or update software, or manage text editor plugins. And, as if I needed more reasons to use GitHub, because GitHub.com provides a browser-based editor I can update my code from any computer, tablet, or smartphone with internet access.

Putting that all together: Hosting your Marlin config on GitHub.com provides ubiquitous access to the source code while enabling you to continuously integrate and deploy Marlin updates - without adding external dependencies.

If you're learning to use GitHub, check out <https://lab.github.com> and <https://github.community>.

## This repository

This repository is a workspace for figuring out how to achieve a few things...

### When I push changes to my config, they're automatically tested and built

Using GitHub Actions and a specified branch of **MarlinFirmware/Marlin**:

1. When changes are pushed to my config in any branch, run tests and add a status check
1. If (tests succeeded and changes were pushed to `main`) OR (status check is green and workflow was manually run) then build the firmware
1. After build succeeds then publish the firmware

### I can tell OctoPrint to install my firmware

idk yet how this'll work, but:

- OctoPrint must not interrupt a print for this work
- If multiple "udpate firmware" triggers are queued, OctoPrint should only act on the most recent

### When my firmware is published, OctoPrint installs it automatically

idk yet how this'll work, but:

- OctoPrint must not interrupt a print for this work
- If multiple "udpate firmware" triggers are queued, OctoPrint should only act on the most recent

### When the examples I follow are updated, my configs are updated

idk yet how this'll work. I imagine:

1. Each day at 1000 UTC my repo checks **MarlinFirmware/Configurations** for updates to configuration examples I follow
1. If there are changes to consider, update or create a pull request in this repo to incorporate them
1. After :point_up: all that works, teach it to ignore changes that would only comment out a line

### Every night my config is built against the codebase

idk yet how this'll work. I imagine:

1. Each day at 1000 UTC my repo checks **MarlinFirmware/Marlin** for updates since the previous build
1. If there are changes to consider, run tests and builds using my own configuration
1. Publish the freshly built firmware
1. If any errors, update or create an issue in this repo to address them


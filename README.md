# Workflow Manager
 [![Platform](https://img.shields.io/badge/platform-osx-lightgrey.svg)](https://en.wikipedia.org/wiki/MacOS) [![GitHub license](https://img.shields.io/github/license/ishammahajan/workflow-manager-macos.svg)](https://github.com/ishammahajan/workflow-manager-macos/blob/master/LICENSE)

Ever realise how much time you might be wasting switching between the contexts of two different projects you might be working on at the same time? Well, here is a solution! Workflow Manager for MacOS uses `Automator.app` and the power of Applescript integrations with [`Google Chrome`](https://www.google.com/chrome/) and [`iTerm`](https://www.iterm2.com/) to stop the minutes you waste switching between the different contexts of different projects (which add up to large amount of time) not considering how your mind distracts itself when doing menial work.

Currently implemented features include :-
- A Workflow, when created through `createworkflow`, makes a set of configuration files under `~/Documents/WorkflowManagement/{your-workflow-name}`. These configurations allow you to set apps which open up by default whenever you switch to this Workflow. They also allow you to set a default list of URLs which open in Google Chrome whenever you open the Workflow, more on this soon.
- In the same configuration folder, you can set a default set of shell commands you might want to execute when switching to that Workflow. This can be automatically `serve`ing files or websites in order to debug them, or automatically build and launch applications, etc. Optionally, you can you can create different profiles for each Workflow of yours in `iTerm`, and if the profile name matches the Workflow name you provided during `createworkflow`, a window with that profile opens up during the execution of configured commands (in `iterm-config` instead of the default profile!)
- When you switch from Workflow A to B, before quitting A, the URLs of currently opened tabs on Chrome are saved, and mapped to A. When you open Workflow A again, you are given a choice between opening the saved tabs/opening the default tabs.

## Installation

Uses [`Google Chrome`](https://www.google.com/chrome/) and [`iTerm`](https://www.iterm2.com/), please install those using the provided links.

Use the provided `setupworkflows` script in order to copy the files provided in `Setup` folder to `~/Library/Services` in order for your installed Workflows to function correctly, these files are their dependencies.

A file called `default_browser` will be created within `~/Documents/WorkflowManagement`, which defines which browser you use (so we can save and reopen the tabs correctly). This file is initialized with `Google Chrome`, so if you use that browser, you should be good to go. However, if you use `Firefox` (currently the only other browser we support), please change this file's value to `Firefox`.

We support `Firefox` browser by the use of a shell script which fetches the URLs of open tabs during a session. The file we use to fetch these links, however, is saved by `Firefox` using a proprietary compression format called `lz4`. To extract information from this, we make use of a python library written for this purpose. Which is why -

NOTE: If you use `Firefox`, you have to install `python3` and the `lz4` library. To do so, use the following :-

- `brew install python3`
  - `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"` if you don't have `brew` installed, yet.

- `pip3 install lz4`

## Usage

Use the `createworkflow` script in order to create your workflow! You will be prompted to install a 'Quick Action', please acknowledge it in order to successfully install it. If for some reason the mentioned prompt did not appear, please navigate to `~/Documents/WorkflowManagement/{your-workflow-name}` in order to find the appropriate file (named `{your-workflow-name}.workflow`) and open it.

There are three ways by which you can open a given Workflow.

- Setup a keyboard shortcut. To do so open the `System Preferences` and navigating to `Keyboard` &rarr; `Shortcuts` &rarr; `Services` and scroll down until you find your Workflow.
- Having any app in focus, click on the app's name in the `Menu Bar`, and click `Services` under it. You will find your Workflow listed under `General`.
- If your computer has a TouchBar, clicking on 'Quick Actions' tabs on it will bring you to a list of `Services`, among which your Workflow will be listed.

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
Feature requests are also contributions! Make sure you open an issue detailing the feature in as much detail as possible.

## License
[GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/)

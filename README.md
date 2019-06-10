# Workflow Manager

Ever realise how much time you might be wasting switching between the contexts of two different projects you might be working on at the same time? Well, here is a solution! Workflow Manager for MacOS uses `Automator.app` and the power of Applescript integrations with [`Google Chrome`](https://www.google.com/chrome/) and [`iTerm`](https://www.iterm2.com/) to stop the minutes you waste switching between the different contexts of different projects (which add up to large amount of time) not considering how your mind distracts itself when doing menial work.

Currently implemented features include :-
- A Workflow, when created through `createworkflow`, makes a set of configuration files under `~/Documents/WorkflowManagement/{your-workflow-name}`. These configurations allow you to set apps which open up by default whenever you switch to this Workflow. They also allow you to set a default list of URLs which open in Google Chrome whenever you open the Workflow, more on this soon.
- In the same configuration folder, you can set a default set of shell commands you might want to execute when switching to that Workflow. This can be automatically `serve`ing files or websites in order to debug them, or automatically build and launch applications, etc. Optionally, you can you can create different profiles for each Workflow of yours in `iTerm`, and if the profile name matches the Workflow name you provided during `createworkflow`, a window with that profile opens up during the execution of configured commands (in `iterm-config` instead of the default profile!)
- When you switch from Workflow A to B, before quitting A, the URLs of currently opened tabs on Chrome are saved, and mapped to A. When you open Workflow A again, you are given a choice between opening the saved tabs/opening the default tabs. 

## Installation

Uses [`Google Chrome`](https://www.google.com/chrome/) and [`iTerm`](https://www.iterm2.com/), please install those using the provided links.

Use the provided `setupworkflows` script in order to copy the files provided in `Setup` folder to `~/Library/Services` in order for your installed Workflows to function correctly, these files are their dependencies.

## Usage

Use the `createworkflow` script in order to create your workflow! You will be prompted to install a 'Quick Action', please acknowledge it in order to successfully install it. If for some reason the mentioned prompt did not appear, please navigate to `~/Documents/WorkflowManagement/{your-workflow-name}` in order to find the appropriate file (named `{your-workflow-name}.workflow`) and open it.

There are three ways by which you can open a given Workflow.
- Setup a keyboard shortcut. To do so open the `System Preferences` and navigating to `Keyboard` -> `Shortcuts` -> `Services` and scroll down until you find your Workflow.
- Having any app in focus, click on the app's name in the `Menu Bar`, and click `Services` under it. You will find your Workflow listed under `General`.
- If your computer has a TouchBar, clicking on 'Quick Actions' tabs on it will bring you to a list of `Services`, among which your Workflow will be listed.

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
Feature requests are also contributions! Make sure you open an issue detailing the feature in as much detail as possible.

## License
[GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/)

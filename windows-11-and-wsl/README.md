<h1>
  <span class="headline">ITB Installfest Early 2025</span>
  <span class="subhead">Windows 11 and WSL</span>
</h1>

## What is WSL?

Have you never heard of WSL before? You're not alone; here's what Microsoft has to say about it:

<blockquote class="quote">
  The Windows Subsystem for Linux lets developers run a GNU/Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dual-boot setup.
  <span>The <a href="https://learn.microsoft.com/en-us/windows/wsl/">WSL documentation</a></span>
</blockquote>

That's fun, but what does that mean in practice? As a Windows user, you can run the same command line apps and use the same commands as your macOS and Ubuntu neighbors in the cohort.

## What you need to begin *(you must read this, do not skip this, this is important)*

- ***A device running Windows 11 version 24H2 (OS Build 26100 or greater).***

  To find your Windows version and build number, use <kbd>Windows Logo Key</kbd> + <kbd>R</kbd> on your keyboard, type `winver`, and select **OK**. You'll see a dialog window like the one below. Note the Version: 24H2.

  ![A dialog box demonstrating a Windows 11 PC eligible for use in ITB.](./assets/winver-dialog.png)

- A user account with administrative privilege to your local installation of Windows 11.
- A Microsoft Account with access to the Microsoft Store application. All requirements are free, but some are only available from the Microsoft Store.
- At least 40GB of free hard drive space.
- At least 8GB of RAM. 16GB of RAM or more is preferable and will improve your learning experience (particularly when screen sharing in Zoom).
- A modern processor capable of running virtual environments - specifically processors with Intel Virtualization Technology (Intel VT) or AMD Virtualization (AMD-V) technology.

## Troubleshooting

If you run into issues during Installfest, please reach out to your Installfest point of contact.

## Slack

We will be using Slack to communicate throughout the course. Download the app [here](https://slack.com/downloads/) and install it. Please do not use the in-browser version of Slack, as it makes managing notifications unnecessarily difficult and makes it easy to miss important class information - the app is the way to go.

We also recommend downloading the Slack app for your mobile device to stay in touch on the go - you can find quick QR code links inside the toggles below. You won't need this often, but it can be handy in emergencies.

<details>
<summary>Slack - iOS</summary>

Scan this QR code with your iOS device to get the Slack app from the App Store.

![A QR code for Slack on the iOS App Store](installfest-assets/shared/slack-ios-qr-code.png)

</details>

<details>
<summary>Slack - Android (Google Play)</summary>

Scan this QR code with your Android device to get the Slack app from the Google Play Store.

![A QR code for Slack on the Google Play Store](installfest-assets/shared/slack-android-qr-code.png)

</details>

## Zoom

We'll hold class in Zoom. If you haven't already, download the Zoom client from [here](https://zoom.us/download#client_4meeting) and install it.

## Updating Microsoft Store apps

We need the newest version of some bundled apps before we can continue. Launch the **Microsoft Store** application and go to the **Updates & downloads** page. The link to the **Updates & downloads** page is outlined in red below.

![The Microsoft Store home page with the Downloads link highlighted in red.](./assets/microsoft-store-home.png)

On the **Updates & downloads** page, select **Get updates**. The **Get updates** button is outlined in red below.

![The Get Updates button on the Library page highlighted in red.](./assets/microsoft-store-library.png)

After you've installed the updates, you can close the Microsoft Store app.

## Run Terminal as Administrator

Windows 11 comes with a built-in Terminal application for us to use.

To launch the Terminal application, press the <kbd>Windows Key</kbd> to launch Windows Search and type `Terminal`. Then, expand the available options in the right panel, as shown in the screenshot below.

![Terminal found using a search in the Start menu. The expand option is highlighted.](./assets/start-search-terminal.png)

Finally, select **Run as administrator** in the right panel. You will be prompted to allow elevated permissions - do so.

![With the expand option selected, the Run as administrator option is highlighted.](./assets/start-terminal-admin.png)

After you've launched the Windows Terminal app, ***pin it to your taskbar*** by right-clicking the icon in the taskbar and selecting the **Pin to taskbar** option. This is how we will eventually launch Ubuntu.

![PowerShell running with administrative access in the Windows Terminal. Note the shield in the title bar indicating that PowerShell is running with elevated permissions!](./assets/powershell-admin.png)

Note the shield in the title bar indicating that PowerShell is running with elevated permissions!

## A note on copying commands

When possible, ***please copy the commands from this page***. You will use most of the commands here once and never again. Typing them out will only introduce the possibility of you making errors. Certain commands will require you to alter portions of them - this is specifically called out when they appear. There are no bonus points for doing work already done for you.

### Copying text in code blocks

To copy text from code blocks, use your mouse to hover over the code block. A **Copy** button will appear in the upper right corner. Click this, and the text in the code block will be put on your clipboard, ready to be pasted.

![A code bock shown in GitHub pages. The Copy button is being pointed at by a red arrow.](./assets/code-copy.png)

## Install WSL

Use this command to install Ubuntu in WSL2. You may be asked to allow apps to have administrative access throughout this process; do so when asked.

```powershell
wsl --install -d Ubuntu
```

To run a command, paste (or type) it into your terminal, confirm it matches what you intended, and press the <kbd>Enter</kbd> key.

Below, you can see the expected output shown in PowerShell after running the install command.

![The expected output shown in PowerShell after running the above command.](./assets/powershell-wsl-install.png)

## Restart your computer

Save any work you want to keep, including this page, and restart your computer to continue!

Upon restarting, the Ubuntu Installer will launch automatically (as shown below) and then finalize the installation, which may take a while. Once you're prompted to supply a user account, continue to the next step. If you get an error message or run into another issue, check out the **Handling errors 💔** subsection below.

![The Ubuntu Installer auto-running after a system restart.](./assets/ubuntu-install.png)

### Handling errors 💔

#### The Ubuntu Installer doesn't launch automatically

If the Ubuntu Installer doesn't launch automatically after restarting your computer, open the **Terminal** application and run the following command:

```powershell
wsl --install -d Ubuntu
```

This command should download and install Ubuntu as shown below:

![Powershell being used to install Ubuntu.](./assets/powershell-wsl-install.png)

Then, launch the Ubuntu application by searching for **Ubuntu** in the Start menu and continue to the next step.

#### Virtual Machine error

You may see this message after your machine restarts:

```plaintext
Please enable the Virtual Machine Platform Windows feature and 
ensure virtualization is enabled in the BIOS.
```

Or this message:

```plaintext
The virtual machine could not be started because a required feature is not installed.
```

If either of these errors occurs, run the command below in PowerShell with Administrator permissions (reference the above instructions to launch PowerShell as the Administrator):

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

and restart your machine.

***If the error persists after restarting, you likely need to enter your BIOS and enable Intel Virtualization Technology (Intel VT) or AMD Virtualization (AMD-V) technology to continue. This error is most common with AMD processors.***

#### I do not have any of the above errors

Reach out to your Installfest point of contact for further guidance.

## Creating a User Account

You will then be prompted to create a username and password. The username should contain any spaces. The username doesn't need to match your Windows username, but it can if you would like. *The password will not be visible as you type it. This is common in many command-line applications.* It is ***vital*** that you do not forget this password, as you will use it throughout the course to interact with WSL.

![Ubuntu successfully launching with a completed setup for the first time!](./assets/ubuntu-first-time-launch.png)

🎊 You're now running WSL 2! Congrats! Go ahead and close the Ubuntu application - we won't use it again. Don't close this guide though; you're not entirely done yet.

## Launch the Terminal

Launch the Terminal application.

The terminal will initially launch with only a Windows PowerShell tab. Let's configure it to launch into your Ubuntu installation by default. Select the dropdown arrow in the title bar, then select **Settings** to open the Terminal settings.

![Accessing the Settings tab in Terminal.](./assets/windows-terminal-settings-access.png)

The **Settings** tab should open with the **Startup** section already selected. The first order of business is to change the **Default profile** setting in this section to **Ubuntu**. While we're here, change the **Default terminal application** to **Windows Terminal**. After making these modifications, click the **Save** button.

![In the Settings tab in Terminal, the Startup section has been selected and the Default profile has been changed to Ubuntu.](./assets/windows-terminal-startup-settings.png)

Close the Terminal app one more time.

## Launching Ubuntu

Drum roll! Launch the Terminal application, and if everything has been successful so far, you should see a window very similar to the one below.

![Successfully launching into Ubuntu by default using the terminal.](./assets/windows-terminal-ubuntu-first-launch.png)

A couple of items to note:

- The terminal should launch directly into the Ubuntu environment.
- The command line prompt should read `Your_Ubuntu_Username@Your_Device_Name:~$`. As shown above, the Ubuntu Username is `student`, and the device name is `win11`. Yours will be different. The `~` represents that we are in the *current user's home directory*.

## Updating and upgrading packages

Windows *does not* manage your Linux installation and will not automatically update it. To manually do so, use this command:

```bash
sudo apt update && sudo apt upgrade
```

Do this now. Enter your Ubuntu password when prompted, and accept the changes to be made by entering <kbd>Y</kbd> when prompted to continue.

After that process is complete, it's time to ensure you're upgraded to the newest LTS version of Ubuntu.

## Upgrading Ubuntu

Close any open Terminal sessions and re-launch the Terminal application. Run this command to start the update:

```bash
sudo do-release-upgrade
```

There are three possible outcomes from this command:

- The first is that you'll receive a message that prints a message including the phrase: **There is no development version of an LTS available**. If that's the case, continue from the **Zsh** steps below.
- The second is that you'll be prompted multiple times to confirm that you would like to proceed with adding, removing, and changing various packages - proceed each time you are prompted. When this process has finished, reboot your machine.
- The third is that you have encountered an error message; check out the **Handling errors 💔** section below.

### Handling errors 💔

You may see this printed to the terminal after you run `sudo do-release-upgrade`:

```plaintext
You have not rebooted after updating a package which requires a reboot. 
Please reboot before upgrading.
```

If you see this message, restart your computer and retry the **Upgrading Ubuntu** step.

## Zsh

Bash is Ubuntu's default shell (command interpreter), but Z shell is more commonly used in modern systems by default, so that's what we will use. Install it with this command, and accept the changes to be made by entering <kbd>Y</kbd> when prompted to continue:

```bash
sudo apt install zsh
```

Verify the installation with this command:

```bash
zsh --version
```

The version number should be 5.8 or greater

Make Zsh the default shell with this command. Enter your Linux password when prompted.

```bash
chsh -s $(which zsh)
```

Close Ubuntu and the Terminal session with this command:

```bash
logout
```

Launch the Terminal application. As shown below, you should be prompted to run a configuration setup for new users:

![Terminal after launching Zsh for the first time.](./assets/zsh-first-launch.png)

Enter `2` to accept the default configuration.

Your terminal prompt should look a little different now!

![Zsh in action.](./assets/zsh-in-action.png)

Let's confirm it worked with this command:

```bash
echo $0
```

This should print `-zsh`.

## Oh My Zsh

We will also install Oh My Zsh - an open-source, community-driven framework for managing your Zsh configuration. Use this command:

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

![A successful installation of Oh My Zsh](./assets/oh-my-zsh-success.png)

Note that your prompt has now changed to `→ ~`. This is the desired outcome!

## Terminal Theme

This step isn't required, but some people don't like the Ubuntu default terminal theme. If you'd like to change it, you can return to the Terminal's Settings menu you were in earlier, as shown below:

![Accessing the Settings tab in Terminal.](./assets/windows-terminal-settings-access-theme.png)

Once in the Settings tab, select the **Ubuntu** profile on the left side of the window.

![Select the Ubuntu profile in the Settings tab.](./assets/windows-terminal-settings-ubuntu.png)

Scroll down and select the **Appearance** option in the **Additional settings** section.

![Select the Appearance option in the Additional settings section.](./assets/windows-terminal-settings-ubuntu-appearance.png)

You can change the **Color scheme** to any of the available options. The **Campbell** theme is a popular choice.

You can also change the **Font face** to any of the available options. The **Cascadia Code** font is a popular choice.

![Changing the appearance of the Ubuntu terminal.](./assets/windows-terminal-settings-ubuntu-appearance-changes.png)

The rest of this guide shows the terminal with those two options selected. You can see what this looks like below. Feel free to make any customizations you like!

![The final appearance of the Windows Terminal.](./assets/windows-terminal-final-appearance.png)

## Visual Studio Code

Install Visual Studio Code from [the Visual Studio Code site](https://code.visualstudio.com/). Install Visual Studio Code on Windows - not in the WSL file system. Accept any default options provided during the setup; there is no need to modify these selections.

### Install the WSL extension

After you've installed VS Code, navigate to the [WSL extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) page in your browser. Click the **Install** button outlined in red below to open the extension marketplace in VS Code. If your browser has any security prompts asking if you want to use the link to open VS Code, accept them.

![The page for the WSL extension in the VS Code Extension Marketplace shown in the Chrome browser.](./assets/vsc-wsl-extension-browser.png)

On the page for the extension in VS Code, click the **Install** button as outlined in red below.

![The page for the WSL extension in the VS Code Extension Marketplace.](./assets/vsc-wsl-extension-install.png)

**Microsoft has this to say about running extensions on WSL:**

> The WSL extension splits VS Code into a "client-server" architecture, with the client (the user interface) running on your Windows machine and the server (your code, Git, plugins, etc) running remotely in WSL.

When running VS Code with the WSL extension, selecting the 'Extensions' tab will display a list of extensions split between your "local" Windows installation and your "remote" WSL installation.

Installing a local extension, like a theme, only needs to be done once.

Some extensions, like the Python extension or any extension that handles linting or debugging, must be installed separately in Ubuntu. VS Code will handle this automatically, so you don't need to worry about it.

While you don't need to think too much about it, this concept is ***VERY IMPORTANT***. You are now running two separate operating systems simultaneously on your machine. When something is installed in one operating system, the other will not know about it! Let's explore this concept more.

## GitHub (GH)

At its core, GitHub (commonly abbreviated as GH) is a service for hosting Git repositories (which we'll talk about soon) in the cloud. It also enables developers to collaborate on projects much more effectively. It might help to think of it as a social media platform for you and more than 100 million developers worldwide.

If you don't have an account there, create one now. Visit [`https://github.com`](https://github.com) and sign up. While there are paid account tiers, GitHub offers a very generous free tier that offers more than you need for the course.

## Git in Windows 11

While you could use Git on Windows as a source control manager, we won't be for our purposes - instead, we will use it mainly for its credential management features. Download Git for Windows 11 from [here](https://git-scm.com/downloads). Follow the installation instructions below.

***Do not change the install location.***

***You will be given many prompts on features to install and choices to make while installing Git. All of these may be left as their default, except for the ones below.***

Unless you have a specific need for the features unchecked, we recommend you use only install the checked components below:

![Note we have unchecked some features not required for our purposes that may only be confusing, get in the way, or waste hard drive space.](./assets/git-component-install.png)

Note we have unchecked some features not required for our purposes that may only be confusing, get in the way, or waste hard drive space.

Again, we won't be using Git features on the Windows side, so having a Start Menu folder would only be confusing and create clutter - select the option for **Don't create a Start Menu folder**.

![When prompted to Select a Start Menu Folder, we are opting to not create a Start Menu folder.](./assets/git-start-menu.png)

When prompted, you should select Use Visual Studio Code as Git's default editor (this does not really matter now, but if you ever use Git in Windows for any reason in the future, this will already be set up for you).

![We are using VS Code as Git's default editor (just in case you ever use Git in Windows for any reason in the future, this will already be set up for you)](./assets/git-default-editor.png)

We'll be using the `main` branch for all our work. Go ahead and set this up now. Again, this setting won't directly impact us as we use Ubuntu, but if you ever do use Git for Windows in the future, you won't have to do this work again later. `main` as the default branch name is the future.

![`main` as the default branch name is the future.](./assets/git-default-branch.png)

Continue from this point, leaving all other settings as their default.

Finally, when installation has been completed, you can uncheck **View Release Notes** and hit **Finish**!

![You've completed the installation of Git on Windows, great work. Now on to Ubuntu!](./assets/git-final-step.png)

You've completed the installation of Git on Windows. Now on to Ubuntu!

## Git in Ubuntu

Close any open **Terminal** sessions and re-launch the **Terminal** application.

Git comes pre-installed with Ubuntu, but ensure you have the most recent stable version with:

```bash
sudo add-apt-repository ppa:git-core/ppa
```

You may be prompted for your Ubuntu password. If you are, enter it. When prompted to continue, press <kbd>Enter</kbd>. If you encounter an error during this process, check out the **Handling errors 💔** sub-section below.

Then enter:

```bash
sudo apt-get update
```

and then finally, use this command to install Git on your machine:

```bash
sudo apt-get install git
```

Enter <kbd>Y</kbd> when prompted to continue.

### Handling errors 💔

After running the `sudo add-apt-repository ppa:git-core/ppa` command above, you may encounter an `HTTPError`. If you do, ensure that your system date and time are correct, then try the same command again. If this does not resolve your issue, reach out to your Installfest point of contact for assistance!

### Git config

With Git installed, we can now make some configuration changes to make it a more effective tool. Complete all of the following configuration steps.

Use the below command to add a user name to Git, which will be used to identify your commits. Replace `User Name` with a name of your choice. Make sure you leave the quotes surrounding your username. Keep the name somewhat professional, or just use your name - this will be used to identify your commits on GitHub. There will not be any output from this command.

```bash
git config --global user.name "User Name"
```

Next, use the below command to add an email to Git, which will be used to identify your commits. Replace `user@email.com` with the email address associated with your [`https://github.com`](https://github.com) account. **The email you provide must match the email address associated with your GitHub account.** Ensure you leave the quotes surrounding your email.

There will not be any output from this command.

```bash
git config --global user.email "user@email.com"
```

Set the default branch name to `main` with the below command. There will not be any output from this command.

```bash
git config --global init.defaultBranch main
```

Set the default Git editor to VS Code with the below command. There will not be any output from this command.

```bash
git config --global core.editor "code --wait"
```

By default, Git will ask for a new commit message when commits are brought into a Git repo. The following command will force the default commit message for all those commits instead of prompting you to add a commit message.

While this isn't a Git command, we're still tackling it as part of this section since it changes Git's behavior. There will not be any output from this command.

```bash
echo "export GIT_MERGE_AUTOEDIT=no" >> ~/.zshrc
```

Turn off rebasing as the default behavior when pulling from a repo with the below command. There will not be any output from this command.

```bash
git config --global pull.rebase false
```

Configure Git to track case changes in file names. There will not be any output from this command.

```bash
git config --global core.ignorecase false
```

Finally, all that work we just did to get Git up and running on Windows is about to pay off: Make the Ubuntu installation of Git use the Windows Git Credential Manager Core:

```bash
git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/bin/git-credential-manager.exe"
```

Now, any Git operation you perform within Ubuntu will use the Git Credential Manager, which is managed by the Windows installation of Git. There will not be any output from this command.

You may have noticed from the command above all the files you have stored in Windows are available on the Ubuntu side in `/mnt/c`, but accessing them comes at a significant performance cost. Therefore, the code you write will be stored in the Ubuntu storage space, and we'll only interact with Windows files and apps when necessary. Additionally, you can access the Ubuntu storage space from Windows at `\\wsl$\Ubuntu\`.

You shouldn't have to bring files from Windows to Ubuntu or Ubuntu to Windows often, but the above information may be useful to you in certain circumstances.

### Configuring a `.gitignore_global` file

***Note: This step is vital to getting a job after the course. If you do not complete these steps exactly, it will look extremely bad to a future employer when they look over your GitHub repos.***

Proper code, utilities, and the use of Git ignore files prevent us from uploading private secrets to the internet.

A global Git ignore file (<code class="filepath">.gitignore_global</code>) will prevent us from uploading private secrets to the internet across all of your projects so that you don't have to worry about making the appropriate entries in every project's Git ignore file.

Use this command to create a <code class="filepath">.gitignore_global</code> file in the user directory:

```bash
touch ~/.gitignore_global
```

There will not be any output from this command.

Next, configure Git to use this file:

```bash
git config --global core.excludesfile ~/.gitignore_global
```

Open the new <code class="filepath">.gitignore_global</code> file in VS Code:

```bash
code ~/.gitignore_global
```

Since this is likely the first time you are running the `code` command, you'll see an output like the one below.

![Creating and opening .gitignore_global in VS Code if this is the first time you are running the code command.](./assets/vsc-wsl-first-launch.png)

This may be your first time launching VS Code to work with an actual file. If so, congrats! You'll  arrive at a page that should look a lot like this:

![The new .gitignore_global file open in VS Code.](./assets/vsc-gig-launch.png)

Here, you see the new <code class="filepath">.gitignore_global</code> file open in VS Code. Note the **WSL** icon in the lower-left corner.

### Here is a [.gitignore_global file for you to use](../global-git-ignore.md)

Open the above page and copy the contents of the code block from the page using the **Copy** button.

Return to VS Code, then click inside the editor (the main portion of the VS Code window).

Paste the contents of the file you copied into the editor in VS Code. Doing this should result in your VS Code window looking similar to this:

![The end of the new .gitignore_global file.](./assets/vsc-gig-content.png)

Congrats, you just edited your first file in VS Code! This is a great time to turn on **Auto Save**! The **Auto Save** setting is in the **File** menu - select it, then re-open the **File** menu to ensure that there is a checkmark next to the **Auto Save** option, as shown below.

![Auto Save checked in the File menu, indicating that Auto Save is enabled.](./assets/vsc-auto-save-enabled.png)

This should save the file, but let's be sure by manually saving it using **Save** in the **File** Menu or pressing <kbd>Ctrl</kbd> + <kbd>S</kbd>.

You can close VS Code for now.

## Python

Python is an extremely popular programming language with a simple syntax. It is a natural choice for developers to have in their toolbox. Python must be installed on your machine to execute programs written with it.

To install Python, run these commands in order in your terminal application, agreeing to any prompts that appear:

```bash
sudo apt-get install software-properties-common
```

```bash
sudo add-apt-repository ppa:deadsnakes/ppa
```

If it doesn't look like anything has happened for a long time after running the above command, press <kbd>Ctrl</kbd> + <kbd>C</kbd> on your keyboard, and re-run the command.

```bash
sudo apt-get update
```

```bash
sudo apt-get install python3.13
```

Make Python 3.13 the default version used with:

```bash
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.13 10
```

You can test the installation by running `python3 --version`.

### Install pip

pip is the package installer for Python. You'll need it to use Python packages found on the [Python Package Index (PyPI)](https://pypi.org/).

Install pip with this command:

```bash
sudo apt install python3-pip
```

## `~/code` directory

You'll need somewhere on your computer to put all your work in the course - that's what the `~/code` directory will be for you! All course content assumes you will have this directory, so let's create it now with this command in your terminal:

```bash
mkdir ~/code
```

## OH WOW YOU DID IT!

You are now set up to start developing in Linux on Windows! Be very proud of yourself; that was quite the process!

## Microsoft PowerToys (optional, but recommended)

From Microsoft:

> Microsoft PowerToys is a set of utilities for power users to tune and streamline their Windows experience for greater productivity.

Among its many useful tools, PowerToys includes one of the best window managers for Windows: FancyZones, which allows you to customize window layouts and get the best setup just for you.

Get PowerToys [here](https://github.com/microsoft/PowerToys/releases/download/v0.76.0/PowerToysSetup-0.76.0-x64.exe).

Learn more about FancyZones [here](https://docs.microsoft.com/en-us/windows/powertoys/fancyzones) and the rest of the tools that come with PowerToys [here](https://learn.microsoft.com/en-us/windows/powertoys/).

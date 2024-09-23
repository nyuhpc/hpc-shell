---
title: "Connecting to the remote HPC system"
teaching: 25 
exercises: 10
questions:
- How do I open a terminal?
- How do I connect to a remote computer?
- What is an SSH key?
objectives:
- Connect to a remote HPC system.
keypoints:
- To connect to a remote HPC system using SSH and a password,
  run `ssh <NetID>@greene.hpc.nyu.edu`.
- To connect to a remote HPC system using SSH and an SSH key,
  run `ssh -i ~/.ssh/key_for_remote_computer <NetID>@greene.hpc.nyu.edu`.
---

## Prerequisites
To access the Greene HPC cluster, you must be connected to the NYU network. If you are physically on campus and connected via a wired connection in your office or through NYU's WiFi, you can directly SSH into the clusters without any additional steps. However, if you are off-campus or working remotely, connecting through the NYU VPN or using the gateway servers is required to establish a secure connection to the HPC systems.

### Remote Connections with the NYU VPN & HPC Gateway Server
If you are connecting from a remote location that is not on the NYU network (your home for example), you have two options: 

1. VPN Option: set up your computer to use the NYU VPN. Once you've created a VPN connection, you can proceed as if you were connected to the NYU net.  

2. Gateway Option: go through our gateway servers (example below). Gateways are designed to support only a very minimal set of commands and their only purpose is to let users connect HPC systems without needing to first connect to the VPN.

### Log into the Greene Cluster
NYU Campus: From within the NYU network, that is, from an on-campus location, or after you VPN inside NYU's network, you can login to the HPC clusters directly.

Off-campus: The host name of Greene is 'greene.hpc.nyu.edu'. Logging in to Greene is the two-stage process. The HPC clusters (Greene) are not directly visible to the internet (outside the NYU Network). If you are outside NYU's Network (off-campus) you must first login to a bastion host named gw.hpc.nyu.edu.

From within the NYU network, that is, from an on-campus location, or after you VPN inside NYU's network, you can log in to the HPC clusters directly. You do not need to log in to the bastion host.

To log in to the HPC cluster (Greene), simply use:

```
ssh <NYUNetID>@greene.hpc.nyu.edu
```

For access from Windows stations using PuTTY, please [click here](#).

To connect to VPN from Linux/MAC, please [click here](#).

From an off-campus location (outside NYU-NET), logging in to the HPC clusters is a two-step process:

1. First, log in to the bastion host, `gw.hpc.nyu.edu`. From a Mac or Linux workstation, this is a simple terminal command (replace `<NYUNetID>` with your NetID). Your password is the same password you use for NYU Home:

```bash
ssh <NYUNetID>@gw.hpc.nyu.edu
```

    Windows users will need to use PuTTY, see [here](#) for instructions.

2. Next, log in to the cluster. For Greene, this is done with:

```bash
ssh <NYUNetID>@greene.hpc.nyu.edu
```


## Opening a Terminal
Accessing the Greene HPC cluster is primarily done through the Command Line Interface (CLI). A CLI provides a text-based environment that allows users to manage files, run programs, and navigate directories via command input. On macOS, the built-in CLI tool is Terminal, while Windows 10 users can leverage the Windows Subsystem for Linux (WSL) for similar functionality. Additionally, a popular tool for connecting to Linux servers from Windows is PuTTY, a free SSH client.

Connecting to an HPC system is most often done through a tool known as "SSH"
(Secure SHell) and usually SSH is run through a terminal. So, to begin using an
HPC system we need to begin by opening a terminal. Different operating systems
have different terminals, none of which are exactly the same in terms of their
features and abilities while working on the operating system. When connected to
the remote system the experience between terminals will be identical as each
will faithfully present the same experience of using that system.

Here is the process for opening a terminal in each operating system.

### Linux

There are many different versions (aka "flavours") of Linux and how to open a
terminal window can change between flavours. Fortunately most Linux users
already know how to open a terminal window since it is a common part of the
workflow for Linux users. If this is something that you do not know how to do
then a quick search on the Internet for "how to open a terminal window in" with
your particular Linux flavour appended to the end should quickly give you the
directions you need.

To connect to the gateway servers, simply open a terminal application and enter the following command:
```bash
ssh <NetID>@gw.hpc.nyu.edu
```

After typing in your password you will be logged in to the cluster. Once this connection is established, you can make one more hop and connect to one of the HPC clusters:
```bash
# this will connect you to Greene HPC cluster
ssh <NetID>@greene.hpc.nyu.edu
```

### Mac

Macs have had a terminal built in since the first version of OS X since it is
built on a UNIX-like operating system, leveraging many parts from BSD (Berkeley
Software Distribution). The terminal can be quickly opened through the use of
the Searchlight tool. Hold down the command key and press the spacebar. In the
search bar that shows up type "terminal", choose the terminal app from the list
of results (it will look like a tiny, black computer screen) and you will be
presented with a terminal window. Alternatively, you can find Terminal under
"Utilities" in the Applications menu.

To connect to the gateway servers, simply open a terminal application and enter the following command:

```bash
ssh <NetID>@gw.hpc.nyu.edu
```

After typing in your password you will be logged in to the cluster. Once this connection is established, you can make one more hop and connect to one of the HPC clusters:

```bash
# this will connect you to Greene HPC cluster
ssh <NetID>@greene.hpc.nyu.edu
```

### Windows

While Windows does have a command-line interface known as the "Command Prompt"
that has its roots in MS-DOS (Microsoft Disk Operating System) it does not have
an SSH tool built into it and so one needs to be installed. There are a variety
of programs that can be used for this; a few common ones we describe here, as
follows:

#### Git BASH

Git BASH gives you a terminal like interface in Windows. You can use this to
connect to a remote computer via SSH. It can be downloaded for free from
[here](https://gitforwindows.org/).

#### Windows Subsystem for Linux

The Windows Subsystem for Linux also allows you to connect to a remote computer
via SSH. Instructions on installing it can be found
[here](https://docs.microsoft.com/en-us/windows/wsl/install-win10).

#### MobaXterm

MobaXterm is a terminal window emulator for Windows and the home edition can be
downloaded for free from
[mobatek.net](https://mobaxterm.mobatek.net/download-home-edition.html). If you
follow the link you will note that there are two editions of the home version
available: Portable and Installer. The portable edition puts all MobaXterm
content in a folder on the desktop (or anywhere else you would like it) so that
it is easy to add plug-ins or remove the software. The installer edition adds
MobaXterm to your Windows installation and menu as any other program you might
install. If you are not sure that you will continue to use MobaXterm in the
future, the portable edition is likely the best choice for you.
MobaKeyGen, see the MoabXterm 
[documentation](https://mobaxterm.mobatek.net/documentation.html) 

Download the version that you would like to use and install it as you would any
other software on your Windows installation. Once the software is installed you
can run it by either opening the folder installed with the portable edition and
double-clicking on the executable file named `MobaXterm_Personal_11.1` (your
version number may vary) or, if the installer edition was used, finding the
executable through either the start menu or the Windows search option.

Once the MobaXterm window is open you should see a large button in the middle
of that window with the text "Start Local Terminal". Click this button and you
will have a terminal window at your disposal.

#### PuTTY

It is strictly speaking not necessary to have a terminal running on your local
computer in order to access and use a remote system, only a window into the
remote system once connected. PuTTY is likely It is, strictly speaking, not
necessary to have a terminal running on your local computer in order to access
and use a remote system, only a window into the remote system once connected.
PuTTY is likely the oldest, most well-known, and widely used software solution
to take this approach.

PuTTY is available for free download from
[https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html). 
Download the version that is correct for your operating system and install it 
as you would other software on your Windows system. Once installed it will be 
available through the start menu or similar.
puttygen, see the Putty 
[documentation](https://www.chiark.greenend.org.uk/~sgtatham/putty/docs.html)

Running PuTTY will not initially produce a terminal but instead a window full
of connection options. Putting the address of the remote system in the "Host
Name (or IP Address)" box and either pressing enter or clicking the "Open"
button should begin the connection process.

If this works you will see a terminal window open that prompts you for a
username through the "login as:" prompt and then for a password. If both of
these are passed correctly then you will be given access to the system and will
see a message saying so within the terminal. If you need to escape the
authentication process you can hold the Control (<kbd>Ctrl</kbd>) key and press
the <kbd>c</kbd> key to exit and start again.

Note that you may want to paste in your password rather than typing it. Use
<kbd>Ctrl</kbd> plus a right-click of the mouse to paste content from the
clipboard to the PuTTY terminal.

For those logging in with PuTTY it would likely be best to cover the terminal
basics already mentioned above before moving on to navigating the remote
system.

### Open OnDemand (Web-based Graphical User Interface)
Open OnDemand is an open source project funded by the National Science Foundation (NSF). Open OnDemand is designed to create easier access to users to interface with HPC systems. Originally developed by Ohio Supercomputer Center (OSC), used by many universities around the world, and now servicing the NYU Greene HPC cluster.

Open OnDemand has a variety of convenient tools to manage files, access the command line, manage and monitor jobs, and launch interactive applications, such as Jupyter Notebooks, RStudio sessions, and even full Linux Desktops. 

Features Include:

Easy file management - upload and download files, view HTML and pictures without downloading

Command-line shell access without any SSH client locally installed

Job management and monitoring

Full Linux desktop experience without X11

Interactive Apps such as JupyterHub and RStudio without the need for port forwarding

Open OnDemand (OOD) is accessible to all users with a valid NYU HPC account while on-campus network or through a VPN.

To access OOD visit: https://ood.hpc.nyu.edu (VPN Required)

#### Access the Shell

Under the clusters menu you can select the Greene Shell Access option to access the Linux shell. No local SSH client is required.

#### Interactive Applications

GUI based applications are accessible without the need for port or X11 forwarding. Select the Interactive Apps menu, select the desired application, and submit the job based on required resources and options. 

#### Troubleshooting Connections to Open OnDemand

A common issue that can occur is receiving an error that the Open OnDemand page cannot be reached. Sometimes this can indicate that the service is down, but often this is an issue with the the local browser cache. You can test this by opening a private browser window and seeing if https://ood.hpc.nyu.edu will load. If it does, try deleting the cache for https://ood.hpc.nyu.edu in your browser history to resolve this issue.

In Chrome, this can be done by navigating to this page in your settings:

chrome://settings/content/all?searchSubpage=ood.hpc.nyu.edu&search=site+data

The link above will automatically search for the Open OnDemand site data and cookies. You can then simply click on the trashcan icon to delete the site cache.

Once done, try navigating again to https://ood.hpc.nyu.edu and the site should load. For other issues please email hpc@nyu.edu.

## Creating an SSH key

SSH keys are an alternative method for authentication to obtain access to 
remote computing systems. They can also be used for authentication when
transferring files or for accessing version control systems. In this section
you will create a pair of SSH keys, a private key which you keep on your
own computer and a public key which is placed on the remote HPC system
that you will log in to.

### Linux, Mac and Windows Subsystem for Linux

Once you have opened a terminal check for existing SSH keys and filenames
since existing SSH keys are overwritten,
```
$ ls ~/.ssh/
```
{: .language-bash}

then generate a new public-private key pair,
```
$ ssh-keygen -t ed25519 -a 100 -f ~/.ssh/id_{{ site.workshop_host }}_ed25519
```
{: .language-bash}

- `-o` (no default): use the OpenSSH key format,
  rather than PEM.
- `-a` (default is 16): number of rounds of passphrase derivation;
  increase to slow down brute force attacks.
- `-t` (default is [rsa](https://en.wikipedia.org/wiki/RSA_(cryptosystem))):
  specify the "type" or cryptographic algorithm. 
  [ed25519](https://en.wikipedia.org/wiki/EdDSA)
 is faster and shorter than RSA for comparable strength.
- `-f` (default is /home/user/.ssh/id_algorithm): filename to store your keys.
  If you already have SSH keys, make sure you specify a different name:
  `ssh-keygen` will overwrite the default key if you don't specify!

If ed25519 is not available, use the older (but strong and trusted)
[RSA](https://en.wikipedia.org/wiki/RSA_(cryptosystem)) cryptography:

```
$ ls ~/.ssh/
$ ssh-keygen -o -a 100 -t rsa -b 4096 -f ~/.ssh/id_{{ site.workshop_host }}_rsa
```
{: .language-bash}
 
The flag `-b` sets the number of bits in the key.
The default is 2048. EdDSA uses a fixed key length,
so this flag would have no effect.

When prompted, enter a strong password that you will remember. 
Cryptography is only as good as the weakest link, and this will be 
used to connect to a powerful, precious, computational resource.

Take a look in `~/.ssh` (use `ls ~/.ssh`). You should see the two 
new files: your private key (`~/.ssh/key_{{ site.workshop_host }}_ed25519` 
or `~/.ssh/key_{{ site.workshop_host }}_rsa`) and 
the public key (`~/.ssh/key_{{ site.workshop_host }}_ed25519.pub` or
`~/.ssh/key_{{ site.workshop_host }}_rsa.pub`). If a key is 
requested by the system administrators, the *public* key is the one
to provide.

> ##### Private keys are your private identity
>
> A private key that is visible to anyone but you should be considered compromised,
> and must be destroyed. This includes having improper permissions on the directory
> it (or a copy) is stored in, traversing any network in the clear, attachment on 
> unencrypted email, and even displaying the key (which is ASCII text) in your 
> terminal window.
>
> Protect this key as if it unlocks your front door. In many ways, it does.
{: .caution}

> #### Further information
> 
> For more information on SSH security and some of the
> flags set here, an excellent resource is 
> [Secure Secure Shell](https://stribika.github.io/2015/01/04/secure-secure-shell.html).
{: .callout}

## Logging onto the system

With all of this in mind, let's connect to a remote HPC system. In this
workshop, we will connect to {{ site.workshop_host }} &mdash; an HPC system
located at the {{ site.workshop_host_location }}. Although it's unlikely that
every system will be exactly like {{ site.workshop_host }}, it's a very good
example of what you can expect from an HPC installation. To connect to our
example computer, we will use SSH (if you are using PuTTY, see above).

SSH allows us to connect to UNIX computers remotely, and use them as if they
were our own. The general syntax of the connection command follows the format
`ssh -i ~/.ssh/key_for_remote_computer <NetID>@greene.hpc.nyu.edu` 
when using SSH keys and `ssh yourUsername@some.computer.address` if only
password access is available.  Let's attempt to connect to the HPC system
now:

```
ssh -i ~/.ssh/key_{{ site.workshop_host }}_ed25519 yourUsername@{{ site.workshop_host_login }}
```
{: .language-bash}

or

```
ssh -i ~/.ssh/key_{{ site.workshop_host }}_rsa yourUsername@{{ site.workshop_host_login }}
```
{: .language-bash}

or if SSH keys have not been enabled 

```
ssh yourUsername@{{ site.workshop_host_login }}
```
{: .language-bash}


```
{% include /snippets/01/login_output.{{ site.workshop_host_id }} %}
```
{: .output}

If you've connected successfully, you should see a prompt like the one below.
This prompt is informative, and lets you grasp certain information at a glance.
(If you don't understand what these things are, don't worry! We will cover
things in depth as we explore the system further.)

```
{{ site.workshop_host_prompt }}
```
{: .output}

## Telling the Difference between the Local Terminal and the Remote Terminal

You may have noticed that the prompt changed when you logged into the remote
system using the terminal (if you logged in using PuTTY this will not apply
because it does not offer a local terminal). This change is important because
it makes it clear on which system the commands you type will be run when you
pass them into the terminal. This change is also a small complication that we
will need to navigate throughout the workshop. Exactly what is reported before
the `$` in the terminal when it is connected to the local system and the remote
system will typically be different for every user. We still need to indicate
which system we are entering commands on though so we will adopt the following
convention:

- `[local]$` when the command is to be entered on a terminal connected to your
  local computer
- `{{ site.workshop_host_prompt }}` when the command is to be entered on a
  terminal connected to the remote system
- `$` when it really doesn't matter which system the terminal is connected to.

> ## Being certain which system your terminal is connected to
>
> If you ever need to be certain which system a terminal you are using is
> connected to then use the following command: `$ hostname`.
{: .callout}

> ## Keep two terminal windows open
>
> It is strongly recommended that you have two terminals open, one connected to
> the local system and one connected to the remote system, that you can switch
> back and forth between. If you only use one terminal window then you will
> need to reconnect to the remote system using one of the methods above when
> you see a change from `[local]$` to `{{ site.workshop_host_prompt }}` and
> disconnect when you see the reverse.
{: .callout}

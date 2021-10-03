# T2 Mojave Ubuntu Kernel

Ubuntu/Mint/Debian kernel with Apple T2 patches built-in. This repo will try to keep up with kernel new releases.

![Build Kernel Package](https://github.com/AdityaGarg8/T2-Mojave-Ubuntu-Kernel/actions/workflows/build.yml/badge.svg)

This project is closely inspired by mikeeq/mbp-fedora-kernel and marcosfad/mbp-ubuntu-kernel. Thank you @mikeeq and @marcosfad for the scripts and setup.

Special thanks to @Redecorating who edited the scripts for Mojave firmware and also provided the CI.

**If this repo helped you in any way, consider inviting a coffee to the people in the [credits](https://github.com/AdityaGarg8/T2-Mojave-Ubuntu-Kernel#credits).**

## Pre installation steps

In case you have used an iso with kernel version **5.8.x or lower**, then follow the [DKMS Guide](http://wiki.t2linux.org/guides/dkms/) to uninstall old drivers and get new drivers for the kernels. It is required only once and must be done before installing a kernel from here.

## INSTALLATION

### The easy way

Download the .deb packages of **linux-headers** and **linux-image** of the kernel you wish to install from the [releases](https://github.com/AdityaGarg8/T2-Mojave-Ubuntu-Kernel/releases) section.

Install **linux-headers** first and then **linux-image** using `apt` and restart your Mac. In case you do not know how to do so, follow the instructions given below. Else you are good to go.

On terminal, type `sudo apt install ` and then drag and drop the **linux-headers** file to the terminal and press enter/return key.

Do the similar process for **linux-images** package.

Restart your Mac.

### Building yourself

Clone the repo using
```bash
git clone https://github.com/AdityaGarg8/T2-Mojave-Ubuntu-Kernel
```
Open [this repo](https://github.com/AdityaGarg8/mojave-patches) in your browser.

Check out the kernel version it is offering right now.

Now edit **build.sh** file in **T2-Mojave-Ubuntu-Kernel** folder of your home directory. Replace the kernel version given in `KERNEL_VERSION` by the one on the above repo.

Now edit **patch_driver.sh** file in the same folder. Replace the commit hash in `APPLE_SMC_DRIVER_COMMIT_HASH` with the latest one in the above repo. It can be found by click on the shortened hash or time elapsed since last update on the right of "AdityaGarg8".

Now open a terminal window and run

```bash
cd T2-Mojave-Ubuntu-Kernel
sudo ./build.sh
```

The kernel shall take around an hour to compile. After that you shall find three .deb packages in `/root/work`.

Install the **linux-headers** package first using `apt`. In case you do not know how to do so, follow the instructions described in the above **The easy way** section. Similarly install the **linux-image** package too.

Restart your Mac.

You may then delete the `/root/work` directory using `sudo rm -r /root/work` to free up space.

## Docs

- Discord: <https://discord.gg/Uw56rqW>
- WiFi firmware:
  - <https://wiki.t2linux.org/guides/wifi/>
  - <https://packages.aunali1.com/apple/wifi-fw/18G2022/>
- blog `Installing Fedora 31 on a 2018 Mac mini`: <https://linuxwit.ch/blog/2020/01/installing-fedora-on-mac-mini/>
- iwd:
  - <https://iwd.wiki.kernel.org/networkconfigurationsettings>
  - <https://wiki.archlinux.org/index.php/Iwd>
  - <https://www.vocal.com/secure-communication/eap-types/>

### Ubuntu

- <https://wiki.ubuntu.com/KernelTeam/GitKernelBuild>
- <https://help.ubuntu.com/community/Repositories/Personal>
- <https://medium.com/sqooba/create-your-own-custom-and-authenticated-apt-repository-1e4a4cf0b864>
- <https://help.ubuntu.com/community/Kernel/Compile>
- <https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel>
- <https://www.linux.com/training-tutorials/kernel-newbie-corner-building-and-running-new-kernel/>
- <https://wiki.ubuntu.com/KernelTeam/KernelMaintenance>

## Credits

- @Redecorating - thanks for editing the scripts and CI for Ubuntu
- @marcosfad - thanks for the original script for Ubuntu
- @MCMrARM - thanks for all RE work
- @ozbenh - thanks for submitting NVME patch
- @roadrunner2 - thanks for SPI (touchbar) driver
- @aunali1 - thanks for ArchLinux Kernel CI and active support
- @jamlam - thanks for providing the Correlium wifi patch
- @ppaulweber - thanks for keyboard and Macbook Air patches
- @mikeeq - thanks for the fedora kernel project and compilation scripts

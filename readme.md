This is an experiment to see if the yocto meta layer [meta-st-stm32mp](https://github.com/STMicroelectronics/meta-st-stm32mp), can be used without the [meta-st-openstlinux](https://github.com/STMicroelectronics/meta-st-openstlinux) disto. 

Instead can we use the [poky](https://github.com/yoctoproject/poky) reference distro provided by Yocto?

Well it certainly builds....but will it boot?

### Environment

Designed be run in a container. See [devcontainer.json](.devcontainer/devcontainer.json)
If you don't have access to the container you can build it by first cloning the [embedded_linux_dockerfiles](https://github.com/cracked-machine/embedded_linux_dockerfiles) repoistory.

### Build

Use the task.json or run the following command line

```
"cd layers/poky",
"&& TEMPLATECONF=/workspaces/stm32_poky/layers/meta-test/conf/templates/stm32mp157f_dk2",
"source oe-init-build-env ../../workdir",
"&& time bitbake core-image-minimal
```

### Create raw file for SD Card 

```
sudo workdir/tmp/deploy/images/stm32mp15-disco/scripts/create_sdcard_from_flashlayout.sh workdir/tmp/deploy/images/stm32mp15-disco/flashlayout_core-image-minimal/deleteall/FlashLayout_disco_stm32mp157f-dk2-deleteall.tsv
```
Google's Android Kernel Build System
======================

Current Device: Sunfish - Pixel 4a

Current Branch: android-12.1

This is based on google branches and source code with my own modifications.


In Order To Build
====================
To initialize your local repository , use a command like this:

    mkdir -p android-kernel $$ cd android-kernel

    repo init -u https://github.com/tnakamur/android_manifest_google_sunfish-kernel.git -b android-12.1

Then to sync up:

    repo sync -c -j8 --force-sync --no-clone-bundle --no-tags

Build commands are:

    build/build.sh

Output Files:

    out/android-msm-sunfish-4.14/dist/dtbo.img

    out/android-msm-sunfish-4.14/dist/Image.lz4-dtb

    out/android-msm-sunfish-4.14/dist/sdmmagpie.dtb


Things To Note
======================
Current defconfig: 

    arch/arm64/configs/sunfish_defconfig

However, if you alter this file, this build system will complain. 
So we need to alter it on the fly.
This is done by a symlinked file from the kernel source located at private/msm-google/
So..

**Actual defconfig**: 

    build.config.no-cfi

This functionality may be changed later.

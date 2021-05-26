Google's Android Kernel Build System
======================

Current Device: Sunfish - Pixel 4a

Current Branch: android-11

This is based on google branches and source code with my own modifications.


In Order To Build
====================
To initialize your local repository , use a command like this:

    mkdir -p android-kernel $$ cd android-kernel

    repo init --depth=1 -u https://github.com/tnakamur/android_manifest_google_sunfish-kernel.git -b android-11

Then to sync up:

    repo sync --no-repo-verify -c --force-sync --no-clone-bundle --no-tags --optimized-fetch --prune -j`nproc`

Build commands are:

    build_sunfish.sh

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

    build.config.sunfish_no-cfi

This functionality may be changed later.

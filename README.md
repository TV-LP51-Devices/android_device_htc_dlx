To build Validus for DNA run these commands:

mkdir android/TV && cd android/TV && repo init - u git://github.com/TV-LP51/android.git -b lp5.1 && repo sync -j5

Personally I like to rerun repo sync after an initial sync because it takes so long but that's up to you.

Now for the fun part....building!!

. build/envsetup.sh && lunch
(enter device number)
time mka validus

If you want to speed up your build times in your .bashrc add these lines to the bottom:

export CCACHE_DIR=$HOME/.ccache
export USE_CCACHE=1
export USE_PREBUILT_CHROMIUM=1

alias git-pl="git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

if [ ! -d "$CCACHE_DIR" ]; then
    $HOME/android/TV/prebuilts/misc/linux-x86/ccache/ccache -M 50G
fi

In case if you didn't know, -J# is an argument for running parallel jobs where # should be your number of cores+1. Since I have 4 cores I use -j5.

When all is said and done you should have a kickass ROM ready to flash!

Device configuration for HTC Droid DNA
=====================================

Basic   | Spec Sheet
-------:|:-------------------------
CPU     | Quad-core 1.5 GHz Krait 300
CHIPSET | Qualcomm MDM615m/APQ8064
GPU     | Adreno 320
Memory  | 2GB RAM
Shipped Android Version | 4.4.2
Storage | 16GB
Battery | 2020 mAh
Dimensions | 141 x 70.5 x 9.7 mm
Display | 1080 x 1920 pixels, Super LCD3
Camera  | 8 MP, 3264 x 2448 pixels
Release Date | November 2012


![Droid DNA](http://wiki.cyanogenmod.org/images/thumb/7/7e/Dlx.png/314px-Dlx.png "Droid DNA")

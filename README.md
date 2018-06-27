# 要如何为Samsung S4编译Mokee呢？（Chinese Version）
# 1.首先，我们需要初始的Mokee源代码。
- 在终端中输入以下代码
- repo init -u https://github.com/MoKee/android.git -b mkn-mr1
- 耐心等待代码下载完成。
- 接着：repo sync -j20 --force-sync
- 如果你网速较快，这最多将会花费你3-5个小时.

# 2.下载设备必需文件。
由于魔趣不太支持local_manifest.xml，所以我并不推荐使用它，但如果你需要，我仍然提供local_manifest.xml。
我们需要：
- omnirom/android_bootable_recovery ==> bootable/recovery-twrp
- android_external_busybox ==> external/busybox
- android_external_stlport ==> external/stlport
- android_packages_apps_SamsungServiceMode ==> packages/apps/SamsungServiceMode
- android_hardware_samsung ==> hardware/samsung
- android_device_samsung_exynos5410-common ==> device/samsung/exynos5410-common
- android_device_samsung_ja3gxx ==> device/samsung/ja3gxx
- android_device_samsung_ja3gchnduos ==> device/samsung/ja3gchnduos
- android_device_samsung_ja3gduosctc ==> device/samsung/ja3gduosctc
- android_device_samsung_jalteskt ==> device/samsung/jalteskt
- android_device_samsung_jaltelgt ==> device/samsung/jaltelgt
- android_kernel_samsung_exynos5410 ==> kernel/samsung/exynos5410
- proprietary_vendor_samsung ==> vendor/samsung
- android_hardware_samsung_slsi-cm_exynos ==> hardware/samsung_slsi-cm/exynos
- android_hardware_samsung_slsi-cm_exynos5 ==> hardware/samsung_slsi-cm/exynos5
- android_hardware_samsung_slsi-cm_exynos5410 ==> hardware/samsung_slsi-cm/exynos5410
- android_hardware_samsung_slsi-cm_openmax ==> hardware/samsung_slsi-cm/openmax
- 以上是我们需要的全部文件，建议找到这些源时候使用git clone指令将其调整到"==>"后的路径，注意，下载到的文件夹要改名为相应的名称！如android_hardware_samsung_slsi-cm_openmax要改为openmax。
- 再次提醒，我非常不建议使用local_manifest!!!!!!!
- 以上的文件基本能在我的源码库里找到，若找不到，请搜索Mokee的Github库，地址：https://github.com/MoKee/android

# 3.如果文件处理好了，我们需要打补丁。
- 第一步，给recovery打补丁
- $cd bootable/recovery-twrp
- $git fetch https://gerrit.omnirom.org/android_bootable_recovery refs/changes/96/22096/11 && git cherry-pick FETCH_HEAD
- cd ../..
- 注意，不要把$输入终端！
- 一定要用omni的recovery！否则容易出错！
- 第二步，给framework打补丁
- $cd frameworks/base
- $git am ../../device/samsung/exynos5410-common/patches/frameworks_base/0001-DO-NOT-MERGE-PATCH-Zygote-Stop-breaking-the-entire-s.patch
- $git fetch https://github.com/LineageOS/android_frameworks_base refs/changes/45/169945/2 && git cherry-pick FETCH_HEAD
- $cd ../..

- 以上我们打完全部的补丁。Mokee的源码已经做出了修复，所以不需要再如Lineage OS一样打其他的补丁了。

# 4.编译
- 输入$export WITH_TWRP=true
- 然后$. build/envsetup.sh
- 最后$brunch mk_ja3gxx-userdebug 此处仅针对ja3gxx机型，如果你要编译其他机型，你需要将ja3gxx改为相应的代号。
- 如果你顺利的话，1个半小时左右就会编译完成。
# 祝你好运 ！

# Build Guide (English Version)

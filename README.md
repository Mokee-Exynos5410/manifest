# Ҫ���ΪSamsung S4����Mokee�أ���Chinese Version��
#1.���ȣ�������Ҫ��ʼ��MokeeԴ���롣
���ն����������´���
repo init -u https://github.com/MoKee/android.git -b mkn-mr1
���ĵȴ�����������ɡ�
���ţ�repo sync -j20 --force-sync
��������ٽϿ죬����ཫ�Ứ����3-5��Сʱ.

#2.�����豸�����ļ���
����ħȤ��̫֧��local_manifest.xml�������Ҳ����Ƽ�ʹ���������������Ҫ������Ȼ�ṩlocal_manifest.xml��
������Ҫ��
omnirom/android_bootable_recovery ==> bootable/recovery-twrp
android_external_busybox ==> external/busybox
android_external_stlport ==> external/stlport
android_packages_apps_SamsungServiceMode ==> packages/apps/SamsungServiceMode
android_hardware_samsung ==> hardware/samsung
android_device_samsung_exynos5410-common ==> device/samsung/exynos5410-common
android_device_samsung_ja3gxx ==> device/samsung/ja3gxx
android_device_samsung_ja3gchnduos ==> device/samsung/ja3gchnduos
android_device_samsung_ja3gduosctc ==> device/samsung/ja3gduosctc
android_device_samsung_jalteskt ==> device/samsung/jalteskt
android_device_samsung_jaltelgt ==> device/samsung/jaltelgt
android_kernel_samsung_exynos5410 ==> 
kernel/samsung/exynos5410
proprietary_vendor_samsung ==> vendor/samsung
android_hardware_samsung_slsi-cm_exynos ==> hardware/samsung_slsi-cm/exynos
android_hardware_samsung_slsi-cm_exynos5 ==> hardware/samsung_slsi-cm/exynos5
android_hardware_samsung_slsi-cm_exynos5410 ==> hardware/samsung_slsi-cm/exynos5410
android_hardware_samsung_slsi-cm_openmax ==> hardware/samsung_slsi-cm/openmax
������������Ҫ��ȫ���ļ��������ҵ���ЩԴʱ��ʹ��git cloneָ��������"==>"���·����ע�⣬���ص����ļ���Ҫ����Ϊ��Ӧ�����ƣ���android_hardware_samsung_slsi-cm_openmaxҪ��Ϊopenmax��
�ٴ����ѣ��ҷǳ�������ʹ��local_manifest!!!!!!!
���ϵ��ļ����������ҵ�Դ������ҵ������Ҳ�����������Mokee��Github�⣬��ַ��https://github.com/MoKee/android

#3.����ļ�������ˣ�������Ҫ�򲹶���
��һ������recovery�򲹶�
$cd bootable/recovery-twrp
$git fetch https://gerrit.omnirom.org/android_bootable_recovery refs/changes/96/22096/11 && git cherry-pick FETCH_HEAD
cd ../..
ע�⣬��Ҫ��$�����նˣ�
һ��Ҫ��omni��recovery���������׳���
�ڶ�������framework�򲹶�
$cd frameworks/base
$git am ../../device/samsung/exynos5410-common/patches/frameworks_base/0001-DO-NOT-MERGE-PATCH-Zygote-Stop-breaking-the-entire-s.patch
$git fetch https://github.com/LineageOS/android_frameworks_base refs/changes/45/169945/2 && git cherry-pick FETCH_HEAD
$cd ../..

�������Ǵ���ȫ���Ĳ�����Mokee��Դ���Ѿ��������޸������Բ���Ҫ����Lineage OSһ���������Ĳ����ˡ�

#4.����
����$export WITH_TWRP=true
Ȼ��$. build/envsetup.sh
���$brunch mk_ja3gxx-userdebug �˴������ja3gxx���ͣ������Ҫ�����������ͣ�����Ҫ��ja3gxx��Ϊ��Ӧ�Ĵ��š�
�����˳���Ļ���1����Сʱ���Ҿͻ������ɡ�
#ף����ˣ�

#Build Guide (English Version)
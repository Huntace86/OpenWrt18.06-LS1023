׼�������ο�openwrt��README

����config�ļ���openwrt���ں˵������ļ���linux.config��openwrt.config���ֱ���make menuconfig ��make kernel_menuconfigʱʹ�á�

20181207�Ķ���
1. ��itb��openwrt�ļ�ϵͳ�����ʱ��϶�Ϊһ�����������д��

2. ��������sysupgrade������ڽ������õı��ݺͻ�ԭ��

3. ��������reset�������ܺ�sys_update���ܣ����ڻָ�ϵͳ������ϵͳ���ܡ�

4. ramdiskģʽ��ϵͳ�ĳ��˾�����openwrt,֧��ssh�����ڽ��������ϵͳ�ָ���ramdisk���µĻָ�Ϊ��
��1��uboot�����ã�
	setenv bootargs "console=ttyS0,115200 root=/dev/ram0 earlycon=uart8250,mmio,0x21c0500"
	setenv bootcmd "run distro_bootcmd; run sd_bootcmd; env exists secureboot && esbc_halt"
	boot
��2����/dev/mmcblk0p3��������ϵͳ���񣬲��������ļ�touch recover
��3��������ϵͳ���Զ����л�ԭ

5. �Ľ���firmware,λ��itb/firmwareĿ¼������˶����������ĵײ�֧��

6. ���¶Ը���������ʹ֮��Ӧ����ţ���iface0~iface4

һ��openwrt��Ŀ¼ִ����make V=s -j1��������bin/targets/layerscape/armv8_64b-glibc��������
openwrt-layerscape-armv8_64b-ls1043ardb-squashfs-sysupgrade.bin,Ҳ�����ں˺��ļ�ϵͳ�Ĵ��
��������
�¸Ķ����������ܷ����֣�һ���ǻ�ԭ�����������浱ǰ���ã���һ����ֱ�����������浱ǰ���ã�

��1���������ļ��ŵ�/dev/mmcblk0p3����������reset��5s���ϣ�ϵͳ������������������/dev/mmcblk0p3�����ľ���
�ָ���sys����Ҳ����/dev/mmcblk0p1�С�

��2���������ļ�openwrt-layerscape-armv8_64b-ls1043ardb-squashfs-sysupgrade.bin�ŵ��豸�У�Ȼ��ִ��sysupgrade openwrt-layerscape-armv8_64b-ls1043ardb-squashfs-sysupgrade.bin,
ϵͳ�����������

�������ñ����뻹ԭ(��δʵ��)
��1��ʹ��sysupgrade -b xxxx.tar.gz�������õı���
��2��ʹ��sysupgrade -r xxxx.tar.gz�������õĻ�ԭ

�ġ�˵��
��һ�θ������µ�firmware֮�����ִ�е�4���е�ramdisk�������ϵͳ�ָ�����Ϊ�п���ϵͳ������ʱû��ϵͳ��
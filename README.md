包含文件及说明：
    1、awboot
        包含awboot和script，dtb（包含重要的bootargs），已编译的二进制文件可以直接运行，烧录脚本在script里。如果想继续优化，源代码已部分误删，最好对照awboot官方文件，以及本hub中另一个仓库的awboot（并非最新版本）进行对照补充。
        主要是烧录位置一定要对，参考script。
    2、kernel
        文件夹包括内核，有hello驱动（simple_demo）以供调试，用的时候注意initramfs的路径要写成文件系统的_install/文件夹。
    3、initramfs
        包括基础busybox生成的文件，以及测试用的init_S6用户小程序。
总project说明：
    可以从bootloader一直启动到rootfs，但是rootfs不能直接输出字符到串口，只能给/dev/simple_demo发送一个代表字符地址的int数字来传递信息，调试网络以及开机脚本、待运行计算程序后仍可以完成任务。
备注：注意以上运行的awboot和kernel的编译软件及版本

文件过大，已保存在百度云盘以及睿客云。

链接：https://pan.baidu.com/s/1dFABwAFDPqFfPruq_O4Emg 
提取码：3ra7

链接：https://rec.ustc.edu.cn/share/b1248bc0-cc04-11ef-8950-495341a55c2d

25.2.13更新：
已成功进入系统，采用linux-6.0，D1s版本进行修改，之前的有问题是因为linux主线没有提供对clock-controller的支持，导致作为consumer的8250_dw驱动无法probe。
调试中出现的问题有，找不到挂载系统（error -2）是因为bootargs中应该使用rdinit而不是init；
内核没有打印是因为设备树中chosen对串口表示的不准确，以现行的dts为准。
有帮助的网址：https://whycan.com/t_9293.html

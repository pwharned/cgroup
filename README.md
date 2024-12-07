# cgroup


GRUB_CMDLINE_LINUX="rd.luks.uuid=luks-55444687-fec8-44eb-9f78-1d7144bc340e rd.lvm.lv=vg_li1608120349/lv_swap rd.lvm.lv=vg_li1608120349/lv_root  vconsole.keymap=us vconsole.font=latarcyrheb-sun32 rhgb quiet loglevel=0 systemd.show_status=0 rd.systemd.show_status=false rd.udev.log_priority=3 rd.driver.blacklist=nouveau modprobe.blacklist=nouveau nvidia-drm.modeset=1 systemd.unified_cgroup_hierarchy=1"

 sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```
[Unit]
Description=Limit CPU usage for Chrome

[Service]
ExecStart=/bin/bash -c 'for pid in $(pgrep chrome|BESClient); do echo $pid > /sys/fs/cgroup/cpu_limit/cgroup.procs; done; '
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

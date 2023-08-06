# 问题：蓝灯无法自动管理系统代理<!-- omit in toc -->

- [1. 问题](#1-问题)
- [2. 方案](#2-方案)
- [3. 实施](#3-实施)

## 1. 问题

蓝灯启动后提示无法自动管理系统代理，需要手动在系统代理设置界面中添加蓝灯的代理服务器信息。

开启蓝灯时，需要手动在系统代理设置界面开启代理，关闭蓝灯后也需要手动将其关闭，否则网络无法使用。由于经常需要切换代理，操作很繁琐。

## 2. 方案

编写 Shell 脚本自动切换系统代理状态，并添加快捷方式图标到底部 Dock 工具栏。

## 3. 实施

1. 启动蓝灯并在系统代理设置界面中添加蓝灯的代理服务器信息（仅操作一次）。

2. 创建脚本文件 `/home/itabbot/proxy-toggle.sh`：

```shell
#!/bin/bash

# 获取当前代理模式
current_mode=$(gsettings get org.gnome.system.proxy mode)
# 快捷方式配置文件路径
desktop_file="/home/itabbot/.local/share/applications/proxy-toggle.desktop"

# 如果未开启代理
if [[ "$current_mode" == *"none"* ]]; then
    # 更新图标
    sed -i "s/^Icon=.*/Icon=network-vpn/" "$desktop_file"
    # 如果没有启动lantern则启动
    if ! pgrep "lantern" > /dev/null; then
        nohup lantern &
    fi
    # 启动系统代理
    gsettings set org.gnome.system.proxy mode 'manual'

# 如果已经开启代理
else
    # 更新图标
    sed -i "s/^Icon=.*/Icon=network-vpn-disabled/" "$desktop_file"
    # 关闭系统代理
    gsettings set org.gnome.system.proxy mode 'none'
fi
```

3. 创建快捷方式配置文件 `/home/itabbot/.local/share/applications/proxy-toggle.desktop`：

```
[Desktop Entry]
Name=ProxyToggle
Exec=gnome-terminal -e "/home/itabbot/proxy-toggle.sh"
Terminal=true
Type=Application
Icon=network-vpn
```

4. 设置脚本文件为可执行权限

```shell
chmod +x proxy-toggle.sh
```

5. 设置执行脚本时不用验证密码，执行 `sudo visudo` 并添加：

```
itabbot ALL=(ALL) NOPASSWD: /home/itabbot/proxy-toggle.sh
```

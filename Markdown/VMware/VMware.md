# Vmware虚拟机设置固定IP地

<br>

### 一、设置虚拟机`ip`地址

- 打开编辑→虚拟网络编辑器

![](https://github.com/Dashan-IZ/DS_Installation/raw/master/Images/VMware-Images/2021-09-19_131631.png)

![](https://github.com/Dashan-IZ/DS_Installation/raw/master/Images/VMware-Images/2021-09-19_132502.png)

- 选择`NAT`设置，设置网关

![](https://github.com/Dashan-IZ/DS_Installation/raw/master/Images/VMware-Images/2021-09-19_134023.png)

<br>

<br>

### 二、虚拟机配置静态`IP`

- 然后打开虚拟机，我这里以`CentOS Linux`系统为例

  - 进入`ifcfg-ens33`

  - ```shell
    vim /etc/sysconfig/network-scripts/ifcfg-ens33
    ```

  - ```shell
    TYPE=Ethernet
    PROXY_METHOD=none
    BROWSER_ONLY=no
    # 改为static
    BOOTPROTO=static
    DEFROUTE=yes
    IPV4_FAILURE_FATAL=no
    IPV6INIT=yes
    IPV6_AUTOCONF=yes
    IPV6_DEFROUTE=yes
    IPV6_FAILURE_FATAL=no
    NAME=ens33
    UUID=5252409b-c2c1-456a-a5b8-5c3db6507fcd
    DEVICE=ens33
    # 改为yes
    ONBOOT=yes
    
    # 子网ip
    IPADDR=192.168.152.37
    # 子网掩码
    NETMASK=255.255.255.0
    # 网关ip
    GATEWAY=192.168.152.2
    ```

- 改完后`:wq`保存配置

- 重启网卡

  - ```shell
    service network restart
    ```

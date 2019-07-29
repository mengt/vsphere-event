## vsphere-monitor
vsphere-event 通过 [pyvmomi](https://github.com/vmware/pyvmomi) 采集 vsphere 集群的数据。只需要连接 vcenter 就可以采集集群内的包括 ESXi，datastore，vm 等各种告警和事件。

#### 版本需求
python 2.7

#### 安装
获取代码
```
git clone https://github.com/mengt/vsphere-event.git
```
安装依赖
```
yum install -y python-virtualenv
cd vsphere-event
virtualenv ./env
./env/bin/pip install -r requirement.txt
```
#### 配置
修改配置文件 `config.py`
```
# interval
interval = 60 # 上报的 step 间隔

# vcenter
host = "vcenter.host" # vcenter 的地址
user = "administrator@vsphere.local" # vcenter 的用户名
pwd = "password" # vcenter 的密码
port = 443 # vcenter 的端口

```

#### 运行
先尝试跑一下，假定 `vsphere-event` 放在 `/opt` 下
```
/opt/vsphere-event/env/bin/python /opt/vsphere-event/vsphere-event.py
```
没有问题的话，将他放入定时任务
```
crontab -e
0-59/1 * * * * /opt/vsphere-event/env/bin/python /opt/vsphere-event/vsphere-monitor.py
```

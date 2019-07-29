## vsphere-event
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
#### 参考
https://vdc-download.vmware.com/vmwb-repository/dcr-public/6b586ed2-655c-49d9-9029-bc416323cb22/fa0b429a-a695-4c11-b7d2-2cbc284049dc/doc/index.html#link192a96c026a5b7ba4ab38a5354358d4e73b03e93;index-mo_types.html

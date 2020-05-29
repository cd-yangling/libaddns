# addns
阿里 DDNS Shell Scripts

## 介绍

阿里云的域名解析服务官方不提供基于 shell 版本。为了方便一些嵌入式设备或者软路由使用，我就自己编写了一个 shell 版本的 SDK. 如果您使用的是腾讯云的 DDNS 请 [点击这里](https://github.com/cd-yangling/libtddns)

已知问题: 参数名称不能携带 `.` 字符。 这是 shell 不被允许的。目前有一个解决方案，但是我还没有实施它。至少 DDNS 接口中不会存在这样的情况。如果您有兴趣你可以参考 [这里](https://stackoverflow.com/questions/9761973/using-variable-as-a-key-in-an-bash-associative-array) 来修复参数名称携带 `.` 的问题。

注意事项: 该脚本仅仅实现了 [获取解析记录列表](https://help.aliyun.com/document_detail/29776.html?spm=a2c4g.11186623.6.657.1f231cebPnJVoC) 和 [修改解析记录](https://help.aliyun.com/document_detail/29774.html?spm=a2c4g.11174283.6.662.5634571fizOAI0) 和 [添加解析记录](https://help.aliyun.com/document_detail/29772.html?spm=a2c4g.11186623.6.660.36d55eb44s6y1q) 和 [删除解析记录](https://help.aliyun.com/document_detail/29773.html?spm=a2c4g.11186623.6.661.673d2846plNtSS) 和 [获取解析记录信息](https://help.aliyun.com/document_detail/29777.html?spm=a2c4g.11186623.6.658.27de3b59ARRwR5) 和 [设置解析记录状态](https://help.aliyun.com/document_detail/29775.html?spm=a2c4g.11186623.6.664.6681606bwqwnpy)

参考文档: [阿里云解析文档](https://help.aliyun.com/product/29697.html?spm=a2c4g.750001.list.95.146d7b13ebZD2k)

## 使用方法

### 获取解析记录列表

```sh
source "$(dirname $0)/libfnaddns"
export AccessKeySecret=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
export AccessKeyId=yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy
curl -sS $(DescribeDomainRecords example.com)
```

### 修改解析记录

```sh
source "$(dirname $0)/libfnaddns"
export AccessKeySecret=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
export AccessKeyId=yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy
curl -sS $(UpdateDomainRecord www id A 202.106.0.20)
```

### 添加解析记录

```sh
source "$(dirname $0)/libfnaddns"
export AccessKeySecret=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
export AccessKeyId=yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy
curl -sS $(AddDomainRecord example.com www A 202.106.0.20)
```

### 删除解析记录

```sh
source "$(dirname $0)/libfnaddns"
export AccessKeySecret=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
export AccessKeyId=yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy
curl -sS $(DeleteDomainRecord id)
```

### 获取解析记录信息

```sh
source "$(dirname $0)/libfnaddns"
export AccessKeySecret=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
export AccessKeyId=yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy
curl -sS $(DescribeDomainRecordInfo id)
```

### 设置解析记录状态

```sh
source "$(dirname $0)/libfnaddns"
export AccessKeySecret=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
export AccessKeyId=yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy
curl -sS $(SetDomainRecordStatus id Enable/Disable)
```


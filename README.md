# addns
阿里 DDNS Shell Scripts

## 介绍

阿里云的域名解析服务官方不提供基于 shell 版本。为了方便一些嵌入式设备或者软路由使用，我就自己编写了一个 shell 版本的 SDK

已知问题: 参数名称不能携带 `.` 字符。 这是 shell 不被允许的。目前有一个解决方案，但是我还没有实施它。至少 DDNS 接口中不会存在这样的情况。如果您有兴趣你可以参考 [这里](https://stackoverflow.com/questions/9761973/using-variable-as-a-key-in-an-bash-associative-array) 来修复参数名称携带 `.` 的问题。

注意事项: 该脚本仅仅实现了 [获取解析记录列表](https://help.aliyun.com/document_detail/29776.html?spm=a2c4g.11186623.6.657.1f231cebPnJVoC) 和 [修改解析记录](https://help.aliyun.com/document_detail/29774.html?spm=a2c4g.11174283.6.662.5634571fizOAI0)

参考文档: [阿里云解析文档](https://help.aliyun.com/product/29697.html?spm=a2c4g.750001.list.95.146d7b13ebZD2k)

## 使用方法

### 获取解析记录列表

```sh
source "$(dirname $0)/libfntddns"
export AccessKeySecret=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
export AccessKeyId=yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy
curl -sS $(DescribeDomainRecords example.com)
```

### 修改解析记录

```sh
source "$(dirname $0)/libfntddns"
export AccessKeySecret=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
export AccessKeyId=yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy
curl -sS $(UpdateDomainRecord www id A 202.106.0.20)
```

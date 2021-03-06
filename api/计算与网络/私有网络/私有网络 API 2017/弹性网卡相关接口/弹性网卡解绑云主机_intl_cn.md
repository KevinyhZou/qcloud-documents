## 1. 接口描述

本接口(DetachNetworkInterface)用于弹性网卡解绑云主机。
接口请求域名：<font style="color:red">vpc.api.qcloud.com</font>

1) 将弹性网卡和云主机解绑。
2) 解绑之后弹性网卡上的所有弹性公网 IP 处于未关联状态，所有未关联状态的弹性公网 IP 将收取费用，具体收费标准详见<a href="https://cloud.tencent.com/doc/product/213/1941#6.-.E5.BC.B9.E6.80.A7.E5.85.AC.E7.BD.91ip.E7.9A.84.E8.AE.A1.E8.B4.B9" title="弹性公网IP的计费">弹性公网IP的计费</a>。
3) 只有运行中或者已关机状态的云主机才能绑定弹性网卡，查看云主机状态详见<a href="https://cloud.tencent.com/doc/api/229/831" title="查看腾讯云主机信息">查看腾讯云主机信息</a>

## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href="/doc/api/245/4772" title="公共请求参数">公共请求参数</a>页面。其中，此接口的Action字段为DetachNetworkInterface。

| 参数名称 | 必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 是 | String | 弹性网卡对应的私用网络ID，例如：vpc-7t9nf3pu |
| networkInterfaceId | 是 | String | 弹性网卡ID，例如：eni-m6dyj72l |
| instanceId | 是 | String  | 云主机实例ID，例如：ins-xx44545f |


## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 错误码。0：成功，其他值：失败|
| message | String | 错误信息|
| taskId | Int | 任务ID，操作结果可以用taskId查询，详见<a href="https://cloud.tencent.com/doc/api/245/%e6%9f%a5%e8%af%a2%e4%bb%bb%e5%8a%a1%e6%89%a7%e8%a1%8c%e7%bb%93%e6%9e%9c%e6%8e%a5%e5%8f%a3">查询任务执行结果接口</a>。 |

## 4. 错误码表
以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码详见<a href="https://cloud.tencent.com/doc/api/245/4924" title="VPC错误码">VPC错误码</a>。

| 错误码 | 描述 |
|---------|---------|
| InvalidVpc.NotFound | 无效的VPC，VPC资源不存在。请再次核实您输入的资源信息是否正确，可通过<a href="http://cloud.tencent.com/doc/api/245/%E6%9F%A5%E8%AF%A2%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%E5%88%97%E8%A1%A8" title="DescribeVpcEx">DescribeVpcEx</a>接口查询VPC |
| InvalidNetworkInterface.NotFound | 无效的弹性网卡，弹性网卡资源不存在。请再次核实您输入的资源信息是否正确，可通过<a href="https://cloud.tencent.com/doc/api/245/%e6%9f%a5%e8%af%a2%e5%bc%b9%e6%80%a7%e7%bd%91%e5%8d%a1%e4%bf%a1%e6%81%af?viewType=preview" title="DescribeNetworkInterfaces">DescribeNetworkInterfaces</a>接口查询弹性网卡 |
| InvalidInstance.NotFound | 无效的云主机实例，云主机实例资源不存在。请再次核实您输入的资源信息是否正确，可通过<a href="https://cloud.tencent.com/doc/api/229/831" title="DescribeInstances">DescribeInstances</a>接口查询云主机实例 |
| InvalidNetworkInterface.NotAttached | 弹性网卡和云主机已解绑 |

## 5. 示例
输入
<pre>
https://vpc.api.qcloud.com/v2/index.php?Action=DetachNetworkInterface
&<<a href="https://cloud.tencent.com/doc/api/229/6976">公共请求参数</a>>
&vpcId=vpc-7t9nf3pu
&networkInterfaceId=eni-m6dyj72l
&instanceId=ins-xx44545f
</pre>
输出
```
{
    "code": 0,
    "message": "",
    "codeDesc": "Success",
    "data":
        {
            "taskId": 16284
        }
}
```


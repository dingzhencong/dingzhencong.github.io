---
title: 源码
tags: 
    - java
    - source code
type: "tags"
---

# java.lang

## Object
- protected方法2个，分别是finalize()、clone();
- native修饰的方法6个，分别是hashCode()、notify()、notifyAll()、wait(long timeout)、clone()、getClass();
- final方法4个,而且都是native方法，分别是notify()、notifyAll()、wait(long timeout)、getClass();
> Object的6个native方法中只有hashCode()、clone()不被final修饰
```java
    public String toString(){
        return getClass().getName() + "@" + Integer.toHexString(hashCode());
    }

    public boolean equals(){
        return (this == obj);
    }

    public native int hashCode();

    protected void finalize() throws Throwable { }

    public final native void notify();

    public final native void notifyAll();

    public final native void wait(long timeout) throws InterruptedException;

    protected native Object clone();

    public final native Class<?> getClass();

```
<!-- more -->
## ThreadLocal

ThreadLocalMap是Thread的属性，set的时候也是以Thread为key，为什么要用Entry[]数组存储
1. replaceStaleEntry方法，为什么需要向前向后搜索相同的key？
```java
    public void set(T value) {
        Thread t = Thread.currentThread();
        ThreadLocalMap map = getMap(t);
        if (map != null)
            map.set(this, value);
        else
            createMap(t, value);
    }

    ThreadLocalMap getMap(Thread t) {
        return t.threadLocals;
    }

    /* ThreadLocal values pertaining to this thread. This map is maintained
     * by the ThreadLocal class. */
    ThreadLocal.ThreadLocalMap threadLocals = null;

```


# java.util

## Collection

## Queue:
        insert:
            add()
            offer()
        delete:
            remove()
            poll()
        exist:
            element()
            peek()


```json
{
    "SYS_HEAD": {
        "serviceCode": "服务代码",
        "serviceScenario": "服务场景",
        "serviceVersion": "服务版本",
        "serviceRequestSystemNumber": "服务请求系统编号",
        "serviceRequestSystemModuleNumber": "服务请求系统子模块编号",
        "serviceRequestSystemSerialNumber": "服务请求系统流水号",
        "serviceRequestSystemTransactionDate": "服务请求系统交易日期",
        "serviceRequestSystemTransactionTime": "服务请求系统交易时间",
        "serviceRequestSystemTerminalNumber": "服务请求系统终端号",
        "serviceRequestSystemChannelType": "服务请求系统渠道类型",
        "sourceServiceRequestSystemNumber": "源服务请求系统编号",
        "sourceServiceRequestSystemSubmoduleNumber": "源服务请求系统子模块编号",
        "sourceServiceRequestSystemSerialNumber": "源服务请求系统流水号",
        "sourceServiceRequestSystemTransactionDate": "源服务请求系统交易日期",
        "sourceServiceRequestSystemTransactionTime": "源服务请求系统交易时间",
        "transactionModel": "交易模式",
        "userLanguage": "用户语言",
        "macCheckNodeNumber": "Mac校验的节点号",
        "macNumber": "Mac值"
    },
    "APP_HEAD": {
        "agent": "经办人",
        "organizationCode": "组织机构代码",
        "agentLevel": "经办人级别",
        "agentCategory": "经办人类别",
        "reviewMark": "复核标志",
        "reviewerArray": [
            {
                "transactionReviewerNumber": "交易复核员号",
                "transactionReviewOrganizationCode": "交易复核机构代码",
                "transactionReviewerLevel": "交易复核员级别",
                "transactionReviewerCategory": "交易复核员类别"
            }
        ],
        "approvalMark": "审批标志",
        "approverInformationArray": [
            {
                "approverNumber": "审批员号",
                "approvalOrganizationCode": "审批机构代码",
                "approverPassword": "审批员密码",
                "approverLevel": "审批员级别",
                "approverCategory": "审批员类别"
            }
        ],
        "channelCode": "渠道号",
        "channelType": "渠道类型",
        "productCode": "产品代码",
        "productType": "产品类型",
        "clientNumber": "客户号",
        "transactionRelatedClientName": "交易关联客户名称",
        "clientType": "客户类型",
        "clientGrade": "客户等级"
    },
    "LOCAL_HEAD": {},
    "BODY": {}
}

{
    "SYS_HEAD": {
        "serviceCode": "服务代码",
        "serviceScenario": "服务场景",
        "serviceVersion": "服务版本",
        "serviceRequestSystemNumber": "服务请求系统编号",
        "serviceRequestSystemModuleNumber": "服务请求系统子模块编号",
        "serviceRequestSystemSerialNumber": "服务请求系统流水号",
        "serviceRequestSystemChannelType": "服务请求系统渠道类型",
        "serviceRequestSystemTerminalNumber": "服务请求系统终端号",
        "sourceServiceRequestSystemNumber": "源服务请求系统编号",
        "sourceServiceRequestSystemSubmoduleNumber": "源服务请求系统子模块编号",
        "sourceServiceRequestSystemSerialNumber": "源服务请求系统流水号",
        "serviceProvisionSystemNumber": "服务提供方系统编号",
        "serviceProvisionSystemSerialNumber": "服务提供系统流水号",
        "serviceProvisionSystemTransactionDate": "服务提供系统交易日期",
        "serviceProvisionSystemTransactionTime": "服务提供系统交易时间",
        "systemProcessingResult": "系统处理结果",
        "userLanguage": "用户语言",
        "macCheckNodeNumber": "Mac校验的节点号",
        "macNumber": "Mac值",
        "transactionReturnCodeArray": [
            {
                "transactionReturnCode": "交易返回代码",
                "transactionReturnInformation": "交易返回信息"
            }
        ]
    },
    "APP_HEAD": {
        "agent": "经办人",
        "organizationCode": "组织机构代码",
        "agentLevel": "经办人级别",
        "agentCategory": "经办人类别",
        "reviewMark": "复核标志",
        "reviewerArray": [
            {
                "transactionReviewerNumber": "交易复核员号",
                "transactionReviewOrganizationCode": "交易复核机构代码",
                "transactionReviewerLevel": "交易复核员级别",
                "transactionReviewerCategory": "交易复核员类别"
            }
        ],
        "approvalMark": "审批标志",
        "approverInformationArray": [
            {
                "approverNumber": "审批员号",
                "approvalOrganizationCode": "审批机构代码",
                "approverLevel": "审批员级别",
                "approverCategory": "审批员类别"
            }
        ],
        "channelCode": "渠道号",
        "channelType": "渠道类型",
        "productCode": "产品代码",
        "productType": "产品类型",
        "clientNumber": "客户号",
        "transactionRelatedClientName": "交易关联客户名称",
        "clientType": "客户类型",
        "clientGrade": "客户等级"
    },
    "LOCAL_HEAD": {},
    "BODY": {}
}
```

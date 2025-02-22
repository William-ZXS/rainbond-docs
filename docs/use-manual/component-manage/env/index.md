---
title: 组件环境变量
---

## 组件环境变量管理
组件支持自定义环境变量，用户以 Key | Value 的形式在环境变量中添加，并会将环境变量注入到组件中。

### 添加环境变量

组件 -> 环境变量 -> 添加变量。

* 变量名：key
* 变量值：value
* 说明：变量说明，不会注入到组件中

### 删除环境变量

组件 -> 环境变量 -> 删除变量

:::danger
注意：变量删除后不可恢复
:::

### 修改环境变量

组件 -> 环境变量 -> 修改

环境变量仅支持修改 `变量值`

### 转移环境变量

将环境变量转移为依赖的环境变量，在该组件被依赖时，此环境变量将会注入到依赖的组件中。

> 转移后环境变量依然会在当前组件中生效。

:::danger

以上环境变量的操作均需要更新/重启组件后生效。

:::


## 组件配置文件管理

配置文件挂载是指我们将文件内容填写到 Rainbond 中，Rainbond以文件的形式挂载到组件中。

### 添加配置文件

进入组件 -> 环境配置 -> 配置文件设置 -> 添加配置文件

<img src="https://static.goodrain.com/docs/5.6/use-manual/component-manage/env/configmap.png" width="30%" />

配置文件信息：

* 配置文件名称：自定义 (不是文件名称)
* 配置文件挂载路径：需填写绝对路径包含文件名，例如：/data/test.conf
* 权限：文件的权限，例如：777
* 配置文件内容：自定义

### 编辑配置文件

进入组件 -> 环境配置 -> 配置文件设置 -> 编辑配置文件

`配置文件挂载路径`、`权限`、`配置文件内容` 均可以修改，配置文件名称不可修改。

Rainbond 会校验是否修改了配置文件内容，如未修改将无法保存。

### 删除配置文件

进入组件 -> 环境配置 -> 配置文件设置 -> 删除配置文件

注意：删除后将不可恢复

:::danger

以上配置文件的操作均需要更新/重启组件后生效。

:::

## 共享配置文件

共享配置文件是将别的组件的配置文件挂载到当前的组件中，适用于多个组件配置文件一致的场景。

### 挂载共享配置文件

进入组件 -> 环境配置 -> 共享配置文件设置 -> 挂载共享配置文件

填写本地挂载路径：

* 勾选需要挂载配置文件的组件
* 填写本地挂载配置文件路径：需写绝对路径包含文件名

![](https://static.goodrain.com/docs/5.6/use-manual/component-manage/env/share-configmap.png)

### 取消挂载共享配置文件

进入组件 -> 环境配置 -> 共享配置文件设置 -> 取消挂载



:::danger

以上共享配置文件的操作均需要更新/重启组件后生效。

:::



### 组件高级环境变量配置

```mdx-code-block
import DocCardList from '@theme/DocCardList';
import {useCurrentSidebarCategory} from '@docusaurus/theme-common';

<DocCardList items={useCurrentSidebarCategory().items}/>
```
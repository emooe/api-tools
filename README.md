<div align="center">
<img alt="logo" height="120" src="./public/favicon.png" width="120"/>
<h2>API Tools</h2>
<p>基于 Typescript、Koa 实现的一些实用的 API 工具, 如随机图片、每日必应、本地IP等 | Some practical API Tools, such as random pictures, daily Bing, local IP, etc.</p>
</div>

## 总览

> 🟢 状态正常
> 🟠 可能失效
> ❌ 无法使用

| **功能** | **调用名称**  | **状态** |
| -------- | ------------- | -------- |
| 随机图片 | img           | 🟢       |
| 每日必应 | bing          | 🟢       |
| 站点状态 | status        | 🟢       |
| 定时任务 | 无 <默认关闭> | 🟢       |

## 启动

```js
// 安装依赖
yarn

// 构建
yarn build

// 本地开发
yarn dev

// 云端部署
yarn start
```

## 使用

### 1、随机图片 API

- 随机跳转一张图片

  ```http
  GET https://example.com/img
  ```

- 跳转到指定 ID 的图片

  ```http
  GET https://example.com/img?id=1
  ```

- 获取包含随机 ID 的图片信息，以 json 格式返回

  ```http
  GET https://example.com/img?type=json
  ```

- 获取包含指定 ID 的图片信息，以 json 格式返回

  ```http
  GET https://example.com/img?id=1&type=json
  ```

- 服务端随机加载一张图片并输出
  ```http
  GET https://example.com/img?type=raw
  ```
- 服务端加载指定 ID 的图片并输出

  ```http
  GET https://example.com/img?id=1&type=raw
  ```

- 支持参数
  | **参数** | **默认** | **必填** | **说明** |
  |--------|--------|--------|----------------------|
  | id | 无 | 否 | 图片 ID |
  | type | 无 | 否 | 'json'或'raw'，以 json 格式返回或服务端渲染 |

### 2、每日必应

- 详细信息

  ```http
  GET https://example.com/bing
  ```

- 直接输出图片

  ```http
  GET https://example.com/bing/image/
  ```

- 支持参数
  | **参数** | **默认** | **必填** | **说明** |
  |--------|--------|--------|----------------------|
  | width | 无 | 否 | 图宽度片 |
  | height | 无 | 否 | 图片高度 |
  | size | 1 | 否 | 获取的图片数量，最大为 8 |
  | days | 0 | 否 | 获取的图片在历史记录中的索引，最大为 7 |

### 3、站点状态

反代 `UptimeRobot` 以实现站点监控

```http
POST https://example.com/status
```

### 定时任务

目前添加了一个定时任务，支持在每天晚上 8 点同步今日必应图片到远程 Github 文件夹

远程仓库：https://github.com/heiemooa/folder

### 持续添加中

## Vercel 部署

现已支持 Vercel 部署，无需服务器

### 操作方法

1. fork 本项目
2. 在 `Vercel` 官网点击 `New Project`
3. 点击 `Import Git Repository` 并选择你 fork 的此项目并点击 `import`
4. `PROJECT NAME`自己填，`FRAMEWORK PRESET` 选 `Other` 然后直接点 `Deploy` 接着等部署完成即可

## 其他

- 本项目为了避免频繁请求官方数据，默认对数据做了缓存处理，默认为 `30` 分钟，如需更改，请自行前往 `utils\cacheData.js` 文件修改
- 本项目部分接口使用了 **页面爬虫**，若违反对应页面的相关规则，请 **及时通知我去除该接口**

## 免责声明

- 本项目提供的 `API` 仅供开发者进行技术研究和开发测试使用。使用该 `API` 获取的信息仅供参考，不代表本项目对信息的准确性、可靠性、合法性、完整性作出任何承诺或保证。本项目不对任何因使用该 `API` 获取信息而导致的任何直接或间接损失负责。本项目保留随时更改 `API` 接口地址、接口协议、接口参数及其他相关内容的权利。本项目对使用者使用 `API` 的行为不承担任何直接或间接的法律责任
- 本项目并未与相关信息提供方建立任何关联或合作关系，获取的信息均来自公开渠道，如因使用该 `API` 获取信息而产生的任何法律责任，由使用者自行承担
- 本项目对使用 `API` 获取的信息进行了最大限度的筛选和整理，但不保证信息的准确性和完整性。使用 `API` 获取信息时，请务必自行核实信息的真实性和可靠性，谨慎处理相关事项
- 本项目保留对 `API` 的随时更改、停用、限制使用等措施的权利。任何因使用本 `API` 产生的损失，本项目不负担任何赔偿和责任

## 鸣谢

- [ToolsApi](https://github.com/imsyy/ToolsApi) 基于此项目进行修改，并 Typescript 语言化

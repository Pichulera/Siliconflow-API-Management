# 硅基流动API聚合管理系统 🚀

## 项目概述 💡

硅基流动API聚合管理系统是一个功能强大的API Key管理平台，不仅通过智能负载均衡算法自动选择可用API密钥，而且提供密钥有效性检测、管理、权限分享等功能实现。系统设计基于Cloudflare Worker脚本，部署简单，同时提供强大的可视化管理工具与全面的数据分析功能。

## ✨ 核心特性

- **🔄 自动负载均衡**：智能分配请求至有效密钥，最大化资源利用率
- **⚡ 高可用架构**：单个密钥故障不影响整体服务可用性
- **📊 可视化分析**：直观图表展示密钥分布、状态与余额趋势
- **🛡️ 多级权限控制**：支持开放、受限和私有三种访问模式进行个性化分享
- **🔍 实时监控**：密钥状态与余额的实时跟踪与更新
- **📱 响应式设计**：完美支持PC端和移动端访问体验

## 🖥️ 功能模块

### 前台功能
- **密钥浏览**：查看所有可用的API密钥及其余额状态
- **API调用文档**：详尽的API调用指南与代码示例
- **智能访问控制**：根据管理员设置提供适当的访问限制

### 管理功能
- **📈 高级仪表盘**
  - 核心指标实时监控（总密钥、有效密钥、平均余额等）
  - 最新添加密钥追踪
  - 余额与状态统计图表
  - 余额趋势分析与异常值过滤

- **🔑 多维度密钥管理**
  - 单个/批量添加密钥
  - 一键检测余额（支持自定义检测参数）
  - 多选操作支持（检测、删除、导出）
  - 智能排序与状态过滤

- **📤 高级导出功能**
  - 支持多种导出格式（纯密钥/带余额格式）
  - 自定义分隔符设置（换行符、逗号、空格、分号、制表符、自定义字符）
  - 条件筛选导出（全部/有效/高余额）
  - 一键复制到剪贴板功能

- **⚙️ 全面系统设置**
  - 管理员账户配置
  - 访问控制模式设置
  - 界面显示参数调整
  - 访客密码管理

## 📊 数据分析与图表

系统内置多种专业图表，帮助管理员深入了解API密钥使用情况：

- **余额分布图**：直观展示不同余额区间的密钥数量分布
- **状态分布图**：清晰呈现有效、无效和错误密钥的比例
- **余额趋势图**：追踪密钥余额变化趋势，支持异常值智能过滤
- **关键指标卡片**：展示最高余额、最低有效余额、中位数余额和总余额

## 🔍 密钥检测高级特性

系统提供极其灵活的密钥检测机制：

- **🕒 智能间隔控制**：支持固定间隔和随机间隔两种模式，可自定义间隔时间范围
- **🔄 完善重试策略**：自定义重试次数与间隔，智能处理临时网络问题
- **📶 实时进度追踪**：检测过程中提供详细的进度、处理速度和预估完成时间
- **⏱️ 动态速率控制**：实时调整API请求速率，有效避免触发API限流保护
- **🛑 中途终止功能**：支持随时停止批量操作，灵活应对需求变化

## 🔌 API调用方式

调用方式与原始API完全相同，只需将请求地址修改为您的代理地址：

```bash
curl -X POST 'https://你的域名/v1/chat/completions' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer your-api-key-here' \
-d '{"model": "Qwen/Qwen2.5-7B-Instruct", "messages": [{"role": "user", "content": "你好"}], "stream": true}'
```

## 🖼️ 界面预览

### 前台密钥浏览界面
![前台界面](https://imgbed.killerbest.com/file/1742612438557_image.png)

### 管理员界面
![管理员仪表盘](https://imgbed.killerbest.com/file/1742612540433_image.png)

### 密钥管理与批量操作
![密钥管理界面](https://imgbed.killerbest.com/file/1742612823663_image.png)

### 数据分析图表
![数据分析图表](https://imgbed.killerbest.com/file/1742612682430_image.png)

### 系统设置
![系统设置界面](https://imgbed.killerbest.com/file/1742612987996_image.png)

## 🌐Demo站点

### [硅基API Key聚合管理系统](https://sili-api.killerbest.com/)

## 🚀 部署教程

### 在Cloudflare Workers部署

1. **准备工作** 📋
   - 注册并登录Cloudflare账号
   - 进入Cloudflare Workers & Pages管理界面

2. **创建KV命名空间** 🗃️
   - 在Workers界面点击"KV"选项卡
   - 创建新的命名空间，命名为`SILICONFLOW_KEY`

3. **创建并配置Worker** ⚙️
   - 点击"创建Worker"按钮
   - 将脚本代码完整复制到Worker编辑器
   - 在"设置"选项卡中，绑定KV命名空间:
     - 变量名设置为`SILICONFLOW_KEY`
     - 选择刚创建的KV命名空间

4. **部署与访问** 🌐
   - 点击"保存并部署"按钮
   - 部署成功后，您将获得一个`*.workers.dev`域名
   - 可选：绑定自定义域名以获得更专业的访问地址

## 🔧 初始配置

1. **首次访问设置** 🔑
   - 在worker脚本最顶部代码，初始化的**用户名**、**密码**、**代理密钥**等
   > 说明：仅作初始化操作，部署后登录管理员后台可更改 
     - 用户名: `default-admin-username`
     - 密码: `default-admin-password`
     - 代理密钥： `default-api-key`

2. **基础安全配置** 🛡️
   - 访问部署地址，选择登录管理员界面
   - 配置适合的访问控制模式
   - 如使用"部分开放"模式，设置安全的访客密码

3. **API域名配置** 🌐
   - 在worker脚本中搜索并替换API教程弹窗中的域名 `<you-project-domain>`
   - 主要位置:
     - API示例请求代码块（约1950行）
     - 端点替换示例（约1980行）
     
 	> 说明：一共四处，分别是两处展示和两处复制内容，都要进行替换
   
   - 将其替换为您部署worker的域名

4. **添加API密钥** ➕
   - 在密钥管理页面添加您的API密钥
   - 使用批量导入功能快速添加多个密钥
   - 点击"更新所有余额"按钮检测所有密钥状态
   
## 🚀 高级使用技巧

### 密钥管理与导出
- **智能排序系统** 📊：支持按余额、更新时间或添加时间排序，升序降序自由切换
- **多格式导出** 📁：支持纯密钥或带余额格式，多种分隔符选择（换行符、逗号、空格等）
- **条件筛选导出** 🔍：基于余额阈值导出高价值密钥，一键复制到剪贴板
- **批量管理功能** 🗂️：强大的多选操作，支持跨页选择和快速筛选

### 数据分析与监控
- **周期选择** 📅：查看全部、最近7天或30天的数据
- **异常值处理** 📈：智能过滤异常值，获得更清晰的数据展示
- **趋势分析** 📉：深入了解密钥余额变化情况，预测资源使用趋势
- **实时状态监控** 📌：自动追踪密钥状态变化，及时发现异常

## 🛡️ 安全建议

- 部署后立即修改默认管理员密码
- 定期清理无效密钥，保持系统整洁
- 使用"部分开放"或"完全私有"模式增强安全性
- 推荐使用自定义域名并启用HTTPS加密
- 定期备份重要密钥数据

## 🔮 未来规划

> 事太多了最近，先鸽着吧

## 📞 技术支持

如有任何问题或建议，请联系管理员：admin@killerbest.com

---

© 2025 KillerBest. 保留所有权利。

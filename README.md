# TVBox 电视频道菜单自定义与直播源接口自动更新

自定义频道菜单，根据模板文件的直播源接口，自动获取并更新最新的直播源接口，生成可用的频道接口文件

[English](./README-EN.md) | 中文

## 特点

- 自定义模板，生成您想要的频道分类与频道顺序
- 接口验效，过滤无效接口
- 按响应时间、分辨率综合权衡排序
- 定时执行，每隔 12 小时执行更新一次
- 可设置重点关注频道，单独配置获取分页的数量
- 分页结果获取（可配置页数、总接口数量）

## 使用方法

1. Fork 此项目，开启 Action 工作流可读写权限：

   - Settings → Actions → General → Workflow permissions → Read and write permissions → Save

2. 修改 demo.txt 模板文件，修改成您想要的频道分类与频道顺序，后续更新根据此文件内容进行更新。
3. 修改配置（可选）：

   #### config.py：

   - source_file：模板文件，默认值：demo.txt
   - final_file：生成文件，默认值：result.txt
   - favorite_list：关注频道名称列表
   - favorite_page_num：关注频道获取分页数量，默认值：5
   - default_page_num：常规频道获取分页数量，默认值：3
   - urls_limit：接口数量，默认值：15
   - response_time_weight：响应时间权重值，默认值：0.5
   - resolution_weight：分辨率权重值，默认值：0.5

   #### .github/workflows/main.yml：

   - 如果您想修改更新频率（默认 12 小时），可修改 on:schedule:- cron 字段

4. result.txt 为更新后的直播源接口文件，source.json 为数据源文件（目前仅作分享使用）
5. 建议采用代理的方式访问直播源与数据源文件（xxx 为您的仓库路径）：
   - https://mirror.ghproxy.com/raw.githubusercontent.com/xxx/result.txt
   - https://mirror.ghproxy.com/raw.githubusercontent.com/xxx/source.json

## 更新日志

### 2024/3/4

- 增加配置项：响应时间与分辨率权重值
- 移除配置项：是否过滤无效接口，始终执行过滤
- 移除按日期排序，采用响应时间与分辨率作为排序规则
- 更新 README：增加修改更新频率、文件代理说明、更新日志

## 免责声明

本项目是为了提供编程学习和研究的资源。项目中收集的数据来源于网络，开发者不对数据的准确性、完整性或可靠性做任何保证。

开发者不对任何可能因使用这些代码或数据而产生的任何直接或间接损失负责。使用者应自行判断其使用的合法性和风险。

本项目的代码和数据仅供学习和研究使用，不得用于任何商业用途。任何人或组织在使用时，应遵守相关法律法规，尊重并保护开发者的权益。

如果您使用了本项目的代码或数据，即表示您已了解并同意此免责声明。如果您不同意此免责声明，您应立即停止使用本项目的代码和数据。

此外，本项目的代码和数据可能会不定期进行更新，但不保证更新的及时性和准确性，也不保证代码的稳定性和功能性。

在任何情况下，因使用或无法使用本项目的代码或数据所产生的任何损害或其他责任，开发者和任何贡献者都不承担任何责任。

使用本项目的代码或数据即表示您已经了解并接受这些条款。

## 许可证

[MIT](./LICENSE) License &copy; 2024-PRESENT [Govin](https://github.com/guovin)

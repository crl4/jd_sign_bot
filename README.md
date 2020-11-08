<p align="center">
    <img src="https://cdn.jsdelivr.net/gh/ruicky/ruicky.github.io/2020/06/05/jd-sign/0.png">
</p>

<p align="center">
    <img alt="Version" src="https://img.shields.io/badge/release-0.0.1-blue"/>
    <a href="https://github.com/ruicky">
        <img alt="Author" src="https://img.shields.io/badge/author-ruicky-blueviolet"/>
    </a>
</p>
## 利用GitHub Actions每天定时给百度推送链接，提高收录率 ##

name: baiduPush

# 两种触发方式：一、push代码，二、每天国际标准时间23点（北京时间+8即早上7点）运行
# on:
#  push:
#  schedule:
#    - cron: '0 23 * * *' # https://help.github.com/en/actions/automating-your-workflow-with-github-actions/events-that-trigger-workflows#scheduled-events-schedule

 on:
   schedule:
     - cron: '*/5 * * * *' # 每5分钟一次，测试用

jobs:
  bot:
    runs-on: ubuntu-latest # 运行环境为最新版的Ubuntu
    steps:
      - name: 'Checkout codes' # 步骤一，获取仓库代码
        uses: actions/checkout@v1
      - name: 'Run baiduPush' # 步骤二，执行sh命令文件
        run: npm install && npm run baiduPush # 运行目录是仓库根目录
# 京东自动签到
功能：
1. 获取签到最新代码
2. 替换参数值
3. 签到并发送通知


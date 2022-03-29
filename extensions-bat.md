- Node 安装
  通过[官网](https://nodejs.org/en/)下载运行包
- bat方式

```bash
@echo off
echo 正在自动下载资源到文档中
echo 当前登录本机的账户是：%username%
echo obs目录初始化
if  EXIST C:\Users\%username%\Documents\obs (
	echo 已经存在obs目录
  :loop
  set /p a=确定要执行文件覆盖功能吗？（1继续，0退出）
  if /i '%a%'=='1' goto continue
  if /i '%a%'=='0' goto end
  echo 输入有误，请重新输入：&&goto loop
  :continue
  rmdir C:\Users\%username%\Documents\obs
  echo obs正在初始化...
  mkdir C:\Users\%username%\Documents\obs
  :end
  @exit
) else (
	echo obs正在初始化...
	mkdir C:\Users\%username%\Documents\obs
)
echo crx插件直接下载
powershell (new-object Net.WebClient).DownloadFile('https://github.com/czj306/test/raw/master/requests.crx','C:\Users\%username%\Documents\obs\requests.crx')

echo 相关流程直接下载
powershell (new-object Net.WebClient).DownloadFile('https://github.com/czj306/test/raw/master/Station.json','C:\Users\%username%\Documents\obs\Station.json')

echo socket下载
powershell (new-object Net.WebClient).DownloadFile('https://raw.githubusercontent.com/czj306/test/master/obs.js','C:\Users\%username%\Documents\obs\obs.js')

echo file下载
powershell (new-object Net.WebClient).DownloadFile('https://raw.githubusercontent.com/czj306/test/master/file.js','C:\Users\%username%\Documents\obs\file.js')

echo 安装forever
npm install -g forever
echo 永久启动服务
forever start C:\Users\%username%\Documents\obs.js

echo 打开谷歌浏览器
start "" "C:\Program Files\Google\Chrome\Application\chrome.exe"
```

- 


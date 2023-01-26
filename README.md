Migrate from WizNote to Joplin.
## 快速操作
### 环境
- Python版本：Python 3.11.1
- wiz版本：windows经典版 ver4.14.3 [网页](https://www.wiz.cn/zh-cn/downloads-windows.html)[下载](https://url.wiz.cn/u/windows)
### 步骤
- 解压zip包到桌面，文件夹名称为wiz2joplin
- 为知笔记目录：F:\Wiz_note\Data（根据自己的笔记路径修改）
- 打开cmd依次输入下面命令
```
python -m venv C:\Users\Administrator\Desktop\wiz2joplin\env\w2j\venv --clear
C:\Users\Administrator\Desktop\wiz2joplin\env\w2j\venv\Scripts\activate.bat
pip install w2j --no-cache-dir或者python setup.py install
w2j -o C:\Users\Administrator\Desktop\wiz2joplin\wiz2joplin_output -w F:\Wiz_note\Data -u 你的账号邮箱xxx@qq.com -t 你的joplin的token -a
```

## !!!CAUTION!!!!

wiz2joplin 0.5 has only been tested in wizNote for Win with wiznote ver4.14.2, not test in wiznoteX.
the folder structure of the macOS and Windows versions of wizNote is different, but maybe this version is also compatible for mac.



## Dependency

- Python 3.9
- macOS Catalina or above
- wizNote for Mac 2.8.7 (2020.8.20 10:28)
- ![wiznote for macOS](wiznoteformac.png)

## Installation

To install this tool, you can use pip:

```
python -m venv ~/w2j/venv
source ~/w2j/venv/bin/activate
pip install w2j
```

Alternatively, you can install the package using the bundled setup script:

```
python -m venv ~/w2j/venv
source ~/w2j/venv/bin/activate
python setup.py install
```

## Usage

If your WizNote user id is `youremail@yourdomain.com`, the token in Joplin Web Clipper is `aa630825022a340ecbe5d3e2f25e5f6a`, and Joplin run on the same computer, you can use wiz2joplin like follows.

Convert all of documents from wizNote to Joplin:

``` shell
w2j -o ~/w2j -w ~/.wiznote -u youremail@yourdomain.com -t aa630825022a340ecbe5d3e2f25e5f6a -a
```

Convert location `/My Notes/reading/` and all of the children documents from WizNote to Joplin:

``` shell
w2j -o ~/w2j -w ~/.wiznote -u youremail@yourdomain.com -t aa630825022a340ecbe5d3e2f25e5f6a -l '/My Note/reading/' -r

```

Use `w2j --help` to show usage for w2j:

```
usage: w2j [-h] --output OUTPUT --wiz-dir WIZNOTE_DIR --wiz-user
           WIZNOTE_USER_ID --joplin-token JOPLIN_TOKEN
           [--joplin-host JOPLIN_HOST] [--joplin-port JOPLIN_PORT]
           [--location LOCATION] [--location-children] [--all][--log-level]

Migrate from WizNote to Joplin.

optional arguments:
  -h, --help            show this help message and exit
  --output OUTPUT, -o OUTPUT
                        The output dir for unziped WizNote file and log file.
                        e.g. ~/wiz2joplin_output or
                        C:\Users\zrong\wiz2joplin_output
  --wiz-dir WIZNOTE_DIR, -w WIZNOTE_DIR
                        Set the data dir of WizNote. e.g ~/.wiznote or
                        C:\Program Files\WizNote
  --wiz-user WIZNOTE_USER_ID, -u WIZNOTE_USER_ID
                        Set your user id(login email) of WizNote.
  --joplin-token JOPLIN_TOKEN, -t JOPLIN_TOKEN
                        Set the authorization token to access Joplin Web
                        Clipper Service.
  --joplin-host JOPLIN_HOST, -n JOPLIN_HOST
                        Set the host of your Joplin Web Clipper Service,
                        default is 127.0.0.1
  --joplin-port JOPLIN_PORT, -p JOPLIN_PORT
                        Set the port of your Joplin Web Clipper Service,
                        default is 41184
  --location LOCATION, -l LOCATION
                        Convert the location of WizNote, e.g. /My Notes/. If
                        you use the --all parameter, then skip --location
                        parameter.
  --location-children, -r
                        Use with --location parameter, convert all children
                        location of --location.
  --all, -a             Convert all documents of your WizNote.
  --log-level           Use with --log-level to set the log level, default is INFO,
                        other choice are "CRITICAL", "ERROR", "WARNING", "INFO", "DEBUG".
```

## Log file

Please read log file `w2j.log` under --output directory to check the conversion states.

## 源码分析相关文章

- [从 WizNote 为知笔记到 Joplin（上）](https://blog.zengrong.net/post/wiznote2joplin1/)
- [从 WizNote 为知笔记到 Joplin（下）](https://blog.zengrong.net/post/wiznote2joplin2/)
- [WizNote 为知笔记 macOS 本地文件夹分析](https://blog.zengrong.net/post/analysis-of-wiznote/)
- [使用腾讯云对象存储(COS)实现Joplin同步](https://blog.zengrong.net/post/joplin-sync-use-cos/)
- [配置 Joplin Server 实现同步](https://blog.zengrong.net/post/joplin-server-config/)

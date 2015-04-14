## Reveal.jsでプレゼン資料を作ってみよう


---

### はじめに

- これはDockerコンテナのCentOS7向けの資料となります。

---

### Githubで資料作成用のレポジトリを作成する

(GitLabなどGithubクローンでも結構です)

例）

```
hayao56/presen0424
```

```
http://115.125.186.10/presen0424/presen-webhook/deploy
```



--

### ホストPCの nginxの設定

ホストPCにSSH接続します

例）
```
$ cd ~/bigdata/
$ ssh g-hayakawa@192.168.0.225 -i ~/bigdata/g-hayakawa_is_rsa
```

```
$ su root
パスワード
```

---

### dockerにコンテナ作成

```
$ docker run --privileged -it -v /Users/work:/work -P -d --name presen0424 gorohayakawa/centos7-nginx:latest
```

```
$ docker-enter presen0424
```

以降、dockerコンテナ内の作業となります。


---

### Rubyのインストール

```
# yum install gcc gcc-c++ make openssl-devel zlib-devel
```
コンパイル用のパッケージは、先にインストールする

```
# yum install ruby ruby-devel rubygems
# yum install sqlite-devel
# ruby --version
ruby 2.0.0p598 (2014-11-13) [x86_64-linux]
```

---

### コンテナ内のネットワーク確認

```
# yum install net-tools
```

コンテナのIPアドレスを確認
172.17.1.110

```
# ifconfig

eth0: flags=67<UP,BROADCAST,RUNNING>  mtu 1500
        inet 172.17.1.110  netmask 255.255.0.0  broadcast 0.0.0.0
        inet6 fe80::42:acff:fe11:16e  prefixlen 64  scopeid 0x20<link>
        ether 02:42:ac:11:01:6e  txqueuelen 0  (Ethernet)
        RX packets 26762  bytes 78588164 (74.9 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 21353  bytes 1494471 (1.4 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

---

### コンテナ内nginxのポート番号を変更

```
# vim /etc/nginx/conf.d/default.conf
```

```
server {
    listen       3006;
    server_name  localhost;
```
↑ ここを3006に変更

ドメイン「/slide」、ポート9000をコンテナ用の公開ディレクトリとして割り当てます。
```
    location /slide {
        rewrite ^/slide/(.+) /$1 break;
        proxy_pass http://127.0.0.1:9000;
    }
```


nginxの再起動
```
# systemctl restart nginx
```


---


### コンテナ内nginxの動作確認


確認したコンテナのIPアドレスにアクセス

```
# curl 172.17.1.110:3006

<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

---

### ホストのnginxの設定

# vim /etc/nginx/conf.d/default.conf
```

ドメイン「/drone」、ポート3005をコンテナ用の公開ディレクトリとして割り当てます。
```
    location /presen {
        rewrite ^/presen/(.+) /$1 break;
        proxy_pass http://172.17.1.110:3006;
    }
```
↑ proxy_passはコンテナのIPアドレス



nginxの再起動
```
systemctl restart nginx
```


```
# curl 127.0.0.1/presen/index.html
```

```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```


---

### Gitのインストール、バージョン確認

```
# yum install git
# git --version
git version 1.8.3.1

# git config --global user.name "hayao56" && git config --global user.email "hayao56@gmail.com" 

```

---

### 公開ディレクトリでGit Cloneします

例）

```
# cd /usr/share/nginx/html
# git clone https://github.com/hayao56/presen0424.git

# chmod 775 -R /usr/share/nginx/html/presen0424 && cd $_
```


---

### treeをインストール、ディレクトリ確認

```
# yum install tree
# tree .
.
└── README.md

```

---

### 権限の変更


```
# chmod 775 -R ~/
# chown -R `whoami` ~/
```


---

### npmのインストール

```
# yum install epel-release

読み込んだプラグイン:fastestmirror
Loading mirror speeds from cached hostfile
 * base: www.ftp.ne.jp
 * epel: ftp.jaist.ac.jp
 * extras: www.ftp.ne.jp
 * updates: www.ftp.ne.jp
パッケージ epel-release-7-5.noarch はインストール済みか最新バージョンです
何もしません
```

```
# yum install nodejs npm --enablerepo=epel

# node -v
v0.10.33

# npm --version
1.3.6
```


---

### bowerのインストール


```
# npm install -g bower
# npm update -g bower
# bower --version
1.4.1
```


---

### Gruntのインストール


```
# npm install -g grunt grunt-cli
# grunt --version
grunt-cli v0.1.13
```


---

### Yeomanをインストールします

動作環境により再現できなくなることも想定されますので、インストール後に必ずバージョンを確認します。


```
# npm install -g yo
# yo --version
1.4.6
```

---

### Reveal.jsのジェネレータをインストールします

```
# npm install -g generator-reveal
```

---

### Yeomanで Reveal.jsのプロジェクトを作成します


```
# chmod -R g+rwx /root
# yo reveal

ls -la ~/.config
```
~/.config はこのタイミングで作成される


・SaaSは利用しない
・テーマは「night」

それ以外の質問はすべてデフォルト設定、Enterで回答する


```
? Do you want to use SASS to create a custom theme? This requires you to have Ruby and Sass installed. (Y/n) n

? What Reveal.js theme would you like to use?
  beige
  blood
  default
  moon
❯ night
  serif
  simple
  sky
  solarized

[?] May bower anonymously report usage statistics to improve the tool over time? (Y/n)
Bower改善のため、匿名でユーザーの使用統計を繰り返し取得しますけどいいですか？→ Y（初回のみ聞かれる）
```

エラーになった場合、node_modulesを削除して yo revealを再実行
```
rm -rf node_modules
```


---

### 画像フォルダを作成

```
$ mkdir images
```



---

### Revealサーバの起動

```
# grunt
```

---

### ホストで接続確認

```
curl 127.0.0.1/presen/presen0424/index.html
```
---

### 外部ネットワークからアクセス

```
http://115.125.186.10/presen/presen0424/index.html
```

---

### .gitignoreに設置追加

```
# vim .gitignore
```

```
node_modules
bower_components
dist
*.log
.sass-cache
index.html
.DS_Store    <-- 追加
```

---

### Gir1レポジトリにコミット


```
vim README.md
```
コメント追加


```
# git add .bowerrc
# git add .editorconfig
# git add .gitignore
# git add .jshintrc
# git add .yo-rc.json
# git add Gruntfile.coffee
# git add bower.json
# git add css/
# git add js/
# git add package.json
# git add slides/
# git add templates/
# git add README.md
```

```
git commit -m "first commit"
```

```
git push
```


---

### スライドの追加

ファイル名はlist.jsonを編集して変更できます。  

```
例）
$ yo reveal:slide "Test" --markdown
```

```
slides
├── test.md    <-- 追加されました。
├── index.md
└── list.json
```
Note: 日本語はファイル名として無視されるようです。

---

### スライドファイルを開いてみる

templates/test.md

```
例）
##  Test

This is a new Markdown slide
```




---

### deploy serverのインストール

```
# cd /usr/share/nginx/html
# git clone https://github.com/hayao56/deploy-server.git
```

---

### bundlerのインストール

```
# cd deploy-server
```

```
# vim Gemfile

以下を修正
source 'http://production.s3.rubygems.org'
#source "https://rubygems.org"
```

```
gem install bundler
```

```
# vim Gemfile

以下を修正
#source 'http://production.s3.rubygems.org'
source "https://rubygems.org"
```

```
bundle update
```


---

### Nginx reverse proxy

For CentOS7-nginx in docker container

```
vim /etc/nginx/conf.d/default.conf
```

```
    location /presen0424-webhook {
        rewrite ^/presen0424-webhook/(.+) /$1 break;
        proxy_pass http://127.0.0.1:9001;
    }
```

```
# systemctl restart nginx
```

---

### Settings

```
vim deploy_worker.rb
```

```
HOST = '127.0.0.1'
PORT = '9001'
TARGET_DIR = '/usr/share/nginx/html/presen0424'
```

---

### Run

```
export PATH=/usr/bin/ruby:$PATH && bundle exec ruby deploy_worker.rb -e production &

[2] 1344
bash-4.2# [2015-04-14 23:46:24] INFO  WEBrick 1.3.1
[2015-04-14 23:46:24] INFO  ruby 2.0.0 (2014-11-13) [x86_64-linux]
== Sinatra (v1.4.6) has taken the stage on 9001 for development with backup from WEBrick
[2015-04-14 23:46:24] INFO  WEBrick::HTTPServer#start: pid=1345 port=9001
```


---

### GitHubで WebHookの設定

```
http://115.125.186.10/presen/presen0424-webhook/deploy
```



---

### System

```
       1.Push              2.Webhook
local -----------> github -----------> deploy_worker.rb
                     ^                       |
                     |                       |
                     +-----------------------+
                            3. Pull
```





---

### スライドの順番を変更

slides/list.json

```
例）
[
    "test.md",   <-- 並べた順に表示される
    "index.md"
]
```

---

### テーマを選ぶ

公式テーマは９種類あります
```
bower_components/reveal.js/css/theme/
├── README.md
├── beige.css
├── blood.css
├── default.css
├── moon.css
├── night.css
├── serif.css
├── simple.css
├── sky.css
├── solarized.css
├── source
└── template
```

---

### テーマを変更する

templates/_index.html
```
　<link rel="stylesheet"
    href="bower_components/reveal.js/css/theme/default.css" id="theme">
```
↓　solarized.css に変更

```
例）
　<link rel="stylesheet"
    href="bower_components/reveal.js/css/theme/solarized.css" id="theme">
```

---

### スライドを起動する

```
$ grunt serve
```

---

### Chromeが起動します

![](images/sample-page.png)


---

### ページを追加

以下を2ページ目、３ページ目を追記してみましょう

templates/sample-page.md
```
例）
##  Sample Page

This is a new Markdown slide

 ---

# page 2

 ---

# page 3
```

---

### スライドをPDFで出力 #1

#### Chromeをデフォルトブラウザ設定にする

```
設定 --> 規定のブラウザに変更
```

---

### スライドをPDFで出力 #2

#### スライドをChromeで起動

```
$ grunt
```


---

### スライドをPDFで出力 #3

#### URLを変更する

```
http://localhost:9000/?#/
```
   ↓  print-pdf を追加
```
http://localhost:9000/?print-pdf#/
```

---

### スライドをPDFで出力 #4

#### PDF出力

ChromeのメニューからPDF保存

```
ファイル --> 印刷 --> 送信先を「PDFに保存」--> 保存
```

---

### スライドをPDFで出力 #5

#### PDF出力結果を確認

- リンクが表示されていない等表示がおかしい場合は_index.html 22行目あたりを修正する。


![](images/pdf-outputsource-indexhtml.png)

参考サイト http://libitte.hatenablog.jp/entry/20141129/1417252936


---

```
<!-- If the query includes 'print-pdf', use the PDF print sheet -->
<script>
if( window.location.search.match( /print-pdf/gi ) ) {
    var link = document.createElement( 'link' );
    link.rel = 'stylesheet';
    link.type = 'text/css';
    link.href = 'bower_components/reveal.js/css/print/pdf.css';
    document.getElementsByTagName( 'head' )[0].appendChild( link );
}
</script>
```





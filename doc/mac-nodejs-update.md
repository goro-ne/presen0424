
Mac OS X：sudo コマンドには非ブランク管理パスワードが必要
https://support.apple.com/ja-jp/HT202035

以下引用：
>管理者が異なるユーザとして (たとえばルート として) コマンドを実行するには sudo ターミナルコマンドを利用できます。このコマンドを実行する際は、現在ログインしている管理者アカウントのパスワードを入力するよう求められます。  

>管理者が異なるユーザとして (たとえばルートとして) コマンドを実行するには sudo ターミナルコマンドを利用できます。このコマンドを実行する際は、現在ログインしている管理者アカウントのパスワードを入力するよう求められます。

>Mac OS X v10.6 以降では、パスワードを入力しないでパスワードプロンプトで「return」キーを押すと、「Sorry, try again」というメッセージが表示され、パスワードを入力するよう再度求められます。

>お使いの管理者アカウントにパスワードが設定されていない場合 (空のパスワード)、sudo コマンドを使う前に、そのユーザアカウントにパスワードを設定します。

Mac OS X 10.6: ログインパスワードを変更する
https://support.apple.com/kb/PH6595?locale=ja_JP&viewlocale=ja_JP

以下引用：
>通常は、パスワードを入力してコンピュータにログインする必要があります。これは、「アカウントパスワード」または「ログインパスワード」と呼ばれます。自分のパスワードは変更できます。複数のアカウントがあるコンピュータの管理者であれば、自分以外のユーザのパスワードもリセットできます。

>ログインパスワードを変更するには：


>1. アップルメニュー＞「システム環境設定」と選択し、「アカウント」をクリックします。  

>2. 「パスワードの変更」をクリックします。

>3. 現在のパスワードを「古いパスワード」フィールドに入力します。  

>4. 新しいパスワードを「新しいパスワード」フィールドに入力してから、「確認」フィールドに再入力します。  
安全なパスワードを選ぶための手助けが必要な場合は、「新しいパスワード」フィールドの横にあるカギのボタンをクリックしてください。  

>5. パスワードを思い出すのに役立つヒントを入力します。誤ったパスワードをログインウインドウに連続して 3 回入力すると、このヒントが表示されます。  

>6. 「パスワードの変更」をクリックします。  

>別のユーザのログインパスワードをリセットするには：

>1. 管理者の名前とパスワードを使用してコンピュータにログインします。

>2. アップルメニュー＞「システム環境設定」と選択し、「アカウント」をクリックします。

>3. カギのアイコンをクリックしてロックを解除してから、管理者名およびパスワードを入力します。

パスワードを変更したいアカウントを選択します。

「パスワードをリセット」をクリックします。

新しいパスワードを「新しいパスワード」フィールドに入力してから、「確認」フィールドに再入力します。

安全なパスワードを選ぶための手助けが必要な場合は、「新しいパスワード」フィールドの横にあるカギのボタンをクリックしてください。

パスワードを思い出すのに役立つヒントを入力します。誤ったパスワードをログインウインドウに連続して 3 回入力すると、このヒントが表示されます。

「パスワードをリセット」をクリックします。

重要：パスワードを変更またはリセットした後は、「キーチェーンアクセス」を開いて「ログイン」キーチェーンを新しいログインパスワードと一致するように変更してください。これにより、ログイン時にキーチェーンのロックが解除されます。詳細については、以下を参照してください。

キーチェーンのパスワードを変更する






Grunt-cliは、「Gruntfile.js」と同じ階層にあるgruntを実行するためのコマンドです。Grunt-cliの働きにより複数のバージョンのGruntをプロジェクトごとに設定できるようにしてくれます。


$ node -v
v0.10.31

$ npm -v
2.7.1

$ brew -v
Homebrew 0.9.5

$ npm update

npm WARN peerDependencies The peer dependency grunt@~0.4.0 included from grunt-contrib-copy will no
npm WARN peerDependencies longer be automatically installed to fulfill the peerDependency
npm WARN peerDependencies in npm 3+. Your application will need to depend on it explicitly.
npm WARN peerDependencies The peer dependency grunt@~0.4 included from grunt-coffeelint will no
npm WARN peerDependencies longer be automatically installed to fulfill the peerDependency
npm WARN peerDependencies in npm 3+. Your application will need to depend on it explicitly.
npm WARN peerDependencies The peer dependency coffeelint@^1 included from grunt-coffeelint will no
npm WARN peerDependencies longer be automatically installed to fulfill the peerDependency
npm WARN peerDependencies in npm 3+. Your application will need to depend on it explicitly.
npm WARN peerDependencies The peer dependency grunt@~0.4.0 included from grunt-contrib-jshint will no
npm WARN peerDependencies longer be automatically installed to fulfill the peerDependency
npm WARN peerDependencies in npm 3+. Your application will need to depend on it explicitly.
npm WARN peerDependencies The peer dependency grunt@~0.4.0 included from grunt-contrib-watch will no
npm WARN peerDependencies longer be automatically installed to fulfill the peerDependency
npm WARN peerDependencies in npm 3+. Your application will need to depend on it explicitly.
npm WARN peerDependencies The peer dependency grunt@~0.4.0 included from grunt-contrib-connect will no
npm WARN peerDependencies longer be automatically installed to fulfill the peerDependency
npm WARN peerDependencies in npm 3+. Your application will need to depend on it explicitly.
npm WARN unmet dependency /Users/g-hayakawa/repos/presen0424/node_modules/grunt/node_modules/findup-sync requires glob@'~3.2.9' but will load
npm WARN unmet dependency /Users/g-hayakawa/repos/presen0424/node_modules/grunt/node_modules/glob,
npm WARN unmet dependency which is version 3.1.21
npm WARN unmet dependency /Users/g-hayakawa/repos/presen0424/node_modules/grunt/node_modules/findup-sync requires lodash@'~2.4.1' but will load
npm WARN unmet dependency /Users/g-hayakawa/repos/presen0424/node_modules/grunt/node_modules/lodash,
npm WARN unmet dependency which is version 0.9.2
npm WARN unmet dependency /Users/g-hayakawa/repos/presen0424/node_modules/grunt/node_modules/grunt-legacy-log requires lodash@'~2.4.1' but will load
npm WARN unmet dependency /Users/g-hayakawa/repos/presen0424/node_modules/grunt/node_modules/lodash,
npm WARN unmet dependency which is version 0.9.2
npm WARN unmet dependency /Users/g-hayakawa/repos/presen0424/node_modules/grunt/node_modules/grunt-legacy-log requires underscore.string@'~2.3.3' but will load
npm WARN unmet dependency /Users/g-hayakawa/repos/presen0424/node_modules/grunt/node_modules/underscore.string,
npm WARN unmet dependency which is version 2.2.1
npm WARN unmet dependency /Users/g-hayakawa/repos/presen0424/node_modules/grunt-contrib-watch/node_modules/gaze/node_modules/globule requires lodash@'~1.0.1' but will load
npm WARN unmet dependency /Users/g-hayakawa/repos/presen0424/node_modules/grunt-contrib-watch/node_modules/lodash,
npm WARN unmet dependency which is version 2.4.1
grunt-contrib-copy@0.7.0 node_modules/grunt-contrib-copy
└── chalk@0.5.1 (ansi-styles@1.1.0, escape-string-regexp@1.0.3, supports-color@0.2.0, strip-ansi@0.3.0, has-ansi@0.1.0)
grunt-contrib-watch@0.6.1 node_modules/grunt-contrib-watch
├── async@0.2.10
├── tiny-lr-fork@0.0.5 (debug@0.7.4, faye-websocket@0.4.4, noptify@0.0.3, qs@0.5.6)
├── gaze@0.5.1 (globule@0.1.0)
└── lodash@2.4.1
load-grunt-tasks@1.0.0 node_modules/load-grunt-tasks
├── multimatch@1.0.1 (array-differ@1.0.0, array-union@1.0.1, minimatch@1.0.0)
└── findup-sync@0.1.3 (glob@3.2.11, lodash@2.4.1)
grunt-contrib-connect@0.9.0 node_modules/grunt-contrib-connect
├── opn@1.0.1
├── connect-livereload@0.5.3
├── async@0.9.0
├── portscanner@1.0.0 (async@0.1.15)
└── connect@2.29.1 (utils-merge@1.0.0, cookie-signature@1.0.6, fresh@0.2.4, pause@0.0.1, cookie@0.1.2, response-time@2.3.0, content-type@1.0.1, basic-auth-connect@1.0.0, on-headers@1.0.0, vhost@3.0.0, parseurl@1.3.0, cookie-parser@1.3.4, bytes@1.0.0, depd@1.0.1, connect-timeout@1.6.1, http-errors@1.3.1, method-override@2.3.2, qs@2.4.1, debug@2.1.3, finalhandler@0.3.4, morgan@1.5.2, serve-favicon@2.2.0, express-session@1.10.4, csurf@1.7.0, type-is@1.6.1, serve-static@1.9.2, compression@1.4.3, errorhandler@1.3.5, multiparty@3.3.2, body-parser@1.12.3, serve-index@1.6.3)
grunt@0.4.5 node_modules/grunt
├── which@1.0.9
├── dateformat@1.0.2-1.2.3
├── eventemitter2@0.4.14
├── getobject@0.1.0
├── rimraf@2.2.8
├── colors@0.6.2
├── async@0.1.22
├── grunt-legacy-util@0.2.0
├── hooker@0.2.3
├── exit@0.1.2
├── nopt@1.0.10 (abbrev@1.0.5)
├── minimatch@0.2.14 (sigmund@1.0.0, lru-cache@2.6.1)
├── glob@3.1.21 (inherits@1.0.0, graceful-fs@1.2.3)
├── lodash@0.9.2
├── coffee-script@1.3.3
├── underscore.string@2.2.1
├── iconv-lite@0.2.11
├── findup-sync@0.1.3 (glob@3.2.11, lodash@2.4.1)
├── grunt-legacy-log@0.1.1 (underscore.string@2.3.3, lodash@2.4.1)
└── js-yaml@2.0.5 (argparse@0.1.16, esprima@1.0.4)
coffeelint@1.9.3 node_modules/coffeelint
├── ignore@2.2.15
├── resolve@0.6.3
├── optimist@0.6.1 (wordwrap@0.0.2, minimist@0.0.10)
├── coffee-script@1.9.2
└── glob@4.5.3 (inherits@2.0.1, inflight@1.0.4, once@1.3.1, minimatch@2.0.4)

grunt-coffeelint@0.0.13 node_modules/grunt-coffeelint
└── coffeelint-stylish@0.1.2 (text-table@0.2.0, chalk@1.0.0)
grunt-contrib-jshint@0.10.0 node_modules/grunt-contrib-jshint
├── hooker@0.2.3
└── jshint@2.5.11 (strip-json-comments@1.0.2, underscore@1.6.0, exit@0.1.2, console-browserify@1.1.0, minimatch@1.0.0, shelljs@0.3.0, cli@0.6.6, htmlparser2@3.8.2)


$ npm install -g grunt-cli

/usr/local/bin/grunt -> /usr/local/lib/node_modules/grunt-cli/bin/grunt
npm WARN unmet dependency /usr/local/lib/node_modules/titanium/node_modules/winston requires colors@'0.x.x' but will load
npm WARN unmet dependency /usr/local/lib/node_modules/titanium/node_modules/colors,
npm WARN unmet dependency which is version 0.6.0-1
grunt-cli@0.1.13 /usr/local/lib/node_modules/grunt-cli
├── resolve@0.3.1
├── nopt@1.0.10 (abbrev@1.0.5)
└── findup-sync@0.1.3 (glob@3.2.11, lodash@2.4.1)


$ which npm
/usr/local/bin/npm



$ /usr/local/share/npm/bin/grunt -version



lsbom -f -l -s -pf /var/db/receipts/org.nodejs.pkg.bom | while read f; do  sudo rm /usr/local/${f}; done
sudo rm -rf /usr/local/lib/node /usr/local/lib/node_modules /var/db/receipts/org.nodejs.*

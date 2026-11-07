<div align="center">

![[logo.png]]

<p>一款面向 <a href="https://github.com/ZToolsCenter/ZTools">ZTools</a> / <a href="https://www.u-tools.cn/index.html">uTools</a> 插件：编码转换、哈希、JWT 解析、古典密码，以及公开 Payload 速查。</p>

<p>仅用于 CTF、本地靶场和<strong>已获得书面授权</strong>的安全测试。</p>

</div>

## 功能

- 编码 / 解码：Base64、Base64URL、Base32、Base58、Hex、URL、HTML 实体、Unicode、二进制、Quoted-Printable、ROT13、Caesar、Morse

![[images/t1.png]]
![[images/t2.png]]
- MD5 / SHA1 / SHA256 / SHA512，可选 HMAC-SHA256
![[images/t3.png]]
- JWT Header / Payload 解析，none / HS256·384·512 / RS256·384·512 伪造签名（含弱密钥、算法混淆）
![[images/t4.png]]
- 古典密码：Caesar、ROT13、栅栏
![[images/t5.png]]
- PHP 绕过构造（独立栏目）：输入函数名，即时生成取反 / 异或 / 或 / 自增
![[images/t6.png]]
- Payload 速查：PHP 伪协议、LFI、XSS、SSTI、SQLi、XXE、SSRF、上传绕过
![[images/t7.png]]


## 开始

### 安装
#### 方法一 在插件市场安装
在 ZTools 或 UTools 插件市场搜索网安 CTF 工具箱，下载即可

![[images/s1.png]]

#### 方式二 在 releases 下载已经打包好的插件包安装
在 [releases][https://github.com/LightPolarisCN/ctf-toolbox-web/releases] 下载插件包，下载好后点击导入本地插件

![[images/s2.png]]

选择下载的插件包，点击安装即可
![[images/s3.png]]

### 方式三：手动编译插件包

```bash
# 1. 进入插件目录
cd ctf-toolbox-web

# 2. 语法检查（无输出即通过）
node --check codec.js && node --check app.js && node --check preload.js

# 3. 打包，版本号取自 plugin.json
VERSION=$(node -p "require('./plugin.json').version")
zip -r "../ctf-toolbox-${VERSION}.zip" \
  plugin.json preload.js index.html styles.css app.js codec.js payloads.js logo.png \
  -x '*.DS_Store' '*__MACOSX*'

# 4. 查看包内容，确认第一层是 plugin.json
unzip -l "../ctf-toolbox-${VERSION}.zip"
```

## 目录

```
ctf-toolbox/
├── plugin.json
├── preload.js
├── index.html
├── styles.css
├── app.js
├── codec.js
├── payloads.js
├── logo.png
├── ASSETS.md
├── LICENSE
└── README.md
```

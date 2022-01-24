# PukiWiki用スキン<br>イカスキン ika.skin.php

次の特長を持つ[PukiWiki](https://pukiwiki.osdn.jp/)用スキン。

- **シンプル**  
伝統的なウィキスタイルを継承しつつ、装飾や色彩を抑えたすっきりデザイン
- **レスポンシブ**  
ウィンドウサイズに適応し、モバイル端末の狭い画面にも対応
- **ダークモード対応**  
ライトテーマとダークテーマを備え、OSのカラースキームに応じた自動切り替えも可能
- **簡単カスタマイズ**  
本文領域の幅・文字サイズ・行間隔・禁則有無などを、CSSに触れずに変更できる

<br>

<img src="https://user-images.githubusercontent.com/3040830/150863805-43c287d7-e0df-4ac7-ba74-e3a4a0be6ab5.png" width="425"/>

<br>

|対象PukiWikiバージョン|対象PHPバージョン|
|:---:|:---:|
|PukiWiki 1.5.3 ~ 1.5.4RC (UTF-8)|PHP 7.4 ~ 8.1|
<br>

**ご注意**  
Internet Explorer（IE）およびレガシーブラウザーには対応しておらず、対応予定もありません。  
非対応ブラウザーでは表示が著しく乱れてしまうため、レガシーブラウザーでのアクセスが多く見込まれるサイトには向いていません。

<br>

## インストール

ika.skin.php を PukiWiki の skin ディレクトリに配置してください。

次に、PukiWiki ルートディレクトリにある設定ファイル default.ini.php を開き、冒頭の SKIN_FILE 定義を下記のように書き換えてください。

```
/////////////////////////////////////////////////
// Skin file

if (defined('TDIARY_THEME')) {
	define('SKIN_FILE', DATA_HOME . SKIN_DIR . 'tdiary.skin.php');
} else {
	// define('SKIN_FILE', DATA_HOME . SKIN_DIR . 'pukiwiki.skin.php'); // 行頭に「//」をつけて標準スキンを無効に
	define('SKIN_FILE', DATA_HOME . SKIN_DIR . 'ika.skin.php'); // 代わりにイカスキンを設定
}
```

以上で完了です。  
ブラウザーで PukiWiki の画面を開くと、見た目が変わっているはずです（変わらない場合はキャッシュをクリアしてみてください）。  
標準スキンに戻したいときは、この定義を元に戻してください。

<br>

## カスタマイズ

PukiWiki ルートディレクトリにある設定ファイル default.ini.php を開き、末尾に下記のコードを追記（コピー＆ペースト）してください。

```
/////////////////////////////////////////////////
// イカスキン ika.skin.php 設定
define('IKASKIN_TITLE',             0); // ヘッダータイトル（0:ページ名, 1:ウィキ名）
define('IKASKIN_THEME',             0); // カラーテーマ（0:ライト, 1:ダーク, 2:OS設定に自動適応）
define('IKASKIN_LINKCOLOR_LIGHT',  ''); // ライトテーマのリンク色（例：'#0000ff'）
define('IKASKIN_LINKCOLOR_DARK',   ''); // ダークテーマのリンク色（例：'#0000ff'）
define('IKASKIN_SHOW_LASTMODIFIED', 0); // 最終更新日時を表示（0:No, 1:Yes）
define('IKASKIN_FONT_SIZE',         0); // 文字サイズ（px単位, 0:デフォルト）
define('IKASKIN_LINE_HEIGHT',       0); // 行の高さ（em単位, 0:デフォルト）
define('IKASKIN_MENU_WIDTH',        0); // メニューバーの幅（px単位, 0:デフォルト）
define('IKASKIN_BODY_WIDTH',        0); // ページ本文の幅（px単位, 0:デフォルト）
define('IKASKIN_WORDWRAP',          1); // 改行規則（0:禁則なし, 1:禁則あり）
define('IKASKIN_SIMPLIFY',          0); // シンプル表示（0:No, 1:Yes）
define('IKASKIN_COPYRIGHT',         0); // 管理人名の接頭辞（0:"Site admin", 1:"©"）
define('IKASKIN_MENU_ORDER',        0); // メニューバーの表示順序（0:MenuBar→本文→RightBar, 1:RightBar→本文→MenuBar）
define('IKASKIN_LOGO',             ''); // サイトロゴ画像パス（例：'image/pukiwiki.png'）
define('IKASKIN_FAVICON',          ''); // ファビコン画像パス（例：'/favicon.ico'）
define('IKASKIN_APPLETOUCHICON',   ''); // 180×180px PNGアイコン画像パス（例：'apple-touch-icon.png'）
define('IKASKIN_CSS',              ''); // CSSファイルパス（例：'mystyle.css'）
define('IKASKIN_DISUSE_MAINJS',     0); // main.js不使用（0:No, 1:Yes）
define('IKASKIN_DISUSE_SEARCH2JS',  0); // search2.js不使用（0:No, 1:Yes）
```

左の「IKASKIN_○○」が設定項目、カンマの後の ’’ や 0 が設定値です。右側には項目の説明コメントがあります。

変更したい項目の値を説明に基づいて書き換えます。  
ファイル名などの文字列は必ず半角クォーテーション（「'」か「"」）で囲んでください。

たとえば、文字の大きさを変更したければ「IKASIKIN_FONT_SIZE」の値を「16」などとします。  
サイトロゴのファイルを指定したければ「IKASKIN_LOGO」の値を「'pukiwiki.png'」などとします。  
変更の必要のない項目はそのままで構いません。

設定は即座に反映されます。  
値を変更してセーブしたら、ブラウザーで PukiWiki の画面をリロードしてください。  
書き方や内容を誤るとエラーが発生したり、効果が表れなかったりします。  
どれが原因かわかりにくくならないよう、一項目ずつ、画面の変化を確かめながら変更するとよいでしょう。

なお、default.ini.php は PukiWiki 標準の設定ファイルの一つ（厳密にいえば pukiwiki.ini.php で指定されている既定プロファイル）で、その他の各種動作も設定することができます。  
詳しくはファイル内のコメントや PukiWiki 公式サイトをご確認ください。  
デフォルトでは一般に不要と思われる高負荷な処理や表示も有効になっているため、ご自分のサイトでの必要やお好みに応じて設定し直すことを勧めます。

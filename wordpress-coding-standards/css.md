<!-- 
# CSS Coding Standards
 -->
# CSS コーディング規約

<!-- 
Like any coding standard, the purpose of the WordPress CSS Coding Standards is to create a baseline for collaboration and review within various aspects of the WordPress open source project and community, from core code to themes to plugins. Files within a project should appear as though created by a single entity. Above all else, create code that is readable, meaningful, consistent, and beautiful.

Within core stylesheets, inconsistencies will often be found. We are working on addressing these and make every effort to have patches and commits from this point forward follow the CSS coding standards. More information on the above and contributing to UI/front-end development will be forthcoming in a separate set of guidelines.
 -->
他のコーディング規約同様「WordPress CSS コーディング規約」も WordPress オープンソースプロジェクトおよびコミュニティでのコラボレーションやレビューのベースラインであり、その適用範囲はコアコードからテーマ、プラグインに至ります。プロジェクト内のすべてのファイルが一人のプログラマーが開発したかのように見える必要があります。読みやすく、意味のある、一貫した美しいコードを目標にしてください。

コアのスタイルシートの中にはコーディングスタイルに合致しないものがいくつかあります。WordPress ではこれらに対処するため、CSS コーディング規約に従ったパッチやコミットになるよう努めています。なお、本ガイドの適用範囲を超える詳細情報、および UI やフロントエンド開発への貢献については、別のガイドラインを作成予定です。

<!-- 
## Structure
 -->
## 構造

<!-- 
There are plenty of different methods for structuring a stylesheet. With the CSS in core, it is important to retain a high degree of legibility. This enables subsequent contributors to have a clear understanding of the flow of the document.

- Use tabs, not spaces, to indent each property.
- Add two blank lines between sections and one blank line between blocks in a section.
- Each selector should be on its own line, ending in either a comma or an opening curly brace. Property-value pairs should be on their own line, with one tab of indentation and an ending semicolon. The closing brace should be flush left, using the same level of indentation as the opening selector.
 -->
スタイルシートの構造化については多くの方法があります。このうちコアの CSS では読みやすさが何よりも重要です。読みやすい CSS であれば、他のコントリビューターもドキュメントの流れをクリアに理解できます。

- インデントはタブです。各プロパティのインデントにはスペースでなく、タブを使用してください。
- セクションとセクションの間には空白行を2行挿入してください。セクション内のブロック間には空白行を1行挿入してください。
- セレクタは1行に1つ書き、行末はコンマ、または開始の波括弧「{」で終えてください。プロパティと値のセットも1行ずつ書き、1つのタブでインデントして始め、セミコロンで終えます。終了の波括弧「}」は改行した新しい行に、開始の波括弧と同じインデントレベルで書きます。

<!-- 
Correct:
 -->
正しい:

```css
#selector-1,
#selector-2,
#selector-3 {
	background: #fff;
	color: #000;
}
```

<!-- 
Incorrect:
 -->
間違い:

```css
#selector-1, #selector-2, #selector-3 {
	background: #fff;
	color: #000;
	}

#selector-1 { background: #fff; color: #000; }
```
<!-- 
## Selectors
 -->
## セレクタ

<!-- 
With specificity, comes great responsibility. Broad selectors allow us to be efficient, yet can have adverse consequences if not tested. Location-specific selectors can save us time, but will quickly lead to a cluttered stylesheet. Exercise your best judgement to create selectors that find the right balance between contributing to the overall style and layout of the DOM.

- Similar to the [WordPress PHP Coding Standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/php/#naming-conventions) for file names, use lowercase and separate words with hyphens when naming selectors. Avoid camelcase and underscores.
- Use human readable selectors that describe what element(s) they style.
- Attribute selectors should use double quotes around values.
- Refrain from using over-qualified selectors, `div.container` can simply be stated as `.container`.
 -->
セレクタの詳細度には、責任が伴います。スコープの広いセレクタを使用すれば効率的ですが、テストが十分でないと逆の結果になるでしょう。局所的なセレクタを使用すると時間の節約にはなりますが、すぐに混乱したスタイルシートが生まれるでしょう。最大限の判断力を駆使し、スタイル全体への貢献と DOM のレイアウトとの間で正しいバランスを取ったセレクタを作成してください。

- セレクタの命名では「[WordPress PHP コーディング規約](https://ja.wordpress.org/team/handbook/coding-standards/wordpress-coding-standards/html/)」のファイル名の命名規則と同じく、小文字の英単語をハイフンでつないでください。キャメルケースやアンダースコアは禁止です。
- 対象の要素を表した、人間が読んで分かるセレクタ名を使用してください。
- 属性セレクタは、値の前後にダブルクオートを使用してください。
- 過剰に修飾したセレクタを使用しないでください。例えば「div.container」は単純に「.container」と書けます。

<!-- 
Correct:
 -->
正しい:

```css
#comment-form {
	margin: 1em 0;
}

input[type="text"] {
	line-height: 1.1;
}
```

<!-- 
Incorrect:
 -->
間違い:

<!-- 
```css
#commentForm { /&042; Avoid camelcase. &042;/
	margin: 0;
}

#comment_form { /&042; Avoid underscores. &042;/
	margin: 0;
}

div#comment_form { /&042; Avoid over-qualification. &042;/
	margin: 0;
}

#c1-xr { /&042; What is a c1-xr?! Use a better name. &042;/
	margin: 0;
}

input[type=text] { /&042; Should be [type="text"] &042;/
	line-height: 110% /&042; Also doubly incorrect &042;/
}
```
 -->
```css
#commentForm { /* キャメルケースは使わない */
    margin: 0;
}
 
#comment_form { /* アンダースコアは使わない */
    margin: 0;
}
 
div#comment_form { /* 過剰に修飾しない */
    margin: 0;
}
 
#c1-xr { /* 「c1-xr」って何?! もっとよい名前があるはず */
    margin: 0;
}
 
input[type=text] { /* [type="text"] とすべき */
    line-height: 110% /* 二重に間違い */
}
```

<!-- 
## Properties
 -->
## プロパティ

<!-- 
Similar to selectors, properties that are too specific will hinder the flexibility of the design. Less is more. Make sure you are not repeating styling or introducing fixed dimensions (when a fluid solution is more acceptable).

- Properties should be followed by a colon and a space.
- All properties and values should be lowercase, except for font names and vendor-specific properties.
- Use hex code for colors, or `rgba()` if opacity is needed. Avoid RGB format and uppercase, and shorten values when possible: `#fff` instead of `#FFFFFF`.
- Use shorthand, except when overriding styles, for `background`, `border`, `font`, `list-style`, `margin`, and `padding` values as much as possible. For a shorthand reference, see [CSS Shorthand](https://codex.wordpress.org/CSS_Shorthand).

 -->
セレクタと同様プロパティも細かすぎるとデザインの柔軟性を損ないます。少ないに越したことはありません。またスタイルを繰り返したり、固定のサイズを指定しないでください。相対値で指定する、流動的なソリューションを推奨します。

- プロパティの後にはコロンとスペースを置いてください。
- すべてのプロパティと値は小文字です。例外はフォント名とベンダー固有のプロパティです。
- 色は16進コード、opacity が必要であれば rgba() を使用してください。RGB フォーマット、大文字は避けてください。可能であれば値は縮めてください。例えば #FFFFFF ではなく #fff。
- スタイルを上書きする場合を除き、可能な限りショートハンド (短縮形) を使用してください。「background」「border」「font」「list-style」「margin」「padding」。ショートハンドの詳細については「[CSS Shorthand](https://codex.wordpress.org/CSS_Shorthand)」を参照してください。

<!-- 

Correct:
 -->
正しい:

```css
#selector-1 {
	background: #fff;
	display: block;
	margin: 0;
	margin-left: 20px;
}
```

<!-- 
Incorrect:
 -->
間違い:

```css
#selector-1 {
	background:#FFFFFF;
	display: BLOCK;
	margin-left: 20PX;
	margin: 0;
}
```
<!-- 
### Property Ordering
 -->
### プロパティの順序

<!-- 
> "Group like properties together, especially if you have a lot of them." 
> -- Nacin
 -->
> "プロパティは、特に数が多い場合、グループにしてください。"
> -- Nacin

<!-- 
Above all else, choose something that is meaningful to you and semantic in some way. Random ordering is chaos, not poetry. In WordPress Core, our choice is logical or grouped ordering, wherein properties are grouped by meaning and ordered specifically within those groups. The properties within groups are also strategically ordered to create transitions between sections, such as `background` directly before `color`. The baseline for ordering is:

- Display
- Positioning
- Box model
- Colors and Typography
- Other

Things that are not yet used in core itself, such as CSS3 animations, may not have a prescribed place above but likely would fit into one of the above in a logical manner. Just as CSS is evolving, so our standards will evolve with it.

Top/Right/Bottom/Left (TRBL/trouble) should be the order for any relevant properties (e.g. `margin`), much as the order goes in values. Corner specifiers (e.g. `border-radius-*-*`) should be ordered as top-left, top-right, bottom-right, bottom-left. This is derived from how shorthand values would be ordered.
 -->
最低限、何らかの意味のある方法を使用してグループ化してください。ランダムな順番はカオスであり、詩的ではありません。WordPress コアの中では、論理的にグループ化した順序を採用しています。プロパティは意味でグループ化され、グループ内で順番に並べられます。グループ内のプロパティもセクション間で流れができるよう並べられます。たとえば background は color の直前です。順序の基準は以下のとおりです。

- 画面
- 位置
- ボックスモデル
- 色とフォント
- その他

コア内部で未使用の、例えば CSS3 animation などは上の順序に規定されていませんが、論理的な方法でどこかには挿入できるはずです。CSS が進化するように、この規約も進化します。

「margin」 などの関連するプロパティ、対応する値の順序についてはTop/Right/Bottom/Left の順序 (TRBL「トラブル」と覚える) を使用してください。「border-radius-*-*」などの四隅の指定の順番は「top-left」「top-right」「bottom-right」「bottom-left」の順番です。これはショートハンドの指定順から来ています。

<!-- 
Example:
 -->
例:

```css
#overlay {
	position: absolute;
	z-index: 1;
	padding: 10px;
	background: #fff;
	color: #777;
}
```

<!-- 
Another method that is often used, including by the Automattic/WordPress.com Themes Team, is to order properties alphabetically, with or without certain exceptions.
 -->
別の方法は Automattic や WordPress.com テーマチームを含む多くのグループで採用されている、例外のあるなしに関係なくアルファベット順にプロパティを並べる方法です。

<!-- 
Example:
 -->
例:

```css
#overlay {
	background: #fff;
	color: #777;
	padding: 10px;
	position: absolute;
	z-index: 1;
}
```
<!-- 
### Vendor Prefixes
 -->
### ベンダープレフィックス

<!-- 
Updated on 2014-02-13, after [[27174](https://core.trac.wordpress.org/changeset/27174)]:

We use [Autoprefixer](https://github.com/postcss/autoprefixer) as a pre-commit tool to easily manage necessary browser prefixes, thus making the majority of this section moot. For those interested in following that output without using Grunt, vendor prefixes should go longest (-webkit-) to shortest (unprefixed). All other spacing remains as per the rest of the standards.
 -->
2014年2月13日、[27174](https://core.trac.wordpress.org/changeset/27174) 後に更新。

ブラウザー固有のベンダープレフィックスを簡単に管理するプレコミットツールとして WordPress では [Autoprefixer](https://github.com/postcss/autoprefixer) を使用します。この結果、本節の大部分の議論は過去のものとなりました。Grunt を使わずに自力で出力と合わせる場合、ベンダープレフィックスは長いもの (「-webkit-」) から短いもの (プレフィックスなし) の順番で配置してください。その他は、規約の他の部分に準拠します。

```css
.sample-output {
	-webkit-box-shadow: inset 0 0 1px 1px #eee;
	-moz-box-shadow: inset 0 0 1px 1px #eee;
	box-shadow: inset 0 0 1px 1px #eee;
}
```
<!-- 
## Values
 -->
## 値

<!-- 
There are numerous ways to input values for properties. Follow the guidelines below to help us retain a high degree of consistency.

- Space before the value, after the colon.
- Do not pad parentheses with spaces.
- Always end in a semicolon.
- Use double quotes rather than single quotes, and only when needed, such as when a font name has a space or for the values of the `content` property.
- Font weights should be defined using numeric values (e.g. `400` instead of `normal`, `700` rather than `bold`).
- 0 values should not have units unless necessary, such as with `transition-duration`.
- Line height should also be unit-less, unless necessary to be defined as a specific pixel value. This is more than just a style convention, but is worth mentioning here. More information: <https://meyerweb.com/eric/thoughts/2006/02/08/unitless-line-heights/>.
- Use a leading zero for decimal values, including in `rgba()`.
- Multiple comma-separated values for one property should be separated by either a space or a newline. For better readability newlines should be used for lengthier multi-part values such as those for shorthand properties like `box-shadow` and `text-shadow`, including before the first value. Values should then be indented one level in from the property.
- Lists of values within a value, like within `rgba()`, should be separated by a space.
 -->
プロパティへの値の入力には多くの方法があります。一貫性を高く保つため次のガイドに従ってください。

- 値の前、コロンの後にはスペースを置きます。
- 括弧にスペースを含めません。
- 常にセミコロンで終えます。
- シングルクオートでなくダブルクオートを、フォント名にスペースが含まれる場合など必要な場合のみ使用します。
- フォントのウエイトは数値を使用して定義します (例: 「normal」でなく「400」を、「bold」でなく「700」を使用します)。
- 「0」に単位を付けません。transition-duration など必要な場合のみ付けます。
- 特定のピクセル値が必要でなければ、行の高さにも単位は付けません。これには単なるスタイルのルールを越えた意味があります。詳細: http://meyerweb.com/eric/thoughts/2006/02/08/unitless-line-heights/
- rgba() の中も含め、小数値には先頭の「0」を付けます。
- 1つのプロパティに複数の値をコンマ区切りで指定する場合、rgba() の中も含め、スペースまたは改行を挿入します。ただし box-shadow や text-shadow のショートハンドプロパティのような非常に長い複数パーツについては、改行を使用します。2番目以降の値は、それぞれ前の値から改行し、セレクタおよび続くスペースの分をインデントし、前の値と同じレベルにします。
- `rgba()`の中のように、値の中の値のリストは、スペースで区切ってください。

<!-- 
Correct:
 -->
正しい:

<!-- 
```css
.class { /&042; Correct usage of quotes &042;/
	background-image: url(images/bg.png);
	font-family: "Helvetica Neue", sans-serif;
	font-weight: 700;
}

.class { /&042; Correct usage of zero values &042;/
	font-family: Georgia, serif;
	line-height: 1.4;
	text-shadow:
		0 -1px 0 rgba(0, 0, 0, 0.5),
		0 1px 0 #fff;
}

.class { /&042; Correct usage of short and lengthier multi-part values &042;/
	font-family: Consolas, Monaco, monospace;
	transition-property: opacity, background, color;
	box-shadow:
		0 0 0 1px #5b9dd9,
		0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```
 -->
```css
.class { /* クオートの正しい用法 */
	background-image: url(images/bg.png);
	font-family: "Helvetica Neue", sans-serif;
	font-weight: 700;
}

.class { /* 値「0」の正しい用法 */
	font-family: Georgia, serif;
	line-height: 1.4;
	text-shadow:
		0 -1px 0 rgba(0, 0, 0, 0.5),
		0 1px 0 #fff;
}

.class { /* 複数パーツの短い形式、長い形式の正しい用法 */
	font-family: Consolas, Monaco, monospace;
	transition-property: opacity, background, color;
	box-shadow:
		0 0 0 1px #5b9dd9,
		0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```


<!-- 
Incorrect:
 -->
間違い:

<!-- 
```css
.class { /&042; Avoid missing space and semicolon &042;/
	background:#fff
}

.class { /&042; Avoid adding a unit on a zero value &042;/
	margin: 0px 0px 20px 0px;
}

.class {
	font-family: Times New Roman, serif; /&042; Quote font names when required &042;/
	font-weight: bold; /&042; Avoid named font weights &042;/
	line-height: 1.4em; /&042; Avoid adding a unit for line height &042;/
}

.class { /&042; Incorrect usage of multi-part values &042;/
	text-shadow: 0 1px 0 rgba(0, 0, 0, 0.5),
                 0 1px 0 #fff;
	box-shadow: 0 1px 0 rgba(0, 0,
		0, 0.5),
		0 1px 0 rgba(0,0,0,0.5);
}
```
 -->
```css
.class { /* スペースとセミコロンを忘れない */
	background:#fff
}

.class { /* 値「0」に単位を付けない */
	margin: 0px 0px 20px 0px;
}

.class {
	font-family: Times New Roman, serif; /* 必要であればフォント名はクォートで囲む */
	font-weight: bold; /* フォントウェイト名は避ける */
	line-height: 1.4em; /* line-height に単位を付けない */
}

.class { /* 複数パーツの誤った用法 */
	text-shadow: 0 1px 0 rgba(0, 0, 0, 0.5),
                 0 1px 0 #fff;
	box-shadow: 0 1px 0 rgba(0, 0,
		0, 0.5),
		0 1px 0 rgba(0,0,0,0.5);
}
```
<!-- 
## Media Queries
 -->
## メディアクエリ

<!-- 
Media queries allow us to gracefully degrade the DOM for different screen sizes. If you are adding any, be sure to test above and below the break-point you are targeting.

- It is generally advisable to keep media queries grouped by media at the bottom of the stylesheet.
    - An exception is made for the `wp-admin.css` file in core, as it is very large and each section essentially represents a stylesheet of its own. Media queries are therefore added at the bottom of sections as applicable.
- Rule sets for media queries should be indented one level in.

 -->
メディアクエリを使用すると異なる画面サイズごとに DOM を分解できます。メディアクエリを追加する場合は対象のブレークポイントの前後で正しく動作することをテスト指定ください。

- 一般にメディアごとにメディアクエリをグループ化し、スタイルシート末尾に配置することが推奨されます。
  - 例外はコアの wp-admin.css ファイルで、ファイルサイズが大きく、各セクションは実質的に自身のスタイルシートを表しているためメディアクエリは適切なセクションの末尾に追加されています。
- メディアクエリのルールセットは1レベル分インデントします。

<!-- 
Example:
 -->
例:

<!-- 
```css
@media all and (max-width: 699px) and (min-width: 520px) {
        /* Your selectors */
}
```
 -->
```css
@media all and (max-width: 699px) and (min-width: 520px) {
        /* あなたのセレクタ */
}
```

<!-- 
## Commenting
 -->
## コメント

<!-- 
- Comment, and comment liberally. If there are concerns about file size, utilize minified files and the `SCRIPT_DEBUG` constant. Long comments should manually break the line length at 80 characters.
- A table of contents should be utilized for longer stylesheets, especially those that are highly sectioned. Using an index number (`1.0`, `1.1`, `2.0`, etc.) aids in searching and jumping to a location.
- Comments should be formatted much as PHPDoc is. The [CSSDoc](https://web.archive.org/web/20070601200419/http://cssdoc.net/) standard is not necessarily widely accepted or used but some aspects of it may be adopted over time. Section/subsection headers should have newlines before and after. Inline comments should not have empty newlines separating the comment from the item to which it relates.
 -->
- コメントを書いてください。大量に書いてください。ファイルサイズが気になるならミニファイと SCRIPT_DEBUG 定数を使用します。長いコメントは80文字で改行します。
- 巨大なスタイルシート、特に複数のセクションがあるものには目次をつけます。見出し番号 (1.0、1.1、2.0等) を付けると検索しやすくなります。
- コメントはできる限り PHPDoc 風にフォーマットします。[CSSDoc](http://web.archive.org/web/20070601200419/http://cssdoc.net/) 標準はまだ広く受け入れられていません。ただし、いずれは浸透するかもしれません。セクション、サブセクションのヘッダーは前後に空白行を挿入します。インラインコメントは対象の項目のすぐ上の行に書き、空白行を挟みません。
<!-- 
For sections and subsections:
 -->
セクションおよびサブセクション:

<!-- 
```css
/**
 * #.# Section title
 *
 * Description of section, whether or not it has media queries, etc.
 */

.selector {
	float: left;
}
```
 -->
```css
/**
 * #.# セクションのタイトル
 *
 * セクションの説明。メディアクエリを持つかどうかなど
 */

.selector {
	float: left;
}
```

<!-- 
For inline:
 -->
インライン:

<!-- 
```css
/* This is a comment about this selector */
.another-selector {
	position: absolute;
	top: 0 !important; /* I should explain why this is so !important */
}
```
 -->
```css
/* セレクタのコメントをここに書く */
.another-selector {
	position: absolute;
	top: 0 !important; /* なぜ !important なのか説明する */
}
```
<!-- 
## Best Practices
 -->
## ベストプラクティス

<!-- 
Stylesheets tend to grow in length and complexity, and as they grow the chance of redundancy increases. By following some best practices we can help our CSS maintain focus and flexibility as it evolves:
 -->
スタイルシートは長く、複雑になりがちで、長くなればなるほど、冗長になる可能性が高くなります。以下のベストプラクティスに従うことで、本質を外さず、柔軟に CSS を管理できます。

<!-- 
- If you are attempting to fix an issue, attempt to remove code before adding more.
- Magic Numbers are unlucky. These are numbers that are used as quick fixes on a one-off basis. Example: `.box { margin-top: 37px }`.
- DOM will change over time, target the element you want to use as opposed to "finding it" through its parents. Example: Use `.highlight` on the element as opposed to `.highlight a` (where the selector is on the parent)
- Know when to use the `height` property. It should be used when you are including outside elements (such as images). Otherwise use `line-height` for more flexibility.
- Do not restate default property and value combinations (for instance `display: block;` on block-level elements).
 -->
- 問題を修正する場合、追加する前に削除することを考えます。
- マジックナンバーは不幸です。マジックナンバーとはその場限りの修正用の数字のことです。例: `.box { margin-top: 37px }`
- DOM は時間と共に変わるため、親から「たどって探す」のではなく使用する要素を設定します。例: セレクタが親にある場合、`.highlight a` ではなく、要素の `.highlight` を使用します
- height プロパティをいつ使用すべきかを熟知してください。すなわち画像のような外部の要素を含める場合に使用します。それ以外であれば line-height の方がより柔軟です。
- デフォルトのプロパティと値のペアを再宣言しないでください。たとえばブロックレベル要素の `display: block;`。

### WP Admin CSS

<!-- 
Check out the [WP Admin CSS Audit](https://wordpress.github.io/css-audit/public/wp-admin), a report generated to document the health of the WP Admin CSS code. Read more in [the repository's README](https://github.com/WordPress/css-audit/blob/trunk/README.md).
 -->
[WP Admin CSS Audit](https://wordpress.github.io/css-audit/public/wp-admin) を確認してください。これは WP Admin CSS コードの健康状態を文書化するために生成されたレポートです。詳細については[リポジトリの README](https://github.com/WordPress/css-audit/blob/trunk/README.md) を参照してください。

<!-- 
## Related Links
 -->
## 関連リンク
<!-- 
- Principles of writing consistent, idiomatic CSS: [https://github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css).
 -->
- Principles of writing consistent, idiomatic CSS: https://github.com/necolas/idiomatic-css

[原文](https://github.com/WordPress/wpcs-docs/blob/master/wordpress-coding-standards/css.md) / [日本語訳](https://github.com/jawordpressorg/wpcs-docs/blob/master/wordpress-coding-standards/css.md)

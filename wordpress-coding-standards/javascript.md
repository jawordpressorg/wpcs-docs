<!-- 
# JavaScript Coding Standards
 -->
# JavaScript コーディング規約

<!-- 
JavaScript has become a critical component in developing WordPress-based applications (themes and plugins) as well as WordPress core. Standards are needed for formatting and styling JavaScript code to maintain the same code consistency as the WordPress standards provide for core PHP, HTML, and CSS code.

> All code in any code-base should look like a single person typed it, no matter how many people contributed. - [Principles of Writing Consistent, Idiomatic JavaScript](https://github.com/rwaldron/idiomatic.js/)

The WordPress JavaScript Coding Standards are adapted from the [jQuery JavaScript Style Guide](https://contribute.jquery.org/style-guide/js). Our standard differs from the jQuery guidelines in the following ways:

- WordPress uses single quotation marks for string declarations.
- Case statements are indented within switch blocks.
- Function contents are consistently indented, including full-file closure wrappers.
- Some whitespace rules differ, for consistency with the WordPress PHP coding standards.
- jQuery’s 100-character hard line limit is encouraged, but not strictly enforced.

Many of the examples below have been adapted directly from the jQuery style guide; these differences have all been integrated into the examples on this page. Any of the below standards and examples should be considered best practice for WordPress code, unless explicitly noted as anti-patterns.
 -->
今や JavaScript は WordPress コアだけでなく、テーマやプラグインなどの WordPress 周辺のアプリケーションにおいても重要なコンポーネントになっています。既存のコア PHP、HTML、CSS の WordPress 規約と同じレベルでコードの一貫性を保つには、JavaScript コードのフォーマットやスタイルにも規約が必要なことは明らかです。

> 多数のコントリビューターが参加していても、すべてのコードは、一人の人間がコーディングしたかのように見えなければならない
> 
> _Principles of Writing Consistent, Idiomatic JavaScript_

WordPress JavaScript コーディング規約は「jQuery JavaScript Style Guide」を基にしていますが、次の点で異なります。

- WordPress は文字列の宣言にシングルクォートを使用します。
- case 文は switch ブロック内でインデントします。
- 関数全体がクロージャでラップされている場合も含め、関数の本体は常にインデントします。
- WordPress PHP コーディング規約と一貫性を保つため、スペースのルールが一部異なります。
- jQuery の 100文字制限を推奨しますが、厳密には強制しません。

この記事の例は直接「jQuery JavaScript Style Guide」から引用していますが、上で挙げた相違点はすべて反映されています。この記事の規約と例は、特にアンチパターンと明記されているもの以外すべて WordPress JavaScript コーディングにおけるベストプラクティスになっています。

<!-- 
## Code Refactoring
 -->
## コードのリファクタリング

<!-- 
> "[Code refactoring should not be done just because we can.](https://make.wordpress.org/core/2011/03/23/code-refactoring/)" - Lead Developer Andrew Nacin

Many parts of the WordPress code structure for JavaScript are inconsistent in their style. WordPress is working to gradually improve this, so the code will be clean and easy to read at a glance.

While the coding standards are important, refactoring older .js files simply to conform to the standards is not an urgent issue. "Whitespace-only" patches for older files are strongly discouraged.

All new or updated JavaScript code will be reviewed to ensure it conforms to the standards, and passes JSHint.
 -->
> [リファクタリングのためだけにコードを変更しないでください。](https://make.wordpress.org/core/2011/03/23/code-refactoring/)
> 
> _リード開発者 Andrew Nacin_

WordPress の多くの JavaScript コードには統一したスタイルがありません。WordPress では徐々にこれらを改善し、コードをクリーンで読みやすいものにするよう努めています。

コーディング規約は確かに重要ですが、規約に合わせるためだけに古い .js ファイルをリファクタリングするほど暇ではありません。古いファイルの「スペースを調整する」だけのパッチなどは絶対にやめてください。

なお新規に作成、更新された JavaScript コードは、コーディング規約に順守し、JSHint にパスしたことをレビューします。

<!-- 
## Spacing
 -->
## スペース

<!-- 
Use spaces liberally throughout your code. "When in doubt, space it out."

These rules encourage liberal spacing for improved developer readability. The minification process creates a file that is optimized for browsers to read and process.

- Indentation with tabs.
- No whitespace at the end of line or on blank lines.
- Lines should usually be no longer than 80 characters, and should not exceed 100 (counting tabs as 4 spaces). _This is a "soft" rule, but long lines generally indicate unreadable or disorganized code._
- `if`/`else`/`for`/`while`/`try` blocks should always use braces, and always go on multiple lines.
- Unary special-character operators (e.g., `++`, `--`) must not have space next to their operand.
- Any `,` and `;` must not have preceding space.
- Any `;` used as a statement terminator must be at the end of the line.
- Any `:` after a property name in an object definition must not have preceding space.
- The `?` and `:` in a ternary conditional must have space on both sides.
- No filler spaces in empty constructs (e.g., `{}`, `[]`, `fn()`).
- There should be a new line at the end of each file.
- Any `!` negation operator should have a following space.<sup>*</sup>
- All function bodies are indented by one tab, even if the entire file is wrapped in a closure.<sup>*</sup>
- Spaces may align code within documentation blocks or within a line, but only tabs should be used at the start of a line.<sup>*</sup>

<a name="spacing-whitespace">*</a>: The WordPress JavaScript standards prefer slightly broader whitespace rules than the jQuery style guide. These deviations are for consistency between the PHP and JavaScript files in the WordPress codebase.

Whitespace can easily accumulate at the end of a line – avoid this, as trailing whitespace is caught as an error in JSHint. One way to catch whitespace buildup is enabling visible whitespace characters within your text editor.
 -->

スペースはコードの中で自由に使えます。「悩んだら、スペースを入れてください」

十分にスペースが入ることで、開発者はコードが読みやすくなります。仮にファイルサイズが増加しても、後続の縮小プロセスにより不要なスペースは削除され、ブラウザでのロード、処理に最適化したファイルが作成されます。

- 「本物のタブ」でインデントしてください。
- 行末や空行にスペースを入れないでください。
- 1タブを4スペースと数え、1行あたり80文字以下を目標としてください。100文字は越えないでください。これは「強制ではありません」が、一般に長い行は読みにくく、整理されていないコードです。
- if、else、for、while、try ブロックは常にブレース「{}」を使用し、常に複数行にしてください。
- 単項特殊文字演算子 (例: 「++」「–」) はオペランドの次にスペースを入れないでください。
- すべての 「,」および「;」の前にスペースを入れないでください。
- 文の終わりに使用されるすべての「;」は行末に書いてください。
- オブジェクト定義内のプロパティ名と、続く「:」の間にスペースを入れないでください。
- 三項条件の「?」と「:」は両側にスペースを入れてください。
- 空のコンストラクタにスペースを入れないでください。例:「{}」「[]」「fn()」。
- 各ファイルの最後には空行を追加してください。
- すべての否定演算子「!」にはスペースを続けください。(*)
- すべての関数の本体は1つのタブでインデントしてください。関数全体がクロージャでラップされても同様です。(*)
- ドキュメントブロックや行の中でスペースを使用して単語や文の位置を揃えても構いません。ただし行の始まりはタブでインデントしてください。(*)

(*): スペースの扱いに関しては WordPress の JavaScript 規約は「jQuery JavaScript Style Guide」よりも若干広めです。この違いは WordPress コードにおける PHP ファイルと JavaScript ファイルとの一貫性の維持から生じています。

スペースは行末に簡単に紛れ込むため注意してください。JSHint では行末のスペースはエラーです。コーディング中にスペースを見つける方法としては、テキストエディタでスペース文字を表示する方法があります。

<!-- 
### Object Declarations
 -->
### オブジェクト定義

<!-- 
Object declarations can be made on a single line if they are short (remember the line length guidelines). When an object declaration is too long to fit on one line, there must be one property per line. Property names only need to be quoted if they are reserved words or contain special characters:
 -->
オブジェクト定義は、短い場合には1行で書いても構いません。ただし最大長の制限は忘れないでください。オブジェクト定義が長く1行に収まらない場合は、1行ごとに1つのプロパティを定義する形で分割してください。プロパティ名は予約語、または特殊文字を含む場合のみクォートしてください。

オブジェクトや配列は、短い場合には1行で定義しても構いません。ただし最大長の制限は忘れないでください。オブジェクトや配列が長く1行に収まらない場合は、1行ごとに1つのメンバーを定義し、行末はカンマとしてください。

<!-- 
```javascript
// Preferred
var obj = {
	ready: 9,
	when: 4,
	'you are': 15,
};
var arr = [
	9,
	4,
	15,
];

// Acceptable for small objects and arrays
var obj = { ready: 9, when: 4, 'you are': 15 };
var arr = [ 9, 4, 15 ];

// Bad
var obj = { ready: 9,
	when: 4, 'you are': 15 };
var arr = [ 9,
	4, 15 ];
```
 -->

```javascript
// 良い
var obj = {
	ready: 9,
	when: 4,
	'you are': 15,
};
var arr = [
	9,
	4,
	15,
];
 
// 小さなオブジェクトと配列の場合は許される
var obj = { ready: 9, when: 4, 'you are': 15 };
var arr = [ 9, 4, 15 ];
 
// 悪い
var obj = { ready: 9,
	when: 4, 'you are': 15 };
var arr = [ 9,
	4, 15 ];
```
<!-- 
### Arrays and Function Calls
 -->
### 配列と関数呼び出し
<!-- 
Always include extra spaces around elements and arguments:
 -->
要素と引数の前後には常にスペースを入れてください。

```javascript
array = [ a, b ];

foo( arg );

foo( 'string', object );

foo( options, object[ property ] );

foo( node, 'property', 2 );

prop = object[ 'default' ];

firstArrayElement = arr[ 0 ];
```
<!-- 
### Examples of Good Spacing
 -->
### 良いスペースの例

<!-- 
```javascript
var i;

if ( condition ) {
	doSomething( 'with a string' );
} else if ( otherCondition ) {
	otherThing( {
		key: value,
		otherKey: otherValue
	} );
} else {
	somethingElse( true );
}

// Unlike jQuery, WordPress prefers a space after the ! negation operator.
// This is also done to conform to our PHP standards.
while ( ! condition ) {
	iterating++;
}

for ( i = 0; i &lt; 100; i++ ) {
	object[ array[ i ] ] = someFn( i );
	$( '.container' ).val( array[ i ] );
}

try {
	// Expressions
} catch ( e ) {
	// Expressions
}
```
 -->
```javascript
var i;

if ( condition ) {
	doSomething( 'with a string' );
} else if ( otherCondition ) {
	otherThing( {
		key: value,
		otherKey: otherValue
	} );
} else {
	somethingElse( true );
}

// jQuery とは異なり、WordPress では否定演算子 ! の後にスペースを入れます。
// これは PHP 規約との一貫性のためです。
while ( ! condition ) {
	iterating++;
}

for ( i = 0; i < 100; i++ ) {
	object[ array[ i ] ] = someFn( i );
	$( '.container' ).val( array[ i ] );
}

try {
	// 式
} catch ( e ) {
	// 式
}
```
<!-- 
## Semicolons
 -->
## セミコロン
<!-- 
Use them. Never rely on Automatic Semicolon Insertion (ASI).
 -->
セミコロンを使用してください。自動セミコロン挿入 (ASI) に頼らないでください。

<!-- 
## Indentation and Line Breaks
 -->
## インデントと改行

<!-- 
Indentation and line breaks add readability to complex statements.

Tabs should be used for indentation. Even if the entire file is contained in a closure (i.e., an immediately invoked function), the contents of that function should be indented by one tab:
 -->
複雑な文もインデントと改行により読みやすくなります。

インデントにはタブを使用してください。即時実行関数のように、関数全体がクロージャに含まれる場合も関数の内部は1つのタブでインデントしてください。

<!-- 
```javascript
( function ( $ ) {
	// Expressions indented

	function doSomething() {
		// Expressions indented
	}
} )( jQuery );
```
 -->
```javascript
( function ( $ ) {
	// インデントした式

	function doSomething() {
		// インデントした式
	}
} )( jQuery );
```

<!-- 
### Blocks and Curly Braces
 -->
### ブロックとブレース

<!-- 
`if`, `else`, `for`, `while`, and `try` blocks should always use braces, and always go on multiple lines. The opening brace should be on the same line as the function definition, the conditional, or the loop. The closing brace should be on the line directly following the last statement of the block.
 -->
if、else、for、while、try ブロックは常にブレース「{}」を使用し、常に複数行にしてください。開始ブレースは関数定義、条件、ループと同じ行に書いてください。終了ブレースはブロックの最後の行の次の行に書いてください。

<!-- 
```javascript
var a, b, c;

if ( myFunction() ) {
	// Expressions
} else if ( ( a &amp;&amp; b ) || c ) {
	// Expressions
} else {
	// Expressions
}
```
 -->
```javascript
var a, b, c;

if ( myFunction() ) {
	// 式
} else if ( ( a && b ) || c ) {
	// 式
} else {
	// 式
}
```
<!-- 
### Multi-line Statements
 -->
### 複数行

<!-- 
When a statement is too long to fit on one line, line breaks must occur after an operator.
 -->
文が長く、1行に収まらない場合は演算子の直後で改行してください。

<!-- 
```javascript
// Bad
var html = '&lt;p>The sum of ' + a + ' and ' + b + ' plus ' + c
	+ ' is ' + ( a + b + c ) + '&lt;/p>';

// Good
var html = '&lt;p>The sum of ' + a + ' and ' + b + ' plus ' + c +
	' is ' + ( a + b + c ) + '&lt;/p>';
```
 -->
```javascript
// 悪い
var html = '<p>The sum of ' + a + ' and ' + b + ' plus ' + c
	+ ' is ' + ( a + b + c ) + '</p>';

// 良い
var html = '<p>The sum of ' + a + ' and ' + b + ' plus ' + c +
	' is ' + ( a + b + c ) + '</p>';
```

<!-- 
Lines should be broken into logical groups if it improves readability, such as splitting each expression of a ternary operator onto its own line, even if both will fit on a single line.
 -->
読みやすさのため、行を論理的なグループで分割してください。たとえば三項演算子では1行に1つ式を書く形で、それぞれの式に分割してください。

<!-- 
```javascript
// Acceptable
var baz = ( true === conditionalStatement() ) ? 'thing 1' : 'thing 2';

// Better
var baz = firstCondition( foo ) &amp;&amp; secondCondition( bar ) ?
	qux( foo, bar ) :
	foo;
```
 -->
```javascript
// 許される
var baz = ( true === conditionalStatement() ) ? 'thing 1' : 'thing 2';

// もっと良い
var baz = firstCondition( foo ) &amp;&amp; secondCondition( bar ) ?
	qux( foo, bar ) :
	foo;
```

<!-- 
When a conditional is too long to fit on one line, each operand of a logical operator in the boolean expression must appear on its own line, indented one extra level from the opening and closing parentheses.
 -->
条件が長く行を折り返す場合、後続の行は1レベル分、追加でインデントし、本体と区別してください。

<!-- 
```javascript
if (
	firstCondition() &amp;&amp;
	secondCondition() &amp;&amp;
	thirdCondition()
) {
    doStuff();
}
```
 -->
```javascript
if (
	firstCondition() &&
	secondCondition() &&
	thirdCondition()
) {
    doStuff();
}
```

<!-- 
### Chained Method Calls
 -->
### 連続したメソッド呼び出し

<!-- 
When a chain of method calls is too long to fit on one line, there must be one call per line, with the first call on a separate line from the object the methods are called on. If the method changes the context, an extra level of indentation must be used.
 -->
連続したメソッド呼び出しが長く、行を折り返す場合、1行に1呼び出しを書いてください。最初の呼び出しも、メソッドが呼び出されるオブジェクトの次の行に書いてください。メソッドがコンテキストを変える場合は、追加のインデントを使用してください。

```javascript
elements
	.addClass( 'foo' )
	.children()
		.html( 'hello' )
	.end()
	.appendTo( 'body' );
```
<!-- 
## Assignments and Globals
 -->
## 代入とグローバル変数
<!-- 
### Declaring Variables with `const` and `let`
 -->
### const と let による変数宣言

<!-- 
For code written using ES2015 or newer, `const` and `let` should always be used in place of `var`. A declaration should use `const` unless its value will be reassigned, in which case `let` is appropriate.

Unlike `var`, it is not necessary to declare all variables at the top of a function. Instead, they are to be declared at the point at which they are first used.
 -->
ES2015 以上を使用して記述されたコードでは、var の代わりに const と let を常に使用する必要があります。値が再割り当てされ無い限り、宣言には const を使用する必要があります。そうでない場合は let を使用しましょう。

var と異なり、関数の先頭ですべての変数を宣言する必要はありません。代わりに、最初に使用する位置で宣言します。

<!-- 
### Declaring Variables With `var`
 -->
### var での変数宣言

<!-- 
Each function should begin with a single comma-delimited `var` statement that declares any local variables necessary. If a function does not declare a variable using `var`, that variable can leak into an outer scope (which is frequently the global scope, a worst-case scenario), and can unwittingly refer to and modify that data.

Assignments within the `var` statement should be listed on individual lines, while declarations can be grouped on a single line. Any additional lines should be indented with an additional tab. Objects and functions that occupy more than a handful of lines should be assigned outside of the `var` statement, to avoid over-indentation.
 -->
関数の定義は、コンマで区切った var 文による、必要なローカル変数の宣言で始めてください。var を使用せずに変数を宣言した場合、変数が外部スコープ、最悪の場合はしばしばグローバルスコープに落ち込み、データが意識しないうちに参照されたり、変更されます。

var 文内では、定義は1つの行にまとめる一方で、代入は新しい個別の行に書いてください。後続の行は追加のタブでインデントしてください。多くの行が必要なオブジェクトや関数はインデントが非常に深くなるため、var の外で代入してください。

<!-- 
```javascript
// Good
var k, m, length,
	// Indent subsequent lines by one tab
	value = 'WordPress';

// Bad
var foo = true;
var bar = false;
var a;
var b;
var c;
```
 -->
```javascript
// 良い
var k, m, length,
	// 後続業は1つのタブでインデント
	value = 'WordPress';

// 悪い
var foo = true;
var bar = false;
var a;
var b;
var c;
```

<!-- 
### Globals
 -->
### グローバル変数

<!-- 
In the past, WordPress core made heavier use of global variables. Since core JavaScript files are sometimes used within plugins, existing globals should not be removed.

All globals used within a file should be documented at the top of that file. Multiple globals can be comma-separated.

This example would make `passwordStrength` an allowed global variable within that file:
 -->
以前は WordPress コアはグローバル変数を多用していました。今もコアの JavaScript ファイルはプラグイン内部で使用されているものがあるため、既存のグローバル変数を除去することはできません。

ファイル内で使用されるすべてのグローバル変数はファイルの先頭でドキュメントしてください。複数のグローバル変数はコンマで区切って並べることもできます。

次の例で passwordStrength はファイル内で許可されるグローバル変数です。

```javascript
/* global passwordStrength:true */
```

<!-- 
The "true" after `passwordStrength` means that this global is being defined within this file. If you are accessing a global which is defined elsewhere, omit `:true` to designate the global as read-only.
 -->
`passwordStrength` の次の「true」はこのグローバル変数がこのファイル内で定義されることを意味します。他のどこかで定義されたグローバル変数にアクセスする場合には :true を削除し、グローバル変数が読み出し専用であることを明示してください。

<!-- 
### Common Libraries
 -->
### 共通ライブラリー

<!-- 
Backbone, jQuery, Underscore, and the global `wp` object are all registered as allowed globals in the root `.jshintrc` file.

Backbone and Underscore may be accessed directly at any time. jQuery should be accessed through `$` by passing the `jQuery` object into an anonymous function:
 -->
Backbone、jQuery、Underscore、グローバルの `wp` オブジェクトは、ルートの `.jshintrc` ファイル内で、許可されたグローバル変数としてすべて登録されています。

Backbone と Underscore はいつでも直接アクセスできます。jQuery は `jQuery` オブジェクトを無名関数に渡すことで $ を介してアクセスできます。

<!-- 
```javascript
( function ( $ ) {
	// Expressions
} )( jQuery );
```
 -->
```javascript
( function ( $ ) {
	// 式
} )( jQuery );
```

<!-- 
This will negate the need to call `.noConflict()`, or to set `$` using another variable.

Files which add to, or modify, the `wp` object must safely access the global to avoid overwriting previously set properties:
 -->
これで `.noConflict()` 呼び出しや他の変数を使用した `$` の設定は不要になります。

追加したり、変更するファイルでは、以前に設定されたプロパティを上書きしないよう、`wp` オブジェクトは安全にグローバル変数にアクセスする必要があります。

<!-- 
```javascript
// At the top of the file, set "wp" to its existing value (if present)
window.wp = window.wp || {};
```
 -->
```javascript
// ファイルの先頭で、wp に既存の値を設定する (もしあれば)
window.wp = window.wp || {};
```

<!-- 
## Naming Conventions
 -->
## 命名規則

<!-- 
Variable and function names should be full words, using camel case with a lowercase first letter. This is an area where this standard differs from the [WordPress PHP coding standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/php/#naming-conventions).

Names should be descriptive, but not excessively so. Exceptions are allowed for iterators, such as the use of `i` to represent the index in a loop.
 -->
変数名と関数名は省略しない完全な単語を使用し、最初の文字を小文字にした camelCase を使用してください。ここは「[WordPress PHP コーディング規約](https://ja.wordpress.org/team/handbook/coding-standards/wordpress-coding-standards/php/)」と異なる部分です。

名前は、過剰にならない範囲で説明的なものににしてください。例外はイテレーターです。例えばループ内のインデックスに `i` を使用できます。

<!-- 
### Abbreviations and Acronyms
 -->
略語と頭字語

<!-- 
[Acronyms](https://en.wikipedia.org/wiki/Acronym) must be written with each of its composing letters capitalized. This is intended to reflect that each letter of the acronym is a proper word in its expanded form.

All other [abbreviations](https://en.wikipedia.org/wiki/Abbreviation) must be written as camel case, with an initial capitalized letter followed by lowercase letters.

If an abbreviation or an acronym occurs at the start of a variable name, it must be written to respect the camelcase naming rules covering the first letter of a variable or class definition. For variable assignment, this means writing the abbreviation entirely as lowercase. For class definitions, its initial letter should be capitalized.
 -->
[頭字語](https://ja.wikipedia.org/wiki/%E9%A0%AD%E5%AD%97%E8%AA%9E)は構成している文字を全て大文字にして書く必要があります。これは頭字語の各文字が展開された形式において適切な単語であるということを反映させる目的があります。

他の全ての[略語](https://ja.wikipedia.org/wiki/%E7%95%A5%E8%AA%9E)はキャメルケースで書く必要があります。つまり、最初の文字を大文字にし続く文字を小文字にします。

略語または頭字語が変数名の先頭である場合、変数またはクラス定義の最初の文字をカバーするキャメルケースの命名規則に従うように記述する必要があります。変数割り当ての場合、これは略語をすべて小文字で書くことを意味します。クラス定義では、最初の文字を大文字にする必要があります。

<!-- 
```javascript
// "Id" is an abbreviation of "Identifier":
const userId = 1;

// "DOM" is an acronym of "Document Object Model":
const currentDOMDocument = window.document;

// Acronyms and abbreviations at the start of a variable name are consistent
// with camelcase rules covering the first letter of a variable or class.
const domDocument = window.document;
class DOMDocument {}
class IdCollection {}
```
 -->
```javascript
// "Id" は "Identifier" （識別子）の略語です。
const userId = 1;
 
// "DOM" は "Document Object Model" の頭字語です。
const currentDOMDocument = window.document;
 
// 変数名の最初に当たる頭字語と略語は変数または
// クラスの最初の文字をカバーするキャメルケースの規則と一致します。
const domDocument = window.document;
class DOMDocument {}
class IdCollection {}
```
<!-- 
### Class Definitions
 -->
### クラス定義
<!-- 
Constructors intended for use with `new` should have a capital first letter (UpperCamelCase).

A [`class` definition](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) must use the UpperCamelCase convention, regardless of whether it is intended to be used with `new` construction.
 -->
`new` での利用を想定するコンストラクターは最初の文字を大文字にしてください。例: UpperCamelCase

[`class` の定義](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)は `new` での利用に関わらず、先頭大文字のキャメルケースを使用してください。

```javascript
class Earth {
	static addHuman( human ) {
		Earth.humans.push( human );
	}

	static getHumans() {
		return Earth.humans;
	}
}

Earth.humans = [];
```
<!-- 
All [`@wordpress/element`](https://www.npmjs.com/package/@wordpress/element) Components, including stateless function components, should be named using Class Definition naming rules, both for consistency and to reflect the fact that a component may need to be transitioned from a function to a class without breaking compatibility.
 -->
ステートレス関数コンポーネントを含むすべての [`@wordpress/element`](https://www.npmjs.com/package/@wordpress/element) コンポーネントは、クラス定義命名規則を使用して名前付けする必要があります。これは一貫性のためと、コンポーネントは互換性を破壊することなく関数からクラスに移行する必要があるかもしれないという事実を反映したものです。

<!-- 
### Constants
 -->
### 定数

<!-- 
An exception to camel case is made for constant values which are never intended to be reassigned or mutated. Such variables must use the [SCREAMING_SNAKE_CASE convention](https://en.wikipedia.org/wiki/Snake_case#History).

In almost all cases, a constant should be defined in the top-most scope of a file. It is important to note that [JavaScript’s `const` assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const) is conceptually more limited than what is implied here, where a value assigned by `const` in JavaScript can in-fact be mutated, and is only protected against reassignment. A constant as defined in these coding guidelines applies only to values which are expected to never change, and is a strategy for developers to communicate intent moreso than it is a technical restriction.
 -->
キャメルケースの例外は定数値です。再代入や変更(mutate) を意図しない変数については[すべて大文字のスネークケース]((https://en.wikipedia.org/wiki/Snake_case#History)) (例: SCREAMING_SNAKE_CASE) を使用してください。

ほとんどすべての場合、定数はファイルの最上位のスコープで定義します。重要な点は [JavaScript の const 割り当て](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)が、コンセプト的にここで想定するよりもかなり制限されている点で、実際、JavaScript の const を割り当てた変数は再代入から保護されるのみで、変更 (mutate) することができます。このコーディング規約で定義する定数は、決して変更されないことを期待した値に対してのみ適用してください。技術的な制限というより、開発者の意図を伝える戦略です。
<!-- 
## Comments
 -->
## コメント

<!-- 
Comments come before the code to which they refer, and should always be preceded by a blank line. Capitalize the first letter of the comment, and include a period at the end when writing full sentences. There must be a single space between the comment token (`//`) and the comment text.
 -->
コメントは参照するコードの前に書いてください。コメントの前は常に1行空けてください。コメントの最初の文字は大文字とし、コメントが文の場合は最後にピリオドを付けてください。コメントトークン「//」とコメントの間にはスペース1個分空けてください。

<!-- 
```javascript
someStatement();

// Explanation of something complex on the next line
$( 'p' ).doSomething();

// This is a comment that is long enough to warrant being stretched
// over the span of multiple lines.
```
 -->
```javascript
someStatement();
 
// 次の行で実行する内容を説明します
$( 'p' ).doSomething();
 
// これは複数行にわたるだけの正当な長さの
// 理由があるコメントです 
```

<!-- 
JSDoc comments should use the `/**` multi-line comment opening. Refer to the [JavaScript Documentation Standards](https://make.wordpress.org/core/handbook/best-practices/inline-documentation-standards/javascript/#multi-line-comments) for more information.

Inline comments are allowed as an exception when used to annotate special arguments in formal parameter lists:
 -->
JSDoc コメントは複数行のコメントを `/**` で始める必要があります。詳細は [JavaScript Documentation Standards](https://make.wordpress.org/core/handbook/best-practices/inline-documentation-standards/javascript/#multi-line-comments) を参照してください。

内部コメントは仮引数リスト内の特殊な引数へのアノテーションで使用される場合のみ、例外的に許可されます。

<!-- 
```javascript
function foo( types, selector, data, fn, /* INTERNAL */ one ) {
	// Do stuff
}
```
 -->
```javascript
function foo( types, selector, data, fn, /* INTERNAL */ one ) {
	// 何か実行する
}
```
<!-- 
## Equality
 -->
## 等価性

<!-- 
Strict equality checks (`===`) must be used in favor of abstract equality checks (`==`).
 -->
抽象的な等価性比較 (==) よりも厳格な等価性比較 (===) を使用してください。

<!-- 
## Type Checks
 -->
型のチェック

<!-- 
These are the preferred ways of checking the type of an object:
 -->
<!--  
- String: `typeof object === 'string'`
- Number: `typeof object === 'number'`
- Boolean: `typeof object === 'boolean'`
- Object: `typeof object === 'object'` or `_.isObject( object )`
- Plain Object: `jQuery.isPlainObject( object )`
- Function: `_.isFunction( object )` or `jQuery.isFunction( object )`
- Array: `_.isArray( object )` or `jQuery.isArray( object )`
- Element: `object.nodeType` or `_.isElement( object )`
- null: `object === null`
- null or undefined: `object == null`
- undefined:
    - Global Variables: `typeof variable === 'undefined'`
    - Local Variables: `variable === undefined`
    - Properties: `object.prop === undefined`
    - Any of the above: `_.isUndefined( object )`
 -->
- 文字列: `typeof object === 'string'`
- 数: `typeof object === 'number'`
- ブール値: `typeof object === 'boolean'`
- オブジェクト: `typeof object === 'object'` または `_.isObject( object )`
- プレーンオブジェクト: `jQuery.isPlainObject( object )`
- 関数: `_.isFunction( object)` または `jQuery.isFunction( object )`
- 配列: `_.isArray( object )` または `jQuery.isArray( object )`
- 要素: `object.nodeType` または `_.isElement( object )`
- null: `object === null`
- null または undefined: `object == null`
- undefined (未定義):
  - グローバル変数: `typeof variable === ‘undefined’`
  - ローカル変数: `variable === undefined`
  - プロパティ: `object.prop === undefined`
  - 上のすべて: `_.isUndefined( object )`

<!-- 
Anywhere Backbone or Underscore are already used, you are encouraged to use [Underscore.js](http://underscorejs.org/#isElement)'s type checking methods over jQuery's.
 -->
Backbone または Underscore がすでに使われている場合は常に、jQuery でなく、[Underscore.js](http://underscorejs.org/#isElement) の型チェックメソッドを使用してください。

<!-- 
## Strings
 -->
## 文字列

<!-- 
Use single-quotes for string literals:
 -->
文字列定数にはシングルクォートを使用してください。

```javascript
var myStr = 'strings should be contained in single quotes';
```
<!-- 
When a string contains single quotes, they need to be escaped with a backslash (`\`):
 -->
文字列にシングルクォートが含まれる場合は、バックスラッシュ (\) でエスケープしてください。

<!-- 
```javascript
// Escape single quotes within strings:
'Note the backslash before the \'single quotes\'';
```
 -->
```javascript
// 文字列内のシングルクォートはエスケープ
'Note the backslash before the \'single quotes\'';
```
<!-- 
## Switch Statements
 -->
## switch 文

<!-- 
The usage of `switch` statements is generally discouraged, but can be useful when there are a large number of cases - especially when multiple cases can be handled by the same block, or fall-through logic (the `default` case) can be leveraged.

When using `switch` statements:

- Use a `break` for each case other than `default`. When allowing statements to "fall through," note that explicitly.
- Indent `case` statements one tab within the `switch`.
 -->
`switch` 文の使用は一般に推奨されません。ただし大量の case がある場合には有用なのも事実です。特に、複数の case が同じブロックで処理されたり、下に落ちていき `default` で拾うロジックが有効に機能する場合です。

`switch` 文を使用する場合

- `default` 以外の各 `case` では `break` を使用してください。次の case に意図的に落とす場合は、明示的にドキュメントしてください。
- `switch` 内の `case` 文は1個のタブでインデントしてください。

<!-- 
```javascript
switch ( event.keyCode ) {
	// ENTER and SPACE both trigger x()
	case $.ui.keyCode.ENTER:
	case $.ui.keyCode.SPACE:
		x();
		break;
	case $.ui.keyCode.ESCAPE:
		y();
		break;
	default:
		z();
}
```
 -->
```javascript
switch ( event.keyCode ) {
	// ENTER と SPACE の両方で x() を呼び出し
	case $.ui.keyCode.ENTER:
	case $.ui.keyCode.SPACE:
		x();
		break;
	case $.ui.keyCode.ESCAPE:
		y();
		break;
	default:
		z();
}
```

<!-- 
It is not recommended to return a value from within a switch statement: use the `case` blocks to set values, then `return` those values at the end.
 -->
witch 文から値を返すことは推奨されません。`case` ブロックを使用して値を設定し、最後に値を `return` してください。

```javascript
function getKeyCode( keyCode ) {
	var result;

	switch ( event.keyCode ) {
		case $.ui.keyCode.ENTER:
		case $.ui.keyCode.SPACE:
			result = 'commit';
			break;
		case $.ui.keyCode.ESCAPE:
			result = 'exit';
			break;
		default:
			result = 'default';
	}

	return result;
}
```
<!-- 
## Best Practices
 -->
## ベストプラクティス

<!-- 
### Arrays
 -->
### 配列

<!-- 
Creating arrays in JavaScript should be done using the shorthand `[]` constructor rather than the `new Array()` notation.
 -->
JavaScript で配列を作成する場合は、`new Array()` 記法ではなく、短い [] コンストラクターを使用してください。

```javascript
var myArray = [];
```
<!-- 
You can initialize an array during construction:
 -->
構築中に配列を初期化できます。

```javascript
var myArray = [ 1, 'WordPress', 2, 'Blog' ];
```
<!-- 
In JavaScript, associative arrays are defined as objects.
 -->
JavaScript では連想配列はオブジェクトとして定義されます。

<!-- 
### Objects
 -->
### オブジェクト

<!-- 
There are many ways to create objects in JavaScript. Object literal notation, `{}`, is both the most performant, and also the easiest to read.
 -->
JavaScript には多くのオブジェクト作成方法があります。オブジェクトリテラル記法、{} は両方ともパフォーマンスがよく、可読性に優れます。

```javascript
var myObj = {};
```

<!-- 
Object literal notation should be used unless the object requires a specific prototype, in which case the object should be created by calling a constructor function with `new`.
 -->
オブジェクトが特定のプロトタイプを必要としない限り、オブジェクトリテラル記法を使用してください。プロトタイプを必要とする場合は、new でコンストラクター関数を呼び出してオブジェクトを作成してください。

```javascript
var myObj = new ConstructorMethod();
```

<!-- 
Object properties should be accessed via dot notation, unless the key is a variable or a string that would not be a valid identifier:
 -->
オブジェクトプロパティはドット記法でアクセスしてください。例外はキーが変数、正しい識別子でないかもしれない文字列の場合です。

```javascript
prop = object.propertyName;
prop = object[ variableKey ];
prop = object['key-with-hyphens'];
```

<!-- 
### Iteration
 -->
### イテレーション

<!-- 
When iterating over a large collection using a `for` loop, it is recommended to store the loop's max value as a variable rather than re-computing the maximum every time:
 -->
for ループを使用して大きなコレクションをイテレートする場合、毎回ループの最大値を再計算するのではなく、いったん変数に代入して使用してください。

<!-- 
```javascript
// Good &amp; Efficient
var i, max;

// getItemCount() gets called once
for ( i = 0, max = getItemCount(); i &lt; max; i++ ) {
	// Do stuff
}

// Bad &amp; Potentially Inefficient:
// getItemCount() gets called every time
for ( i = 0; i &lt; getItemCount(); i++ ) {
	// Do stuff
}
```
 -->
```javascript
// 良い & 効果的
var i, max;

// getItemCount() が1度だけ呼ばれる
for ( i = 0, max = getItemCount(); i &lt; max; i++ ) {
	// なにか実行する
}

// 悪い & 潜在的に非効率
// getItemCount() が毎回呼ばれる
for ( i = 0; i &lt; getItemCount(); i++ ) {
	// 何か実行する
}
```

<!-- 
### Underscore.js Collection Functions
 -->
### Underscore.js コレクション関数

<!-- 
Learn and understand Underscore's [collection and array methods](http://underscorejs.org/#collections). These functions, including `_.each`, `_.map`, and `_.reduce`, allow for efficient, readable transformations of large data sets.

Underscore also permits jQuery-style chaining with regular JavaScript objects:
 -->
Underscore の [コレクションと配列メソッド](http://underscorejs.org/#collections) を学習し、理解してください。`_.each`、`_.map`、`_.reduce` 等を使用すると、大きなデータ集合の変換において効果的で、可読性にも優れます。

また Underscore では通常の JavaScript オブジェクトに対して jQuery スタイルのチェーンが可能です。

<!-- 
```javascript
var obj = {
	first: 'thing 1',
	second: 'thing 2',
	third: 'lox'
};

var arr = _.chain( obj )
	.keys()
	.map( function ( key ) {
		return key + ' comes ' + obj[ key ];
	} )
	// Exit the chain
	.value();

// arr === [ 'first comes thing 1', 'second comes thing 2', 'third comes lox' ]
```
 -->
```javascript
var obj = {
	first: 'thing 1',
	second: 'thing 2',
	third: 'lox'
};

var arr = _.chain( obj )
	.keys()
	.map( function ( key ) {
		return key + ' comes ' + obj[ key ];
	} )
	// チェーンを出る
	.value();

// arr === [ 'first comes thing 1', 'second comes thing 2', 'third comes lox' ]
```
<!-- 
### Iterating Over jQuery Collections
 -->
jQuery コレクションでのイテレート

<!-- 
The only time jQuery should be used for iteration is when iterating over a collection of jQuery objects:
 -->
jQuery オブジェクトのコレクションをイテレートする場合のみ、jQuery でイテレートしてください。

<!-- 
```javascript
$tabs.each( function ( index, element ) {
	var $element = $( element );

	// Do stuff to $element
} );
```
 -->
```javascript
$tabs.each( function ( index, element ) {
	var $element = $( element );

	// $element に対してなにか実行する
} );
```
<!-- 
Never use jQuery to iterate over raw data or vanilla JavaScript objects.
 -->
生データや素の JavaScript オブジェクトのイテレートには決して jQuery を使わないでください。

## JSHint

<!-- 
[JSHint](https://jshint.com) is an automated code quality tool, designed to catch errors in your JavaScript code. JSHint is used in WordPress development to quickly verify that a patch has not introduced any logic or syntax errors to the front-end.
 -->
[JSHint](https://jshint.com) は JavaScript コード内のエラーを発見する自動化コード品質検証ツールです。WordPress の開発ではフロントエンド側にロジックや構文のエラーを持ち込まないよう JSHint を使用してパッチを迅速に検証しています。

<!-- 
### Installing and Running JSHint
 -->
### JSHint のインストールと実行

<!-- 
JSHint is run using a tool called [Grunt](https://gruntjs.com/). Both JSHint and Grunt are programs written in [Node.js](https://nodejs.org/). The `package.json` configuration file that comes with the WordPress development code allows you to install and configure these tools.

To install Node.js, click the Install link on the [Node.js](https://nodejs.org/) website. The correct install file for your operating system will be downloaded. Follow the installation steps for your operating system to install the program.

Once Node.js is installed, open a command line window and navigate to the directory where you [checked out a copy of the WordPress SVN repository](https://make.wordpress.org/core/handbook/tutorials/installing-wordpress-locally/from-svn/) (use `cd ~/directoryname`. You should be in the root directory which contains the `package.json` file.

Next, type `npm install` into the command line window. This will download and install all the Node packages used in WordPress development.

You should now be able to type `npm run grunt jshint` to have Grunt check all the WordPress JavaScript files for syntax and logic errors. To only check core code, type `npm run grunt jshint:core`; to only check unit test .js files, type `npm run grunt jshint:tests`.
 -->
JSHint は実行に [Grunt](https://gruntjs.com/) と呼ばれるツールを使用します。JSHint も Grunt も [Node.js](https://nodejs.org/) で書かれたプログラムです。WordPress 開発コードに付属する構成ファイル `package.json` を使用すると、これらのツールを簡単にインストールし、構成できます。

Node.js をインストールするには [Node.js](https://nodejs.org/) サイトのインストールのリンクをクリックしてください。オペレーティングシステムに合った正しいインストールファイルがダウンロードされます。プログラムのインストールにはオペレーティングシステムごとのインストール手順に従ってください。

Node.js のインストール後にコマンドラインウィンドウを開き、[WordPress SVN リポジトリのコピーをチェックアウトした](https://make.wordpress.org/core/handbook/tutorials/installing-wordpress-locally/from-svn/)ディレクトリに「`cd ~/directoryname`」で移動してください。`package.json` ファイルを含むルートディレクトリにいるはずです。

次にコマンドラインウィンドウで「`npm install`」と入力します。WordPress 開発で使用するすべての Node パッケージをダウンロードし、インストールします。

ここで「`npm run grunt jshint`」と入力すると、すべての WordPress JavaScript ファイルの構文エラー、ロジックエラーを Grunt で検証できます。コアコードのみを検証するには「n`pm run grunt jshint:core`」、ユニットテスト .js ファイルのみを検証するには「`npm run grunt jshint:tests`」と入力してください。

<!-- 
### JSHint Settings
 -->
### JSHint の設定

<!-- 
The configuration options used for JSHint are stored within a [`.jshintrc` title="WordPress JSHint file in svn trunk"](https://develop.svn.wordpress.org/trunk/.jshintrc) in the WordPress SVN repository. This file defines which errors JSHint should flag if it finds them within the WordPress source code.
 -->
JSHint に使用される構成オプションは WordPress SVN リポジトリ内の [`.jshintrc` title="WordPress JSHint file in svn trunk"](https://develop.svn.wordpress.org/trunk/.jshintrc) に保存されます。このファイルでは JSHint が WordPress ソースコード内のどのエラーにフラグを立てるべきかを定義します。

<!-- 
### Target A Single File
 -->
### 単一ファイルの検証

<!-- 
To specify a single file for JSHint to check, add `--file=filename.js` to the end of the command. For example, this will only check the file named "admin-bar.js" within WordPress's core JavaScript files:
 -->
JSHint の検証に単一ファイルを指定するには、コマンドの最後に「--file=filename.js」を追加してください。例えば、次の行は WordPress の JavaScript ファイル内のファイル「admin-bar.js」のみを検証します。

`npm run grunt jshint:core --file=admin-bar.js`

<!-- 
And this would only check the "password-strength-meter.js" file within the unit tests directory:
 -->
次の行は ユニットテスト用ディレクトリ内のファイル「password-strength-meter.js」のみを検証します。

`npm run grunt jshint:tests --file=password-strength-meter.js`

<!-- 
Limiting JSHint to a single file can be useful if you are only working on one or two specific files and don't want to wait for JSHint to process every single file each time it runs.
 -->
開発中に1、2個の特定のファイルだけ変更しており、JSHint 実行のたびにすべてのファイルの検証を待ちたくない場合、JSHint を単一ファイルに絞ると効率的です。

<!-- 
### JSHint Overrides: Ignore Blocks
 -->
### JSHint オーバーライド – ignore ブロック

<!-- 
In some situations, parts of a file should be excluded from JSHint. As an example, the script file for the admin bar contains the minified code for the jQuery HoverIntent plugin - this is third-party code that should not pass through JSHint, even though it is part of a WordPress core JavaScript file.

To exclude a specific file region from being processed by JSHint, enclose it in JSHint directive comments:
 -->
ファイルの一部を JSHint の検証から除外したい場合があります。たとえばツールバーのスクリプトファイルが 縮小された jQuery HoverIntent プラグインのコードを含む場合、これは WordPress コア JavaScript の一部ですが、サードパーティ製のコードのため JSHint をパスする必要はありません。

JSHint の処理から特定のファイルの部分を除外するには、JSHint ディレクティブコメントで囲んでください。

<!-- 
```javascript
/* jshint ignore:start */
if ( typeof jQuery.fn.hoverIntent === 'undefined' ) {
	// hoverIntent r6 - Copy of wp-includes/js/hoverIntent.min.js
	(function(a){a.fn.hoverIntent=...............
}
/* jshint ignore:end */
```
 -->
```javascript
/* jshint ignore:start */
if ( typeof jQuery.fn.hoverIntent === 'undefined' ) {
	// hoverIntent r6 - Copy of wp-includes/js/hoverIntent.min.js
	(function(a){a.fn.hoverIntent=...............
}
/* jshint ignore:end */
```

<!--  
## Credits
 -->
## クレジット
<!-- 
- The jQuery examples are adapted from the [jQuery JavaScript Style Guide](https://contribute.jquery.org/style-guide/js), which is made available under the MIT license.
 -->
- jQuery の例は MIT license の下で利用可能な「[jQuery JavaScript Style Guide](https://contribute.jquery.org/style-guide/js)」から転用しています。

[原文](https://github.com/WordPress/wpcs-docs/blob/master/wordpress-coding-standards/javascript.md) / [日本語訳](https://github.com/jawordpressorg/wpcs-docs/blob/master/wordpress-coding-standards/javascript.md)

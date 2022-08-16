<!-- 
# PHP Coding Standards
 -->
# PHP コーディング規約

<!-- 
These PHP coding standards are intended for the WordPress community as a whole. They are mandatory for WordPress Core and we encourage you to use them for your themes and plugins as well.

While themes and plugins may choose to follow a different _coding style_, these **_coding standards_** are not just about _code style_, but also encompass established best practices regarding interoperability, translatability, and security in the WordPress ecosystem, so, even when using a different _code style_, we recommend you still adhere to the WordPress Coding Standards in regard to these best practices.
 -->
PHP 標準コーディング規約は、WordPress コミュニティ全体を対象としています。WordPress コアでは必須、テーマやプラグインでも同様に使用を推奨します。

テーマやプラグインは別のコーディングスタイルを選択できますが、この **コーディング標準** は、単にコーディングスタイルに関するものではなく、WordPress エコシステムの相互運用性、翻訳性、セキュリティに関する確立したベストプラクティスを包含するものであり、別のコーディングスタイルを使用する場合でも、このベストプラクティスに関して WordPress コーディング標準を遵守することを推奨します。

<!-- 
While not all code may fully comply with these standards (yet), all newly committed and/or updated code should fully comply with these coding standards.

Also see the [PHP Inline Documentation Standards](https://developer.wordpress.org/coding-standards/inline-documentation-standards/php/) for further guidelines.
 -->
すべてのコードは、(まだ) この規約に完全に準拠していませんが、新しくコミットされたコードや更新されたコードは、コーディング規約に完全に準拠する必要があります。

また、[PHP インラインドキュメント規約](https://ja.wordpress.org/team/handbook/coding-standards/inline-documentation-standards/php/)も参照してください。

<!-- 
If you want to automatically check your code against this standard, you can use the official [WordPress Coding Standards](https://github.com/WordPress/WordPress-Coding-Standards) tooling, which is run using [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer/).
 -->
この規約への準拠を自動的にチェックしたい場合は、公式の [WordPress Coding Standards](https://github.com/WordPress/WordPress-Coding-Standards)ツールを使用してください。[PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer/) を使用して実行されます。

<!-- 
Some parts of the WordPress code structure for PHP markup are inconsistent in their style. WordPress is working to gradually improve this by helping users maintain a consistent style so the code can become clean and easy to read at a glance.
 -->
<!-- 
WordPress の一部の PHP コードには一貫性に欠ける部分があります。WordPress ではユーザーの支援も得ながら徐々にこれらを改善し、コードをクリーンで読みやすいものにするよう努めています。

WordPress において PHP のコードを書く場合はこの規約に従ってください。これは WordPress コアのプログラミングだけではなく、プラグインやテーマの作成でも同様です。規約は多くの点で「[Pear standards](http://pear.php.net/manual/en/standards.php)」に似ていますが、一部異なる部分もあります。
 -->
<!-- 
<h2>PHP</h2>
 -->
<!-- 
## PHP
 -->

<!-- 
## General
 -->
## 全般

<!-- 
### Opening and Closing PHP Tags
 -->
### 開始、終了の PHP タグ

<!-- 
When embedding multi-line PHP snippets within an HTML block, the PHP open and close tags must be on a line by themselves.
 -->
HTML ブロック内に複数行の PHP コードを埋め込む場合、PHP 開始タグ、終了タグはそれぞれ1行を使用してください。

<!-- 
Correct (Multiline):
 -->
正しい (複数行):

```php
function foo() {
    ?>
    <div>
        <?php
        echo esc_html(
            bar(
                $baz,
                $bat
            )
        );
        ?>
    </div>
    <?php
}
```
<!-- 
Correct (Single Line):
 -->
正しい (単一行):

```php
<input name="<?php echo esc_attr( $name ); ?>" />
```

<!-- 
Incorrect:
 -->
間違い:

```php
if ( $a === $b ) { ?>
<some html>
<?php }
```

<!-- 
### No Shorthand PHP Tags
 -->
### PHP ショートタグは禁止

<!-- 
**Important:** Never use shorthand PHP start tags. Always use full PHP tags.
 -->
**重要** 絶対に PHP のショートタグは使わないでください。常に完全な PHP タグを使用してください。

<!-- 
Correct:
 -->
正しい:

```php
<?php ... ?>
<?php echo esc_html( $var ); ?>
```
<!-- 
Incorrect:
 -->
間違い:

```php
<? ... ?>
<?= esc_html( $var ) ?>
```

<!-- 
### Single and Double Quotes
 -->
### シングルクォートとダブルクォート

<!-- 
Use single and double quotes when appropriate. If you're not evaluating anything in the string, use single quotes. You should almost never have to escape quotes in a string, because you can just alternate your quoting style, like so:
 -->
シングルクォートとダブルクォートは適切に使い分けてください。文字列の中で何も評価しない場合は、シングルクォートを使用してください。クォートの種類を入れ替えれば済むため、文字列の中でエスケープを使用する必要はほとんどないはずです。

```php
echo '<a href="/static/link" class="button button-primary">Link name</a>';
echo "<a href='{$escaped_link}'>text with a ' single quote</a>";
```

<!-- 
Text that goes into HTML or XML attributes should be escaped so that single or double quotes do not end the attribute value and invalidate the HTML, causing a security issue. See [Data Validation](https://developer.wordpress.org/plugins/security/data-validation/) in the Plugin Handbook for further details.
 -->
HTML や XML の属性に入るテキストはエスケープしてください。シングルクォートまたはダブルクォートが閉じていない属性値は、HTML として無効で、セキュリティ問題を引き起こす可能性があります。詳細については、プラグインハンドブックの [Data Validation](https://developer.wordpress.org/plugins/security/data-validation/) を参照してください。

<!-- 
## Naming
 -->
## 命名

<!-- 
### Naming Conventions
 -->
### 命名規則

<!-- 
Use lowercase letters in variable, action/filter, and function names (never `camelCase`). Separate words via underscores. Don't abbreviate variable names unnecessarily; let the code be unambiguous and self-documenting.
 -->
変数、アクション、関数の名前にはアルファベット小文字を使います。`camelCase` は使いません。単語はアンダースコアで区切ります。不必要に変数名を省略しないでください。コードは明確に、理解可能なものにしてください。

```php
function some_name( $some_variable ) { [...] }
```
<!-- 
Class names should use capitalized words separated by underscores. Any acronyms should be all upper case.
 -->
クラス名は大文字で始まる単語をアンダースコアで区切ります。省略語はすべて大文字にします。

```php
class Walker_Category extends Walker { [...] }
class WP_HTTP { [...] }
```
<!-- 
Constants should be in all upper-case with underscores separating words:
 -->
定数はすべて大文字で、アンダースコアで区切ります。

```php
define( 'DOING_AJAX', true );
```
<!-- 
Files should be named descriptively using lowercase letters. Hyphens should separate words.
 -->
ファイル名はアルファベットの小文字を使用して、内容を説明する名前にしてください。単語はハイフンで区切ります。

```php
my-plugin-name.php
```

<!-- 
Class file names should be based on the class name with `class-` prepended and the underscores in the class name replaced with hyphens, for example, `WP_Error` becomes:
 -->
クラスファイルの名前はクラス名を基にして、前に「class-」を付け、クラス名内部のアンダースコアはハイフンで置き換えます。 たとえば「WP_Error」の場合

```php
class-wp-error.php
```

<!-- 
This file-naming standard is for all current and new files with classes. There is one exception to this rule for three legacy files: `class.wp-dependencies.php`, `class.wp-scripts.php`, `class.wp-styles.php`. Those files are prepended with `class.`, a dot after the word class instead of a hyphen.

Files containing template tags in the `wp-includes` directory should have `-template` appended to the end of the name so that they are obvious.
 -->
このファイル命名規則は、すべての現行のクラスファイル、将来のクラスファイルに適用されます。例外は 3つの古いファイル「class.wp-dependencies.php」「class.wp-scripts.php」「class.wp-styles.php」で、これらは接頭辞が `class.` のように、ハイフンの代わりにドットで始まります。

`wp-includes` 内のテンプレートタグを含むファイルには、分かりやすさのため名前の末尾に `-template` を付けてくだださい。

```php
general-template.php
```

<!-- 
### Interpolation for Naming Dynamic Hooks
 -->
### ダイナミックフック名での変数展開の利用

<!-- 
Dynamic hooks should be named using interpolation rather than concatenation for readability and discoverability purposes.

Dynamic hooks are hooks that include dynamic values in their tag name, e.g. `{$new_status}_{$post->post_type}` (publish_post).

Variables used in hook tags should be wrapped in curly braces `{` and `}`, with the complete outer tag name wrapped in double quotes. This is to ensure PHP can correctly parse the given variables' types within the interpolated string.
 -->
ダイナミックフックの名前では読みやすさ、検索のしやすさのため、変数の連結でなく、展開を使用してください。

ダイナミックフックはタグ名に動的な値を含むフックです。例: `{$new_status}_{$post->post_type}` (publish_post)

フックタグで使用される変数は中括弧(「{」と「}」)で囲み、完全なタグ名全体をダブルクオートで囲んでください。こうすると PHP は、挿入された文字列内で指定された変数の型を正しくパースできます。

```php
do_action( "{$new_status}_{$post->post_type}", $post->ID, $post );
```
<!-- 
Where possible, dynamic values in tag names should also be as succinct and to the point as possible. `$user_id` is much more self-documenting than, say, `$this->id`.
 -->
このときタグ名内の動的な値はできるだけ簡潔で分かりやすいものにしてください。`$user_id` の方がたとえば `$this->id` などよりも明確です。

<!-- 
## Whitespace
 -->
## スペース

<!-- 
### Space Usage
 -->
### スペースの使い方

<!-- 
Always put spaces after commas, and on both sides of logical, comparison, string and assignment operators.
 -->
コンマの後ろや、論理演算子、比較演算子、文字列演算子、代入演算子の両側には、常にスペースを入れてください。

```php
SOME_CONST === 23;
foo() && bar();
! $foo;
array( 1, 2, 3 );
$baz . '-5';
$term .= 'X';
```

<!-- 
Put spaces on both sides of the opening and closing parentheses of control structure blocks.
 -->
制御構造ブロックの開きかっこ、閉じかっこの両側にも入れてください。

```php
foreach ( $foo as $bar ) { ...
```

<!-- 
When defining a function, do it like so:
 -->
関数を定義する場合は、次の形式に従ってください。

```php
function my_function( $param1 = 'foo', $param2 = 'bar' ) { ...

function my_other_function() { ...
```
<!-- 
When calling a function, do it like so:
 -->
関数を呼び出す場合

```php
my_function( $param1, func_param( $param2 ) );
my_other_function();
```
<!-- 
When performing logical comparisons, do it like so:
 -->
論理比較の場合

```php
if ( ! $foo ) { ...
```

<!-- 
[Type casts](https://www.php.net/manual/en/language.types.type-juggling.php#language.types.typecasting) must be lowercase. Always prefer the short form of type casts, `(int)` instead of `(integer)` and `(bool)` rather than `(boolean)`. For float casts use `(float)`, not `(real)` which is [deprecated](https://www.php.net/manual/en/migration74.deprecated.php#migration74.deprecated.core.real) in PHP 7.4, and removed in PHP 8:
 -->
[型のキャスト](http://www.php.net/manual/en/language.types.type-juggling.php#language.types.typecasting) は小文字です。常に短い形式を使用してください。`(integer)` でなく `(int)`、`(boolean)` でなく `(bool)`。float については `(float)` を使用してください。`(real)` は使いません。PHP 7.4 で [非推奨](https://www.php.net/manual/en/migration74.deprecated.php#migration74.deprecated.core.real)、PHP 8 で削除されています。

```php
foreach ( (array) $foo as $bar ) { ...

$foo = (bool) $bar;
```

<!-- 
When referring to array items, only include a space around the index if it is a variable, for example:
 -->
配列要素を参照する場合には、添字が変数の場合のみ前後にスペースを入れてください。

<!-- 
```php
$x = $foo['bar']; // Correct.
$x = $foo[ 'bar' ]; // Incorrect.

$x = $foo[0]; // Correct.
$x = $foo[ 0 ]; // Incorrect.

$x = $foo[ $bar ]; // Correct.
$x = $foo[$bar]; // Incorrect.
```
 -->
```php
$x = $foo['bar']; // 正しい
$x = $foo[ 'bar' ]; // 間違い

$x = $foo[0]; // 正しい
$x = $foo[ 0 ]; // 間違い

$x = $foo[ $bar ]; // 正しい
$x = $foo[$bar]; // 間違い
```

<!-- 
In a `switch` block, there must be no space between the `case` condition and the colon.
 -->
`switch` ブロックでは、`case` の条件とコロンの間にスペースを置かないでください。

<!-- 
```php
switch ( $foo ) {
    case 'bar': // Correct.
    case 'ba' : // Incorrect.
}
```
 -->
```php
switch ( $foo ) {
	case 'bar': // 正しい
	case 'ba' : // 間違い
}
```

<!-- 
Similarly, there should be no space before the colon on return type declarations.
 -->
同様に、戻りの型の宣言のコロンの前にスペースを置かないでください。

```php
function sum( $a, $b ): float {
    return $a + $b;
}
```

<!-- 
Unless otherwise specified, parentheses should have spaces inside them.
 -->
特に指定のない限り、括弧はそれぞれの内側にスペースを置いてください。

```php
if ( $foo && ( $bar || $baz ) ) { ...

my_function( ( $x - 1 ) * 5, $y );
```

<!-- 
### Indentation
 -->
### インデント

<!-- 
Your indentation should always reflect logical structure. Use **real tabs**, **not spaces**, as this allows the most flexibility across clients.

Exception: if you have a block of code that would be more readable if things are aligned, use spaces:
 -->
インデントは常に論理的な構造を反映してください。インデントには**本物のタブ**を使用します。**スペースは使わないでください**。大部分のクライアント環境で最大の柔軟性を得られます。

例外: コードブロックの可読性のために必要であれば、スペースを使用してください。

```php
[tab]$foo   = 'somevalue';
[tab]$foo2  = 'somevalue2';
[tab]$foo34 = 'somevalue3';
[tab]$foo5  = 'somevalue4';
```
<!-- 
For associative arrays, _each item_ should start on a new line when the array contains more than one item:
 -->
連想配列で複数の要素を含む場合、_各項目_を、新しい行で始めてください。

```php
$query = new WP_Query( array( 'ID' => 123 ) );
```

```php
$args = array(
[tab]'post_type'   => 'page',
[tab]'post_author' => 123,
[tab]'post_status' => 'publish',
);
 
$query = new WP_Query( $args );
```
<!-- 
Note the comma after the last array item: this is recommended because it makes it easier to change the order of the array, and makes for cleaner diffs when new items are added.
 -->
注意: 配列の最後の要素に続くコンマは推奨です。配列の要素を簡単に並べ替えることができ、新しい項目が追加されても diff の結果が明確です。

```php
$my_array = array(
[tab]'foo'   => 'somevalue',
[tab]'foo2'  => 'somevalue2',
[tab]'foo3'  => 'somevalue3',
[tab]'foo34' => 'somevalue3',
);
```

<!-- 
For `switch` control structures, `case` statements should be indented one tab from the `switch` statement and the contents of the `case` should be indented one tab from the `case` condition statement.
 -->
`switch` 制御構造では、`case` 文は `switch` 文から1タブ分インデントし、`case` の内容は `case` の条件文から1タブ分インデントしてください。

```php
switch ( $type ) {
[tab]case 'foo':
[tab][tab]some_function();
[tab][tab]break;
[tab]case 'bar':
[tab][tab]some_function();
[tab][tab]break;
}
```

<!-- 
**Rule of thumb:** Tabs should be used at the beginning of the line for indentation, while spaces can be used mid-line for alignment.
 -->
**ルール**: 行の先頭はタブでインデントし、途中を揃える場合にスペースを使用してください。

<!-- 
### Remove Trailing Spaces
 -->
### 文末の空白の除去

<!-- 
Remove trailing whitespace at the end of each line. Omitting the closing PHP tag at the end of a file is preferred. If you use the tag, make sure you remove trailing whitespace.
 -->
各行末尾のスペースは削除してください。ファイル末尾の PHP 終了タグの除去は推奨です。終了タグを使用する場合には、その後にスペースがないことを確認してください。

<!-- 
## Formatting
 -->
フォーマット

<!-- 
### Brace Style
 -->
### ブレース (波かっこ、中括弧) の形式

<!-- 
Braces shall be used for all blocks in the style shown here:
 -->
すべてのブロックに対して以下の形式でブレースを使用してください。

```php
if ( condition ) {
    action1();
    action2();
} elseif ( condition2 && condition3 ) {
    action3();
    action4();
} else {
    defaultaction();
}
```

<!-- 
If you have a really long block, consider whether it can be broken into two or more shorter blocks, functions, or methods, to reduce complexity, improve ease of testing, and increase readability.

Braces should always be used, even when they are not required:
 -->
その上で非常に長いブロックがあれば、複数の短いブロック、関数、メソッドに分割できないかを検討してください。分割することで複雑度を解消し、テストしやすくなり、可読性を向上します。

ブレースは必ず使用してください。省略可能な場合でも使用してください。

```php
if ( condition ) {
    action0();
}

if ( condition ) {
    action1();
} elseif ( condition2 ) {
    action2a();
    action2b();
}

foreach ( $items as $item ) {
    process_item( $item );
}
```
<!-- 
Note that requiring the use of braces means that _single-statement inline control structures_ are prohibited. You are free to use the [alternative syntax for control structures](https://www.php.net/manual/en/control-structures.alternative-syntax.php) (e.g. `if`/`endif`, `while`/`endwhile`)—especially in templates where PHP code is embedded within HTML, for instance:
 -->
注意: ブレースの使用を義務付けるということは、「単一文のインライン制御構造」の禁止を意味します。「[制御構造に関する別の構文](http://php.net/manual/ja/control-structures.alternative-syntax.php)」は使用しても構いません (例: 「if」と「endif」、「while」と「endwhile」)。これらは例えば、テンプレート内で HTML に PHPコードを埋め込む際に使用されます。

```php
<?php if ( have_posts() ) : ?>
    <div class="hfeed">
        <?php while ( have_posts() ) : the_post(); ?>
            <article id="<?php echo esc_attr( 'post-' . get_the_ID() ); ?>" class="<?php echo esc_attr( get_post_class() ); ?>">
                <!-- ... -->
            </article>
        <?php endwhile; ?>
    </div>
<?php endif; ?>
```
<!-- 
### Declaring Arrays
 -->
### 配列の宣言

<!-- 
Using long array syntax ( `array( 1, 2, 3 )` ) for declaring arrays is generally more readable than short array syntax ( `[ 1, 2, 3 ]` ), particularly for those with vision difficulties. Additionally, it's much more descriptive for beginners.

Arrays must be declared using long array syntax.
 -->
配列の宣言では、一般に長い配列構文 (array( 1, 2, 3 )) の方が短い配列構文 ([ 1, 2, 3 ]) よりも可読性に優れます。これは主に視覚的な面からから来ますが、加えて初心者にとっても分かりやすくなります。

配列は常に長い配列構文で宣言してください。

<!-- 
### Multiline Function Calls
 -->
### 複数行での関数呼び出し

<!-- 
When splitting a function call over multiple lines, each parameter must be on a separate line. Single line inline comments can take up their own line.

Each parameter must take up no more than a single line. Multi-line parameter values must be assigned to a variable and then that variable should be passed to the function call.
 -->
関数呼び出しを複数行に分割する場合、1行ずつパラメータを並べてください。インラインコメントも単体で1行にしてください。

各パラメータはそれ以上複数行に分割しないでください。複数行必要なパラメータ値は、まず変数に割り当て、次にその変数を関数呼び出しに指定してください。

```php
$bar = array(
    'use_this' => true,
    'meta_key' => 'field_name',
);
$baz = sprintf(
    /* translators: %s: Friend's name */
    __( 'Hello, %s!', 'yourtextdomain' ),
    $friend_name
);

$a = foo(
    $bar,
    $baz,
    /* translators: %s: cat */
    sprintf( __( 'The best pet is a %s.' ), 'cat' )
);
```

<!-- 
## Object-Oriented Programming

### Only One Object Structure (Class/Interface/Trait) per File
 -->
## オブジェクト指向プログラミング

### ファイルごとに、1つのオブジェクト構造 (クラス、インターフェース、トレイト)

<!-- 
For instance, if we have a file called `class-example-class.php` it can only contain one class in that file.
 -->
例えば、ファイル `class-example-class.php` には1つのクラスしか入れられません。

<!-- 
```php
// Incorrect: file class-example-class.php.
class Example_Class { [...] }

class Example_Class_Extended { [...] }
```
 -->
```php
// 間違い: ファイル class-example-class.php
class Example_Class { [...] }

class Example_Class_Extended { [...] }
```

<!-- 
The second class should be in its own file called `class-example-class-extended.php`.
 -->
2つ目のクラスは、個別のファイル `class-example-class-extended.php` に置きます。

<!-- 
```php
// Correct: file class-example-class.php.
class Example_Class { [...] }
```

```php
// Correct: file class-example-class-extended.php.
class Example_Class_Extended { [...] }
```
 -->
```php
// 正しい: ファイル class-example-class.php
class Example_Class { [...] }
```

```php
// 正しい: ファイル class-example-class-extended.php
class Example_Class_Extended { [...] }
```


<!-- 
## Control Structures
 -->
## 制御構造

<!-- 
### Use `elseif`, not `else if`
 -->
### 「elseif」を使う。「else if」は使わない

<!-- 
`else if` is not compatible with the colon syntax for `if|elseif` blocks. For this reason, use `elseif` for conditionals.
 -->
「else if」は「if|elseif」ブロックのコロン構文と互換性がありません。条件式では「elseif」を使用してください。

<!-- 
### Yoda Conditions
 -->
### ヨーダ記法

```php
if ( true === $the_force ) {
    $victorious = you_will( $be );
}
```
<!-- 
When doing logical comparisons involving variables, always put the variable on the right side and put constants, literals, or function calls on the left side. If neither side is a variable, the order is not important. (In [computer science terms](https://en.wikipedia.org/wiki/Value_(computer_science)#Assignment:_l-values_and_r-values), in comparisons always try to put l-values on the right and r-values on the left.)
 -->
変数を伴う論理比較を行う場合、常に変数を右側に、定数や文字列や関数呼び出しを左側に置いてください。どちらも変数でなければ、順序は重要ではありません ([コンピューターサイエンスの言葉](https://en.wikipedia.org/wiki/Value_(computer_science)#Assignment:_l-values_and_r-values)では、比較時、常に l-value を右意、r-value を左に置きます)。

<!-- 
In the above example, if you omit an equals sign (admit it, it happens even to the most seasoned of us), you'll get a parse error, because you can't assign to a constant like `true`. If the statement were the other way around `( $the_force = true )`, the assignment would be perfectly valid, returning `1`, causing the if statement to evaluate to `true`, and you could be chasing that bug for a while.

A little bizarre, it is, to read. Get used to it, you will.

This applies to `==`, `!=`, `===`, and `!==`. Yoda conditions for `<`, `>`, `<=` or `>=` are significantly more difficult to read and are best avoided.
 -->
上の例で1つ等号を忘れると (白状すると、熟練のコアメンバーでもやらかします)、パースエラーが発生します。定数 `true` に代入できないためです。もし条件式が `( $the_force = true )` であれば、代入は構文として正しく `1` を返し、結果 if 文は `true` と評価し、そして、しばらくバグと闘うことになるでしょう。

ヨーダ記法は最初、奇妙に見えるかもしれませんが、そのうち慣れるはずです。

なおヨーダ記法は「`==`」「`!=`」「`===`」「`!==`」で使用してください。「<」「>」「<=」「>=」では読みづらいため避けてください。

<!-- 
## Operators
 -->
## 演算子
<!-- 
### Ternary Operator
 -->
### 三項演算子

<!--
[Ternary operators](https://www.php.net/manual/en/language.operators.comparison.php#language.operators.comparison.ternary) are fine, but always have them test if the statement is true, not false. Otherwise, it just gets confusing. (An exception would be using `! empty()`, as testing for false here is generally more intuitive.)

The short ternary operator must not be used.

For example:
 -->
[三項演算子](http://en.wikipedia.org/wiki/ja:%E4%B8%89%E9%A0%85%E6%BC%94%E7%AE%97%E5%AD%90)は使用しても構いませんが、常に文が true かどうかをテストしてください。false のテストは混ぜないでください、混乱するだけです。ただし「! empty()」の場合は例外です。この場合は false のテストのほうが直感的でしょう。

短い形式の三項演算子は使用しないでください。

例:

```php
// (if statement is true) ? (do this) : (else, do this);
$musictype = ( 'jazz' === $music ) ? 'cool' : 'blah';
// (if field is not empty ) ? (do this) : (else, do this);
```
<!-- 
### Error Control Operator `@`
 -->
### エラー制御演算子 @

<!-- 
As noted in the [PHP docs](https://www.php.net/manual/en/language.operators.errorcontrol.php):

> PHP supports one error control operator: the at sign (@). When prepended to an expression in PHP, any diagnostic error that might be generated by that expression will be suppressed.

While this operator does exist in Core, it is often used lazily instead of doing proper error checking. Its use is highly discouraged, as even the PHP docs also state:

> Warning: Prior to PHP 8.0.0, it was possible for the @ operator to disable critical errors that will terminate script execution. For example, prepending @ to a call of a function that did not exist, by being unavailable or mistyped, would cause the script to terminate with no indication as to why.
 -->
[PHP ドキュメント](http://www.php.net//manual/ja/language.operators.errorcontrol.php) にあるように、

> PHP はエラー制御演算子(@)をサポートしています。PHP の式の前に付けた場合、その式で起こる可能性のある診断エラーは抑制されます。

この演算子がコア内に存在すると、適切なエラーチェックが行われずしばしば遅れて適用されます。決して使用しないでください。ちなみに PHP のドキュメントにさえ次のような箇所があります。

> PHP 8.0.0 より前のバージョンでは、 スクリプトの実行を停止させるような致命的な場合であっても @ 演算子でエラーメッセージを抑止することが可能でした。 たとえば、存在しなかったり、ミスタイプされていたり、 利用できない関数コールの前に @ 演算子を付けると、 原因を示すことなく、その場所でスクリプトは終了してしまっていました。

<!-- 
## Database
 -->
データベース

<!-- 
### Database Queries
 -->
### データベースクエリ

<!-- 
Avoid touching the database directly. If there is a defined function that can get the data you need, use it. Database abstraction (using functions instead of queries) helps keep your code forward-compatible and, in cases where results are cached in memory, it can be many times faster.

If you must touch the database, consider creating a [Trac](https://core.trac.wordpress.org/) ticket. There you can discuss the possibility of adding a new function to cover the functionality you wanted, for a future version of WordPress.
 -->
データベースには直接触らないでください。必要なデータを取得する関数があれば、それを使用してください。クエリの代わりに関数を使用したデータベースの抽象化を利用すると、コードは前方互換性を保ち、結果がメモリー内にキャッシュされる場合は何倍も速くなります。

データベースに触る必要があると考える場合は、[Trac](https://core.trac.wordpress.org/) チケットの作成を検討してください。そこで、WordPress の将来のバージョンに、希望する機能を持つ新しい関数を追加する可能性について議論できます。

<!-- 
### Formatting SQL statements
 -->
### SQL 文の書式

<!-- 
When formatting SQL statements you may break them into several lines and indent if it is sufficiently complex to warrant it. Most statements work well as one line though. Always capitalize the SQL parts of the statement like `UPDATE` or `WHERE`.

Functions that update the database should expect their parameters to lack SQL slash escaping when passed. Escaping should be done as close to the time of the query as possible, preferably by using `$wpdb->prepare()`

`$wpdb->prepare()` is a method that handles escaping, quoting, and int-casting for SQL queries. It uses a subset of the `sprintf()` style of formatting. Example :
 -->
SQL 文が非常に複雑な場合は、複数行に分割し、インデントしても構いません。大部分の SQL 文は1行の場合と同様に動作するはずです。文の SQL の部分は「`UPDATE`」や「`WHERE`」のように常に大文字にしてください。

データベースを更新する関数は、渡されたパラメータが SQL 用にエスケープされていないと仮定して処理してください。エスケープはできるだけクエリの直前に、可能であれば「`$wpdb->prepare()`」を使用して実行してください。

「`$wpdb->prepare()`」は SQL クエリのエスケープ、クォート、整数へのキ ャストを処理するメソッドです。`sprintf()` 書式のサブセットを使用します。 例:

<!-- 
```php
$var = "dangerous'"; // Raw data that may or may not need to be escaped.
$id = some_foo_number(); // Data we expect to be an integer, but we're not certain.

$wpdb->query( $wpdb->prepare( "UPDATE $wpdb->posts SET post_title = %s WHERE ID = %d", $var, $id ) );
```
 -->
```php
$var = "dangerous'"; // 生データ。エスケープしてもしなくても良い
$id = some_foo_number(); // integer を期待するデータ。ただし確証はない

$wpdb->query( $wpdb->prepare( "UPDATE $wpdb->posts SET post_title = %s WHERE ID = %d", $var, $id ) );
```

<!-- 
`%s` is used for string placeholders and `%d` is used for integer placeholders. Note that they are not 'quoted'! `$wpdb->prepare()` will take care of escaping and quoting for us. The benefit of this is that it is easy to see at a glance whether something has been escaped or not because it happens right when the query happens.

See [Data Validation](https://developer.wordpress.org/plugins/security/data-validation/) in the Plugin Handbook for further details.
 -->
`%s` は文字列のプレースホルダーとして、`%d` は整数のプレースホルダーとして使用されます。注意: これらに「クォート」はありません。 「`$wpdb->prepare()`」がエスケープやクォートを実行します。この方法の良い点は、クエリーが発生するとすぐに起きるため、エスケープの有無が一目でわかる点です。

詳細については、Plugin Handbook の「[Data Validation](https://developer.wordpress.org/plugins/security/data-validation/)」を参照してください。

<!-- 
## Recommendations

### Self-Explanatory Flag Values for Function Arguments
 -->
## 推奨

### 関数の引数には意味のあるフラグ値を使用する

<!-- 
Prefer string values to just `true` and `false` when calling functions.
 -->
関数を呼び出す場合は、単に `true` や `false` を使用するのではなく、文字列値を使用してください。

<!-- 
```php
// Incorrect.
function eat( $what, $slowly = true ) {
...
}
eat( 'mushrooms' );
eat( 'mushrooms', true ); // What does true mean?
eat( 'dogfood', false ); // What does false mean? The opposite of true?
```
 -->
```php
// 間違い
function eat( $what, $slowly = true ) {
...
}
eat( 'mushrooms' );
eat( 'mushrooms', true ); // true って、どういうこと?
eat( 'dogfood', false ); // false って、どういうこと? true の反対ってこと?
```

<!-- 
PHP only supports named arguments as of PHP 8.0. However, as WordPress currently still supports older PHP versions, we cannot yet use those.
Without named arguments, the values of the flags are meaningless, and each time we come across a function call like the examples above, we have to search for the function definition. The code can be made more readable by using descriptive string values, instead of booleans.
 -->
PHP は 8.0 以降で名前付き引数をサポートします。しかし、WordPress は現在まだ古いバージョンの PHP をサポートしているため、まだ名前付き引数をを使用できません。
名前付き引数がない場合、フラグの値には意味がありません。この結果、上のような例に出会うたびに関数定義を探す必要が出てきます。ブール値の代わりに説明的な文字列値を使用することで、コードは読みやすくなります。

<!-- 
```php
// Correct.
function eat( $what, $speed = 'slowly' ) {
...
}
eat( 'mushrooms' );
eat( 'mushrooms', 'slowly' );
eat( 'dogfood', 'quickly' );
```
 -->
```php
// 正しい
function eat( $what, $speed = 'slowly' ) {
...
}
eat( 'mushrooms' );
eat( 'mushrooms', 'slowly' );
eat( 'dogfood', 'quickly' );
```
<!-- 
When more words are needed to describe the function parameters, an `$args` array may be a better pattern.
 -->
関数パラメータに説明を加えたければ、配列 `$args` が良いパターンです。 

```php
function eat( $what, $args ) {
...
}
eat ( 'noodles', array( 'speed' => 'moderate' ) );
```

<!-- 
Be careful when using this pattern, as it can lead to "Undefined array index" notices if input isn't validated before use. Use this pattern only where it makes sense (i.e. multiple possible arguments), not just for the sake of it.
 -->
このパターンを使用する際には注意が必要です。使用前に入力を検証しなければ、警告「Undefined array index (未定義の配列インデックス)」になる場合があります。このパターンは、意味のある場合のみ使用してください (たとえば、複数の引数を指定する場合など)。

<!-- 
### Clever Code
 -->
### 賢いコード

<!--
In general, readability is more important than cleverness or brevity.
 -->
一般にコードの読みやすさは賢さや短さよりも重要です。

```php
isset( $var ) || $var = some_function();
```
<!-- 
Although the above line is clever, it takes a while to grok if you're not familiar with it. So, just write it like this:
 -->
上のコードは賢いかもしれませんが、構文に慣れていなければ完全に理解するまで時間がかかります。それよりも次のように書くべきです。

```php
if ( ! isset( $var ) ) {
    $var = some_function();
}
```

<!-- 
Unless absolutely necessary, loose comparisons should not be used, as their behaviour can be misleading.

Correct:
 -->
本当に必要でない限り、緩やかな比較 (loose comparison) は、動作を誤解しやすいため、使用しないでください。

正しい:

```php
if ( 0 === strpos( $text, 'WordPress' ) ) {
    echo esc_html__( 'Yay WordPress!', 'textdomain' );
}
```
<!-- 
Incorrect:
 -->
間違い:

```php
if ( 0 == strpos( 'WordPress', 'foo' ) ) {
    echo esc_html__( 'Yay WordPress!', 'textdomain' );
}
```

<!-- 
Assignments must not be placed in conditionals.

Correct:
 -->
条件の中で代入しないでください。

正しい:

```php
$data = $wpdb->get_var( '...' );
if ( $data ) {
    // Use $data.
}
```

<!-- 
Incorrect:
 -->
間違い:

```php
if ( $data = $wpdb->get_var( '...' ) ) {
    // Use $data.
}
```

<!-- 
In a `switch` statement, it's okay to have multiple empty cases fall through to a common block. If a case contains a block, then falls through to the next block, however, this must be explicitly commented.
 -->
`switch` 文では、共通コードに落ちる複数の空白 case があっても構いません。しかし、case にコードがあって次のコードに落ちる場合にはその旨をコメントを記述してください。

<!-- 
```php
switch ( $foo ) {
    case 'bar':                // Correct, an empty case can fall through without comment.
    case 'baz':
        echo esc_html( $foo ); // Incorrect, a case with a block must break, return, or have a comment.
    case 'cat':
        echo 'mouse';
        break;                 // Correct, a case with a break does not require a comment.
    case 'dog':
        echo 'horse';
        // no break            // Correct, a case can have a comment to explicitly mention the fall through.
    case 'fish':
        echo 'bird';
        break;
}
```
 -->
```php
switch ( $foo ) {
	case 'bar':	      // 正しい。空白の case はコメントなしで次に落ちて良い。
	case 'baz':
		echo $foo;    // 間違い。コードを含む case は break または returnで終えるか、コメントを含む必要がある。
	case 'cat':
		echo 'mouse';
		break;        // 正しい。break のある case にコメントは不要。
	case 'dog':
		echo 'horse';
		// no break   // 正しい。次に落ちる旨を明確に記述したコメントがある。
	case 'fish':
		echo 'bird';
		break;
}
```
<!-- 
The `goto` statement must never be used.

The `eval()` construct is _very dangerous_ and is impossible to secure. Additionally, the `create_function()` function, which internally performs an `eval()`, is deprecated since PHP 7.2 and has been removed in PHP 8.0. Neither of these must be used.
 -->
`goto` 文は決して使わないでください。

`eval()` 言語構造は **非常に危険** で、安全性を保つことが不可能です。また `create_function()` 関数は内部的に `eval()` を実行し、PHP 8.0 では両方とも削除されました。両方の関数を使わないでください。


<!-- 
### Closures (Anonymous Functions)
 -->
### クロージャー (無名関数)

<!-- 
Where appropriate, closures may be used as an alternative to creating new functions to pass as callbacks. For example:
 -->
必要であれば、コールバックに渡す際、新規に関数を作成する代わりにクロージャーを使うことができます。例えば、

```php
$caption = preg_replace_callback(
    '/<[a-zA-Z0-9]+(?: [^<>]+>)*/',
    function ( $matches ) {
        return preg_replace( '/[\r\n\t]+/', ' ', $matches[0] );
    },
    $caption
);
```

<!-- 
Closures should not be passed as filter or action callbacks, as removing these via `remove_action()` / `remove_filter()` is complex (at this time)  (see [#46635](https://core.trac.wordpress.org/ticket/46635 "Improve identifying of non–trivial callbacks in hooks") for a proposal to address this).
 -->
クロージャーをフィルターやアクションのコールバックとして渡さないでください。`remove_action()` / `remove_filter()` による削除は、現時点では、複雑です (この問題を解決する提案については [#46635](https://core.trac.wordpress.org/ticket/46635 "Improve identifying of non–trivial callbacks in hooks (フック内の自明でないコールバックの識別の改良)") を参照してください)。

<!-- 
### Regular Expressions
 -->
### 正規表現

<!-- 
Perl compatible regular expressions ([PCRE](https://www.php.net/pcre), `preg_` functions) should be used in preference to their POSIX counterparts. Never use the `/e` switch, use `preg_replace_callback` instead.

It's most convenient to use single-quoted strings for regular expressions since, contrary to double-quoted strings, they have only two metasequences which need escaping: `\'` and `\\`.
 -->
POSIX 互換関数 ではなく、Perl 互換の正規表現 ([PCRE](http://php.net/pcre) `preg_` 関数) を使用してください。決して「`/e`」修飾子は使わず、代わりに「`preg_replace_callback`」を使用してください。

正規表現には、一重引用符で囲む文字列を使用するほうが便利です。二重引用符で囲む文字列とは異なり、一重引用符で囲む文字列には、エスケープが必要なものは、2つのメタシークエンス「`\’`」と「`\\`」しかないためです。

<!-- 
### Don't `extract()`
 -->
### extract() は使わない

<!-- 
Per [#22400](https://core.trac.wordpress.org/ticket/22400 "Remove all, or at least most, uses of extract() within WordPress"):

> `extract()` is a terrible function that makes code harder to debug and harder to understand. We should discourage it's [sic] use and remove all of our uses of it.

Joseph Scott has [a good write-up of why it's bad](https://blog.josephscott.org/2009/02/05/i-dont-like-phps-extract-function/).
 -->
[#22400: Remove all, or at least most, uses of extract() within WordPress](https://core.trac.wordpress.org/ticket/22400) によれば、

> `extract()` はひどい関数。コードはデバッグしにくいし、読みにいし。使うのは禁止して、中で使ってるのも全部削除しよう。

Joseph Scott が [何がそんなにひどいのかを書いています](https://blog.josephscott.org/2009/02/05/i-dont-like-phps-extract-function/)。

<!-- 
<h2>Credits</h2>
 -->
<!-- 
## クレジット
 -->
<!-- 
<ul>
 	<li>PHP standards: <a href="http://pear.php.net/manual/en/standards.php" target="_blank">Pear standards</a></li>
</ul>
 -->
<!-- 
- PHP 規約: [Pear standards](http://pear.php.net/manual/en/standards.php)
 -->
<!-- 
<h3>Major Changes</h3>
 -->
<!-- 
### 主な変更
 -->
<!-- 
<ul>
 	<li>November 13, 2013: <a href="http://make.wordpress.org/core/2013/11/13/proposed-coding-standards-change-always-require-braces/">Braces should always be used, even when they are optional</a></li>
 	<li>June 20, 2014: Add <a href="#error-control-operator">section</a> to discourage use of the <a href="http://www.php.net//manual/en/language.operators.errorcontrol.php">error control operator</a> (<code>@</code>). See <a href="https://irclogs.wordpress.org/chanlog.php?channel=wordpress-dev&amp;day=2014-06-20&amp;sort=asc#m873356">#wordpress-dev</a>.</li>
 	<li>October 20, 2014: Update brace usage to indicate that the alternate syntax for control structures is allowed, even encouraged. It is single-line inline control structures that are forbidden.</li>
 	<li>January 21, 2014: Add section to forbid extract().</li>
</ul>
 -->

<!-- 
- 2013/11/13: [ブレースは常に使う。オプションの場合でも使う](https://make.wordpress.org/core/2013/11/13/proposed-coding-standards-change-always-require-braces/)。
- 2014/6/20: 「エラー制御演算子 @」の説明を追加。[エラー制御演算子 (@)](http://www.php.net//manual/en/language.operators.errorcontrol.php) の使用は禁止。参照 [#wordpress-dev](https://irclogs.wordpress.org/chanlog.php?channel=wordpress-dev&day=2014-06-20&sort=asc#m873356)。
- 2014/10/20: ブレースの更新 – 「制御構造に関する別の構文」の使用の許可、というか推奨。禁じられた「単一行のインライン制御構造」。
- 2014/1/21: extract() 禁止を追加
 -->

[原文](https://github.com/WordPress/wpcs-docs/blob/master/wordpress-coding-standards/php.md) / [日本語訳](https://github.com/jawordpressorg/wpcs-docs/blob/master/wordpress-coding-standards/php.md)

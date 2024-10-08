<!-- 
# PHP Coding Standards
 -->
# PHP コーディング規約

<!-- 
These PHP coding standards are intended for the WordPress community as a whole. They are mandatory for WordPress Core and we encourage you to use them for your themes and plugins as well.

While themes and plugins may choose to follow a different _coding style_, these **_coding standards_** are not just about _code style_, but also encompass established best practices regarding interoperability, translatability, and security in the WordPress ecosystem, so, even when using a different _code style_, we recommend you still adhere to the WordPress Coding Standards in regard to these best practices.
 -->
PHP コーディング規約は、WordPress コミュニティ全体を対象としています。規約の遵守は WordPress コアでは必須、テーマやプラグインでも同様に使用を推奨します。

テーマやプラグインは別の _コーディングスタイル_ を選択できますが、この **コーディング規約** は、単なる _コーディングスタイル_ ではなく、WordPress エコシステムの相互運用性、翻訳、セキュリティに関する確立したベストプラクティスを包含するものです。別の _コーディングスタイル_ を使用する場合でも、このベストプラクティスに関しては WordPress コーディング規約を遵守することを推奨します。

<!-- 
While not all code may fully comply with these standards (yet), all newly committed and/or updated code should fully comply with these coding standards.

Also see the [PHP Inline Documentation Standards](https://developer.wordpress.org/coding-standards/inline-documentation-standards/php/) for further guidelines.
 -->
すべてのコードは、(まだ) この規約に完全に準拠していませんが、新しくコミットされたコードや更新されたコードは、コーディング規約に完全に準拠する必要があります。

また、[PHP インラインドキュメント規約](https://ja.wordpress.org/team/handbook/coding-standards/inline-documentation-standards/php/)も参照してください。

<!-- 
If you want to automatically check your code against this standard, you can use the official [WordPress Coding Standards](https://github.com/WordPress/WordPress-Coding-Standards) tooling, which is run using [PHP_CodeSniffer](https://github.com/PHPCSStandards/PHP_CodeSniffer/).
 -->
この規約への準拠を自動的にチェックしたい場合は、[PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer/) を使用して実行する公式の [WordPress Coding Standards](https://github.com/WordPress/WordPress-Coding-Standards) ツールを使用してください。

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
### Writing include/require statements
 -->
### include 文、require 文の記述

<!-- 
Because `include[_once]` and `require[_once]` are language constructs, they do not need parentheses around the path, so those shouldn't be used. There should only be one space between the path and the include/require keywords.
 -->
`include[_once]` と `require[_once]` は言語構成要素のため、パスを括弧で囲む必要はありません。パスと include キーワード、require キーワードの間には、スペースを1つだけ挿入してください。

<!-- 
It is _strongly recommended_ to use `require[_once]` for unconditional includes. When using `include[_once]`, PHP will throw a warning when the file is not found but will continue execution, which will almost certainly lead to other errors/warnings/notices being thrown if your application depends on the file loaded, potentially leading to security leaks. For that reason, `require[_once]` is generally the better choice as it will throw a `Fatal Error` if the file cannot be found.
 -->
無条件のインクルードには `require[_once]` を使用することを _強く推奨_ します。`include[_once]` を使用すると、PHP はファイルが見つからなければ警告を投げますが、処理は続行します。アプリケーションが読み込むファイルに依存する場合、ほぼ間違いなく他のエラー、警告、通知がスローされ、潜在的にはセキュリティリークにつながります。そのため、一般には `require[_once]` の方が良い選択です。ファイルが見つからなければ `Fatal Error` がスローされます。

```php
// 正しい
require_once ABSPATH . 'file-name.php';

// 間違い
include_once  ( ABSPATH . 'file-name.php' );
require_once     __DIR__ . '/file-name.php';
```

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
function some_name( $some_variable ) {}
```

<!-- 
For function parameter names, it is _strongly recommended_ to avoid reserved keywords as names, as it leads to hard to read and confusing code when using the PHP 8.0 "named parameters in function calls" feature.
Also keep in mind that renaming a function parameter should be considered a breaking change since PHP 8.0, so name function parameters with due care!
 -->
関数の引数名には、予約キーワードを使わないことを _強く推奨_ します。これは PHP 8.0の「関数呼び出し内の名前付き引数」機能を使用する際に、読みづらく、混乱したコードになるためです。
また、関数の引数名を変更することは PHP 8.0以降は破壊的な変更と見なされることに注意してください。

<!-- 
Class, trait, interface and enum names should use capitalized words separated by underscores. Any acronyms should be all upper case.
 -->
クラス名、トレイト名、インターフェース名、列挙体名は、大文字で始まる単語をアンダースコアで区切ります。省略語はすべて大文字にします。

```php
class Walker_Category extends Walker {}
class WP_HTTP {}

interface Mailer_Interface {}
trait Forbid_Dynamic_Properties {}
enum Post_Status {}
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
This file-naming standard is for all current and new files with classes, except test classes.
For files containing test classes, the file name should reflect the class name exactly, as per PSR4. This is to ensure cross-version [compatibility with all supported PHPUnit versions](https://github.com/sebastianbergmann/phpunit/pull/4109).
 -->
このファイルの命名規則は、テスト用のクラスを除いて、クラスを含むすべての現行および新規のファイルに適用されます。テストクラスを含むファイルについては PSR4 に従ってファイル名にクラス名を正確に反映しなければなりません。これにより、[すべてのサポート PHPUnit バージョンにおけるバージョン間の互換性](https://github.com/sebastianbergmann/phpunit/pull/4109) が保証されます。

<!-- 
Files containing template tags in the `wp-includes` directory should have `-template` appended to the end of the name so that they are obvious.
 -->
`wp-includes` ディレクトリ内のテンプレートタグを含むファイルには、分かりやすさのため名前の末尾に `-template` を付けてくだださい。

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

フックタグで使用される変数は中括弧(「{」と「}」)で囲み、完全なタグ名全体をダブルクォートで囲んでください。こうすると PHP は、挿入された文字列内で指定された変数の型を正しくパースできます。

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
Always put spaces after commas, and on both sides of logical, arithmetic, comparison, string and assignment operators.
 -->
コンマの後ろや、論理演算子、比較演算子、算術演算子、比較演算子、文字列演算子、代入演算子の両側には、常にスペース (空白文字) を入れてください。

```php
SOME_CONST === 23;
foo() && bar();
! $foo;
array( 1, 2, 3 );
$baz . '-5';
$term .= 'X';
if ( $object instanceof Post_Type_Interface ) {}
$result = 2 ** 3; // 8.
```

<!-- 
Put spaces on both sides of the opening and closing parentheses of control structure blocks.
 -->
制御構造ブロックの開き括弧、閉じ括弧の両側にも入れてください。

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
<!-- 
同様に、戻りの型の宣言のコロンの前にスペースを置かないでください。

```php
function sum( $a, $b ): float {
    return $a + $b;
}
```
 -->
<!-- 
Unless otherwise specified, parentheses should have spaces inside them.
 -->
特に指定のない限り、括弧はそれぞれの内側にスペースを置いてください。

```php
if ( $foo && ( $bar || $baz ) ) { ...

my_function( ( $x - 1 ) * 5, $y );
```

<!-- 
When using increment (`++`) or decrement (`--`) operators, there should be no spaces between the operator and the variable it applies to.
 -->
加算子(`++`)または減算子(`--`)を使用するとき、演算子と適用する変数の間にスペースは挿入できません。

```php
// 正しい
for ( $i = 0; $i < 10; $i++ ) {}

// 間違い
for ( $i = 0; $i < 10; $i ++ ) {}
++   $b; // 複数のスペース
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

例外: コードブロックの可読性のために、必要であれば、スペースを使用してください。

```php
[tab]$foo   = 'somevalue';
[tab]$foo2  = 'somevalue2';
[tab]$foo34 = 'somevalue3';
[tab]$foo5  = 'somevalue4';
```
<!-- 
For associative arrays, _each item_ should start on a new line when the array contains more than one item:
 -->
連想配列で複数の要素を含む場合、_各項目_ を、新しい行で始めてください。

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
There should be no trailing blank lines at the end of a function body.
 -->
関数本体の末尾の空白行は削除してください。

<!-- 
## Formatting
 -->
## フォーマット

<!-- 
### Brace Style
 -->
### ブレース (波括弧、中括弧) の形式

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
その上で非常に長いブロックがあれば、複数の短いブロック、関数、メソッドに分割できないかを検討してください。分割することで複雑度を解消し、テストしやすくなり、可読性を向上できます。

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
### Type declarations
 -->
### 型宣言

<!-- 
Type declarations must have exactly one space before and after the type. The nullability operator (`?`) is regarded as part of the type declaration and there should be no space between this operator and the actual type. Class/interface/enum name based type declarations should use the case of the class/interface/enum name as declared, while the keyword-based type declarations should be lowercased.
 -->
型宣言では型の前後に、正確に1つのスペースを挿入しなければなりません。nullabile な演算子 (`?`) は型宣言の一部とみなされ、この演算子と実際の型の間にスペースは挿入できません。クラス名、インターフェース名、列挙体名に基づく型宣言では、これらの名前の宣言と同じ大文字、小文字を使用する必要があります。一方、キーワードに基づく型宣言では、小文字を使用しなければなりません。

<!-- 
Return type declarations should have no space between the closing parenthesis of the function declaration and the colon starting a return type.
 -->
戻り値の型宣言では関数宣言の閉じ括弧と、戻り値の型を始めるコロンの間にスペースを挿入しないでください。

<!-- 
These rules apply to all structures allowing for type declarations: functions, closures, enums, catch conditions as well as the PHP 7.4 arrow functions and typed properties.
 -->
以上のルールは型宣言を許可するすべての構造に適用されます: 関数、クロージャ、列挙型、catch 条件、PHP 7.4のアロー関数、型付きプロパティ。

```php
// 正しい
function foo( Class_Name $parameter, callable $callable, int $number_of_things = 0 ) {
    // 何かを実行する
}

function bar(
    Interface_Name&Concrete_Class $param_a,
    string|int $param_b,
    callable $param_c = 'default_callable'
): User|false {
    // 何かを実行する
}

// 間違い
function baz(Class_Name $param_a, String$param_b,      CALLABLE     $param_c )   :   ?   iterable   {
    // 何かを実行する
}
```

<!-- 
[info]
Type declaration usage has the following restrictions based on the minimum required PHP version of an application, whether it is WordPress Core, a plugin or a theme:
 -->
型宣言の使用には、WordPress コア、プラグイン、テーマのいずれであっても、アプリケーションに最低限必要な PHP バージョンに基づく以下の制限があります：

<!-- 
- The scalar `bool`, `int`, `float`, and `string` type declarations cannot be used until the minimum PHP version is PHP 7.0 or higher.
- Return type declarations cannot be used until the minimum PHP version is PHP 7.0 or higher.
- Nullable type declarations cannot be used until the minimum PHP version is PHP 7.1 or higher.
- The `iterable` and `void` type declarations cannot be used until the minimum PHP version is PHP 7.1 or higher. The `void` type can only be used as a return type.
- The `object` type declaration cannot be used until the minimum PHP version is PHP 7.2 or higher.
- Property type declarations cannot be used until the minimum PHP version is PHP 7.4 or higher.
- `static` (return type only) cannot be used until the minimum PHP version is PHP 8.0 or higher.
- `mixed` type cannot be used until the minimum PHP version is PHP 8.0 or higher. Take note that the `mixed` type includes `null`, so cannot be made nullable.
- Union types cannot be used until the minimum PHP version is PHP 8.0 or higher.
- Intersection types cannot be used until the minimum PHP version is PHP 8.1 or higher.
- `never` (return type only) cannot be used until the minimum PHP version is PHP 8.1 or higher.
- Disjunctive normal form types (combining union types and intersection types) cannot be used until the minimum PHP version is PHP 8.2 or higher.
[/info]
 -->
- スカラー型 `bool`、`int`、`float`、`string` の型宣言は、サポートする最低バージョンが PHP 7.0 以降になるまでは使用できません。
- 戻り値の型宣言は、サポートする最低バージョンが PHP 7.0 以降になるまでは使用できません。
- Nullable 型の宣言は、サポートする最低バージョンが PHP 7.1 以降になるまでは使用できません。
- `iterable` および `void` 型の宣言は、サポートする最低バージョンが PHP 7.1 以降になるまでは使用できません。`void` 型は戻り値としてのみ使用できます。
- `object` 型の宣言は、サポートする最低バージョンが PHP 7.2 以降になるまでは使用できません。
- プロパティの型宣言は、サポートする最低バージョンが PHP 7.4 以降になるまでは使用できません。
- `static` 型 (戻り値の型のみ) は、サポートする最低バージョンが PHP 8.0 以降になるまでは使用できません。
- `mixed` 型は、サポートする最低バージョンが PHP 8.0 以降になるまでは使用できません。注意: `mixed` 型には `null` が含まれるため、nullable にはできません。
- union 型は、サポートする最低バージョンが PHP 8.0 以降になるまでは使用できません。
- 交差型は、サポートする最低バージョンが PHP 8.1 以降になるまでは使用できません。
- `never` 型 (戻り値の型のみ) は、サポートする最低バージョンが PHP 8.1 以降になるまでは使用できません。
- 選言標準形 (論理和型と論理積型の組み合わせ) は、サポートする最低バージョンが PHP 8.2 以降になるまでは使用できません。

<!-- 
_Usage in WordPress Core_
 -->
_WordPress コアでの使用_

<!-- 
[warning]
Adding type declarations to existing WordPress Core functions should be done with extreme care.
[/warning]
 -->
> 警告: 既存のWordPress コアの関数への型宣言の追加は、細心の注意を払ってください。

<!-- 
The function signature of any function (method) which can be overloaded by plugins or themes should not be touched.
This leaves, for now, only unconditionally declared functions in the global namespace, `private` class methods, and code new to Core, as candidates for adding type declarations.
 -->
プラグインやテーマで上書きされる可能性のある関数 (メソッド) のシグネチャは、触るべきではありません。
現時点で型宣言を追加する余地があるものは、グローバル名前空間で無条件に宣言された関数、`private` クラスのメソッド、コアに新しく追加されたコードだけです。

<!-- 
Note: Using the `array` keyword in type declarations is **strongly discouraged** for now, as most often, it would be better to use `iterable` to allow for more flexibility in the implementation and that keyword is not yet available for use in WordPress Core until the minimum requirements are raised to PHP 7.1.
 -->
注意：型宣言で `array` キーワードを使用することは、現時点で **強く推奨されません** 。ほとんどの場合、`iterable` を使用した方が実装の柔軟性が高くなりますし、このキーワードは最低要件が PHP 7.1 に上がるまで WordPress コアでは使用できません。

<!-- 
### Magic constants
 -->
### マジック定数

<!-- 
The [PHP native `__*__` magic constants](https://www.php.net/manual/en/language.constants.magic.php), like `__CLASS__` and `__DIR__`, should be written in uppercase when used.
 -->
[PHP ネイティブの `__*__` マジック定数](https://www.php.net/manual/en/language.constants.magic.php)、例えば `__CLASS__` や `__DIR__` は大文字でなければなりません。

<!-- 
When using the `::class` constant for class name resolution, the `class` keyword should be in lowercase and there should be no spaces around the `::` operator.
 -->
クラス名の解決に `::class` 定数を使用する場合、`class` キーワードは小文字にし、`::` 演算子の前後にはスペースを入れないでください。

```php
// 正しい
add_action( 'action_name', array( __CLASS__, 'method_name' ) );
add_action( 'action_name', array( My_Class::class, 'method_name' ) );

// 間違い
require_once __dIr__ . '/relative-path/file-name.php';
add_action( 'action_name', array( My_Class :: CLASS, 'method_name' ) );
```

<!-- 
### Spread operator `...`
 -->
### スプレッド演算子 `...`

<!-- 
When using the spread operator, there should be one space or a new line with the appropriate indentation before the spread operator. There should be no spaces between the spread operator and the variable/function call it applies to. When combining the spread operator with the reference operator (`&`), there should be no spaces between them.
 -->
スプレッド演算子を使用する場合、スプレッド演算子の前にスペースを1つ空けるか、適切なインデントで改行しなければなりません。スプレッド演算子とそれが適用される変数、関数呼び出しの間にはスペースを挿入しないでください。スプレッド演算子と参照演算子 (`&`) を組み合わせる場合も、その間にスペースを挿入しないでください。

```php
// 正しい
function foo( &...$spread ) {
    bar( ...$spread );

    bar(
        array( ...$foo ),
        ...array_values( $keyed_array )
    );
}

// 間違い
function fool( &   ... $spread ) {
    bar(...
             $spread );

    bar(
        [...  $foo ],... array_values( $keyed_array )
    );
}
```

<!-- 
[info]
The spread operator (or splat operator as it's known in other languages) can be used for packing arguments in function declarations (variadic functions) and unpacking them in function calls as of PHP 5.6. Since PHP 7.4, the spread operator is also used for unpacking numerically-indexed arrays, with string-keyed array unpacking available since PHP 8.1.
When used in a function declaration, the spread operator can only be used with the last parameter.
[/info]
 -->
> メモ: スプレッド演算子 (他の言語では splat 演算子として知られる) は、PHP 5.6以降で、関数宣言 (可変長引数関数) での引数のパックや関数呼び出しでの引数のアンパックに使用できます。PHP 7.4以降では、スプレッド演算子は数値添字付き配列のアンパックに、PHP 8.1以降では文字列キー付き配列のアンパックにも使用できます。
> 関数宣言で使用する場合、スプレッド演算子は、最後のパラメータでのみ使用できます。

<!-- 
## Declare Statements, Namespace, and Import Statements
 -->
## 文、名前空間、インポート文の宣言

<!-- 
### Namespace declarations
 -->
### 名前空間の宣言

<!-- 
Each part of a namespace name should consist of capitalized words separated by underscores.

Namespace declarations should have exactly one blank line before the declaration and at least one blank line after.
 -->
名前空間の名前は、先頭が大文字の単語と、アンダースコアの区切りから構成してください。

名前空間の宣言は、宣言の前に正確に1行の空白行を入れ、宣言の後に少なくとも1行の空白行を入れてください。

<!-- 
```php
namespace Prefix\Admin\Domain_URL\Sub_Domain\Event; // Correct.
```
 -->
```php
namespace Prefix\Admin\Domain_URL\Sub_Domain\Event; // 正しい
```

<!-- 
There should be only one namespace declaration per file, and it should be at the top of the file. Namespace declarations using curly brace syntax are not allowed. Explicit global namespace declaration (namespace declaration without name) are also not allowed.
 -->
名前空間の宣言は1ファイルにつき1つだけとし、ファイルの先頭に記述してください。中括弧を使用した名前空間宣言は使用できません。明示的なグローバル名前空間宣言 (名前のない名前空間宣言) も使用できません。

```php
// 間違い: 中括弧構文を使用した名前空間宣言
namespace Foo {
    // コード
}

// 間違い: グローバル名前空間での名前空間宣言
namespace {
    // コード
}
```

<!-- 
_There is currently no timeline for introducing namespaces to WordPress Core._

The use of namespaces in plugins and themes is strongly encouraged. It is a great way to prefix a lot of your code to prevent naming conflicts with other plugins, themes and/or WordPress Core.

Please do make sure you use a unique and long enough namespace prefix to actually prevent conflicts. Generally speaking, using a namespace prefix along the lines of `Vendor\Project_Name` is a good idea.
 -->
_WordPress コアへの名前空間の導入時期は、現在、未定です。_

プラグインやテーマでの名前空間の使用を強く推奨します。他のプラグインやテーマ、WordPress コアとの名前の衝突を防ぐために、できるだけ多くのコードに接頭辞を付けてください。

ただし、競合を防ぐために、十分な長さのユニークな名前空間接頭辞を使用してください。一般には、`Vendor\Project_Name`のような、会社名とプロジェクト名の組み合わせの名前空間接頭辞を使用すると良いでしょう。

<!-- 
[warning]
The `wp` and `WordPress` namespace prefixes are reserved for WordPress itself.
[/warning]
 -->
**警告**: 名前空間接頭辞 `wp` と `WordPress` は WordPress 用に予約されています。 

<!-- 
[info]
Namespacing has no effect on variables, constants declared with `define()` or non-PHP native constructs, like the hook names as used in WordPress.
Those still need to be prefixed individually.
[/info]
 -->
> 名前空間は、変数、`define()`で宣言された定数、WordPress で使用されるフック名などの非 PHP ネイティブな構成要素には影響しません。
> これらには、従来どおり個別に接頭辞をつける必要があります。

<!-- 
### Using import `use` statements
 -->
### インポートの `use` 文の使用

<!-- 
Using import `use` statements allows you to refer to constants, functions, classes, interfaces, namespaces, enums and traits that live outside of the current namespace.
 -->
インポートの `use` 文を使用すると、現在の名前空間の外にある定数、関数、クラス、インターフェース、名前空間、列挙型、トレイトを参照できます。

<!-- 
Import `use` statements should be at the top of the file and follow the (optional) `namespace` declaration. They should follow a specific order based on the **type** of the import:
 -->
インポートの `use` 文はファイルの先頭に記述し、オプションで `namespace` 宣言の後に記述します。これらはインポートの **タイプ** に基づいた特定の順序に従う必要があります。

<!-- 
1. `use` statements for namespaces, classes, interfaces, traits and enums
2. `use` statements for functions
3. `use` statements for constants
 -->
1. `use` 文 - 名前空間、クラス、インターフェース、トレイト、列挙型
2. `use` 文 - 関数
3. `use` 文 - 定数

<!-- 
Aliases can be used to prevent name collisions (two classes in different namespaces using the same class name).
When using aliases, make sure the aliases follow the WordPress naming convention and are unique.
 -->
エイリアスは使用できます。異なる名前空間の2つのクラスが同じクラス名を使用することで生じる、名前の衝突を防止できます。
エイリアスを使用する場合は WordPress の命名規則に従い、一意であることを確認してください。

<!-- 
The following examples showcase the correct and incorrect usage of import `use` statements regarding things like spacing, groupings, leading backslashes, etc.
 -->
以下の例では、スペース、グループ化、先頭のバックスラッシュなど、インポートの `use` 文の正しい使い方と間違った使い方を紹介しています。

<!-- 
Correct:
 -->
正しい:

```php
namespace Project_Name\Feature;

use Project_Name\Sub_Feature\Class_A;
use Project_Name\Sub_Feature\Class_C as Aliased_Class_C;
use Project_Name\Sub_Feature\{
    Class_D,
    Class_E as Aliased_Class_E,
}

use function Project_Name\Sub_Feature\function_a;
use function Project_Name\Sub_Feature\function_b as aliased_function;

use const Project_Name\Sub_Feature\CONSTANT_A;
use const Project_Name\Sub_Feature\CONSTANT_D as ALIASED_CONSTANT;

// 残りのコード
```

<!-- 
Incorrect:
 -->
間違い:

```php
namespace Project_Name\Feature;

use   const   Project_Name\Sub_Feature\CONSTANT_A; // use と const キーワードの後に余計なスペース
use function Project_Name\Sub_Feature\function_a; // 定数インポートの後に関数インポート
use \Project_Name\Sub_Feature\Class_C as aliased_class_c; // 先頭にバックスラッシュは使えない。エイリアスが命名規則に従っていない。
use Project_Name\Sub_Feature\{Class_D, Class_E   as   Aliased_Class_E} // as キーワードの前後に余計なスペース。中括弧内部の誤ったスペース
use Vendor\Package\{ function function_a, function function_b,
     Class_C,
        const CONSTANT_NAME}; // 1つの use 文中に異なるタイプのインポートが組み合わさっている。グループ use 文の中に誤ったスペース

class Foo {
    // コード
}

use const \Project_Name\Sub_Feature\CONSTANT_D as Aliased_constant; // クラス定義の後のインポート、先頭のバックスラッシュ、命名規則違反
use function Project_Name\Sub_Feature\function_b as Aliased_Function; // クラス定義の後のインポート、命名規則違反

// 残りのコード
```

<!-- 
[alert]
Import `use` statements have no effect on dynamic class, function or constant names.
Group `use` statements are available from PHP 7.0, and trailing commas in group `use` statements are available from PHP 7.2.
[/alert]
 -->
> 警告: インポートの `use` 文は動的なクラス、関数、定数名には影響しません。`use` 文のグループは PHP 7.0から使用可能です。グループの `use` 文の末尾にカンマをつけることは PHP 7.2から可能です。

<!-- 
[info]
Note that, unless you have implemented [autoloading](https://www.php.net/manual/en/language.oop5.autoload.php), the `use` statement won't automatically load whatever is being imported. You'll either need to set up autoloading or load the file containing the class/function/constant using a `require/import` statement, for the imported constructs to be loaded when used.
[/info]
 -->
> ヒント: [自動ロード](https://www.php.net/manual/en/language.oop5.autoload.php)を実装していない限り、`use` 文はインポートされるものを自動的にロードしないことに注意してください。インポートする構成要素を使用の際にロードするには、自動ロードをセットアップするか、`require/import` 文を使用してクラス、関数、定数を含むファイルをロードする必要があります。

<!-- 
**Note about WordPress Core usage**
 -->
**WordPress コアでの使用に関する注意**

<!-- 
While import `use` statements can already be used in WordPress Core, it is, for the moment, **strongly discouraged**.
 -->
WordPress コアではすでにインポートの `use` 文を使用できますが、現時点では**強く推奨されません**。

<!-- 
Import `use` statements are most useful when combined with namespaces and a class autoloading implementation.
As neither of these are currently in place for WordPress Core and discussions about this are ongoing, holding off on adding import `use` statements to WordPress Core is the sensible choice for now.
 -->
インポートの `use` 文は、名前空間やクラスの自動ロード実装と組み合わせたときに最も有用です。
現在、WordPress コアではこのどちらも実装されておらず、この件に関する議論が進行中です。このため WordPress コアではインポートの `use` 文の追加を控えることが、今のところ賢明な選択です。

<!-- 
## Object-Oriented Programming
 -->
## オブジェクト指向プログラミング

<!-- 
### Only One Object Structure (Class/Interface/Trait/Enum) per File
 -->
### ファイルごとに、1つのオブジェクト構造 (クラス、インターフェース、トレイト、列挙型)

<!-- 
For instance, if we have a file called `class-example-class.php` it can only contain one class in that file.
 -->
例えば、ファイル `class-example-class.php` には1つのクラスしか入れられません。

<!-- 
```php
// Incorrect: file class-example-class.php.
class Example_Class {}

class Example_Class_Extended {}
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
class Example_Class {}
```

```php
// Correct: file class-example-class-extended.php.
class Example_Class_Extended {}
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
### Trait Use Statements
 -->
### トレイトの use 文

<!-- 
Trait `use` statements should be at the top of a class and should have exactly one blank line before the first `use` statement, and at least one blank line after the last statement. The only exception is when the class only contains trait `use` statements, in which case the blank line after may be omitted.
 -->
トレイトの `use` 文はクラスの先頭に記述し、最初の `use` 文の前には正確に1行の空白行を、最後の `use` 文の後には少なくとも1行の空白行を記述します。唯一の例外は、クラスがトレイトの `use` 文のみを含む場合で、その場合は後ろの空白行を省略できます。

<!-- 
The following code examples show the formatting requirements for trait `use` statements regarding things like spacing, grouping and indentation.
 -->
以下のコード例では、スペース、グループ化、インデントなどに関して、トレイトの `use` 文に必要な書式を示します。

```php
// 正しい
class Foo {

    use Bar_Trait;
    use Foo_Trait,
        Bazinga_Trait {
        Bar_Trait::method_name insteadof Bar_Trait;
        Bazinga_Trait::method_name as bazinga_method;
    }
    use Loopy_Trait {
        eat as protected;
    }

    public $baz = true;

    ...
}

// 間違い
class Foo {
    // トレイトの use 文の前に空白行がない、use キーワードの後に複数のスペース。
    use       Bar_Trait;

    /*
     * トレイトのインポート時に複数のスペース、開き中括弧の後に開業なし。
     * エイリアスは置換するメソッドと同じ行でなければならない。
     */
    use Foo_Trait,   Bazinga_Trait{Bar_Trait::method_name    insteadof     Foo_Trait; Bazinga_Trait::method_name
        as     bazinga_method;
            }; // 不正なインデントの中括弧
    public $baz = true; // トレイトのインポートの後に空白行がない

    ...
}
```

<!-- 
### Visibility should always be declared
 -->
### アクセス権 (Visibility) を常に宣言する

<!-- 
For all constructs that allow it (properties, methods, class constants since PHP 7.1), visibility should be explicitly declared.
Using the `var` keyword for property declarations is not allowed.
 -->
アクセス権を宣言可能なすべての構成要素 (プロパティ、メソッド、PHP 7.1 以降のクラス定数) について、明示的にアクセス権を宣言しなければなりません。
プロパティの宣言に `var` キーワードは使用できません。

```php
// 正しい
class Foo {
    public $foo;

    protected function bar() {}
}

// 間違い
class Foo {
    var $foo;

    function bar() {}
}
```

<!-- 
_Usage in WordPress Core_
 -->
_WordPress コアでの使用_

<!-- 
Visibility for class constants can not be used in WordPress Core until the minimum PHP version has been raised to PHP 7.1.
 -->
WordPress コアでは、サポートするPHP の最小バージョンが PHP 7.1に上がるまでは、クラス定数のアクセス権を使用できません。

<!-- 
### Visibility and modifier order
 -->
### アクセス権 (Visibility) と修飾子の順番

<!-- 
When using multiple modifiers for a _class declaration_, the order should be as follows:
 -->
複数の修飾子を _クラス宣言_ に使用する場合、次の順序に従ってください。

<!-- 
1. First the optional `abstract` or `final` modifier.
2. Next, the optional `readonly` modifier.
 -->
1. まず、オプションの `abstract` または `final` 修飾子
2. 次に、オプションの `readonly` 修飾子

<!-- 
When using multiple modifiers for a _constant declaration_ inside object-oriented structures, the order should be as follows:
 -->
複数の修飾子をオブジェクト指向構造体の内部の _定数宣言_ に使用する場合、次の順序に従ってください。

<!-- 
1. First the optional `final` modifier.
2. Next, the visibility modifier.
 -->
1. まず、オプションの `final` 修飾子
2. 次に、アクセス権修飾子

<!-- 
When using multiple modifiers for a _property declaration_, the order should be as follows:
 -->
複数の修飾子を _プロパティ宣言_ に使用する場合、次の順序に従ってください。

<!-- 
1. First a visibility modifier.
2. Next, the optional `static` or `readonly` modifier (these keywords are mutually exclusive).
3. Finally, the optional `type` declaration.
 -->
1. まず、アクセス権修飾子
2. 次に、オプションの `static` または `readonly` 修飾子 (これらのキーワードは互いに排他的)
3. 最後に、オプションの `type` 宣言

<!-- 
When using multiple modifiers for a _method declaration_, the order should be as follows:
 -->
複数の修飾子を _メソッド宣言_ に使用する場合、次の順序に従ってください。

<!-- 
1. First the optional `abstract` or `final` modifier.
2. Then, a visibility modifier.
3. Finally, the optional `static` modifier.
 -->
1. まず、オプションの `abstract` または `final` 修飾子
2. 次に、アクセス権修飾子
3. 最後に、オプションの `static` 修飾子

```php
// 正しい
abstract readonly class Foo {
    private const LABEL = 'Book';

    public static $foo;

    private readonly string $bar;

    abstract protected static function bar();
}

// 間違い
class Foo {
    protected final const SLUG = 'book';

    static public $foo;

    static protected final function bar() {
        // コード
    };
}
```
<!-- 
[info]
- Visibility for OO constants can be declared since PHP 7.1.
- Typed properties are available since PHP 7.4.
- Readonly properties are available since PHP 8.1.
- `final` modifier for constants in object-oriented structures is available since PHP 8.1.
- Readonly classes are available since PHP 8.2.
[/info]
 -->
ヒント:
- OO 定数のアクセス権は、PHP 7.1 以降で宣言できます。
- 型付きプロパティは、PHP 7.4 以降で使用できます。
- リードオンリープロパティは、PHP 8.1 以降で使用できます。
- オブジェクト指向構造体内の定数の `final` 修飾子は、PHP 8.1 以降で使用できます。
- リードオンリークラスは、PHP 8.2 以降で使用できます。

<!-- 
### Object Instantiation
 -->
### オブジェクトのインスタンス化

<!-- 
When instantiating a new object instance, parenthesis must always be used, even when not strictly necessary.
There should be no space between the name of the class being instantiated and the opening parenthesis.
 -->
新しいオブジェクトインスタンスをインスタンス化するときは、厳密に必要でない場合でも、常に括弧を使用しなければなりません。
インスタンス化されるクラス名と始まりの括弧の間にはスペースを入れないでください。

```php
// 正しい
$foo = new Foo();
$anonymous_class = new class( $parameter ) { ... };
$instance = new static();

// 間違い
$foo = new Foo;
$anonymous_class = new class ( $input ) { ... };
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
上の例で1つ等号を忘れると、パースエラーが発生します (白状すると、熟練のコアメンバーでもやらかします)。定数 `true` に代入できないためです。もし条件式が `( $the_force = true )` であれば、代入は構文として正しく `1` を返し、結果 if 文は `true` と評価し、そして、しばらくバグと闘うことになるでしょう。

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
### Increment/decrement operators
 -->
### 加算子 / 減算子

<!-- 
Pre-increment/decrement should be favoured over post-increment/decrement for stand-alone statements.
 -->
スタンドアロンの文では、前置加算子、前置減算子が、後置加算子、後置減算子に優先します。

<!-- 
Pre-increment/decrement will increment/decrement and then return, while post-increment/decrement will return and then increment/decrement.
Using the "pre" version is slightly more performant and can prevent future bugs when code gets moved around.
 -->
前置加算子、前置減算子は、インクリメント、デクリメントしてから値を戻します。一方、後置加算子、後置減算子は値を戻してから、インクリメント、デクリメントします。
「前置」バージョンの方が若干パフォーマンスに優れ、また将来コードが移動したときのバグを防ぐことができます。

```php
// 正しい。前置減算子
--$a;

// 間違い。後置減算子
$a--;
```

<!-- 
## Database
 -->
## データベース

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

「`$wpdb->prepare()`」は SQL クエリのエスケープ、クォート、整数へのキャストを処理するメソッドです。`sprintf()` 書式のサブセットを使用します。 例:

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
The following placeholders can be used in the query string:
 --> 
クエリー文字列には次のプレースホルダーを使用できます:

- %d (整数)
- %f (浮動小数点数)
- %s (文字列)
- %i (識別子。例: テーブル名、フィールド名)

<!-- 
Note that these placeholders should not be 'quoted'! `$wpdb->prepare()` will take care of escaping and quoting for us. This makes it easy to see at a glance whether something has been escaped or not because it happens right when the query happens.
 -->
注意: これらのプレースホルダを「クォートで囲まない」でください。`wpdb->prepare()` がエスケープとクォートを実行します。これはクエリーが発生したときに実行されるため、エスケープされたかどうかが一目で分かります。

<!--
See [Data Validation](https://developer.wordpress.org/plugins/security/data-validation/) in the Plugin Handbook for further details.
 -->
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

`eval()` 構成要素は **非常に危険** で、安全性を保つことが不可能です。また `create_function()` 関数は内部的に `eval()` を実行し、PHP 8.0 では両方とも削除されました。両方の関数を使わないでください。


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

<!-- 
### Shell commands
 -->
### シェルコマンド

<!-- 
Use of the [backtick operator](https://www.php.net/manual/en/language.operators.execution.php) is not allowed.
 -->
[バッククォート演算子](https://www.php.net/manual/en/language.operators.execution.php) (「`」)の使用は認められません。

<!-- 
Use of the backtick operator is identical to [`shell_exec()`](https://www.php.net/manual/en/function.shell-exec.php), and most hosts disable this function in the `php.ini` file for security reasons.
 -->
バッククォート演算子の使用は、[`shell_exec()`](https://www.php.net/manual/en/function.shell-exec.php) と同じです。セキュリティ上の理由からほとんどのホスティング環境では `php.ini` ファイルでこの関数が無効にされています。

[原文](https://github.com/WordPress/wpcs-docs/blob/master/wordpress-coding-standards/php.md) / [日本語訳](https://github.com/jawordpressorg/wpcs-docs/blob/master/wordpress-coding-standards/php.md)

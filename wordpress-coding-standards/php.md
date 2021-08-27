<!-- 
# PHP Coding Standards
 -->
# PHP コーディング規約

<!-- 
Some parts of the WordPress code structure for PHP markup are inconsistent in their style. WordPress is working to gradually improve this by helping users maintain a consistent style so the code can become clean and easy to read at a glance.

Keep the following points in mind when writing PHP code for WordPress, whether for core programming code, plugins, or themes. The guidelines are similar to <a href="http://pear.php.net/manual/en/standards.php">Pear standards</a> in many ways, but differ in some key respects.

See also: <a href="https://developer.wordpress.org/coding-standards/inline-documentation-standards/php/">PHP Documentation Standards</a>.
 -->
WordPress の一部の PHP コードには一貫性に欠ける部分があります。WordPress ではユーザーの支援も得ながら徐々にこれらを改善し、コードをクリーンで読みやすいものにするよう努めています。

WordPress において PHP のコードを書く場合はこの規約に従ってください。これは WordPress コアのプログラミングだけではなく、プラグインやテーマの作成でも同様です。規約は多くの点で「[Pear standards](http://pear.php.net/manual/en/standards.php)」に似ていますが、一部異なる部分もあります。

[PHP インラインドキュメント規約](https://ja.wordpress.org/team/handbook/coding-standards/inline-documentation-standards/php/)も参照してください。

<!-- 
<h2>PHP</h2>
 -->
## PHP

<!-- 
<h3>Single and Double Quotes</h3>
 -->
### シングルクォートとダブルクォート

<!-- 
Use single and double quotes when appropriate. If you're not evaluating anything in the string, use single quotes. You should almost never have to escape quotes in a string, because you can just alternate your quoting style, like so:
 -->
シングルクォートとダブルクォートは適切に使い分けてください。文字列で何も評価しない場合は、シングルクォートを使用してください。クォートの種類を入れ替えれば済むため、文字列の中でエスケープを使用する必要はほとんどないはずです。

```php
echo '<a href="/static/link" title="Yeah yeah!">Link name</a>';
echo "<a href='$link' title='$linktitle'>$linkname</a>";
```

<!-- 
Text that goes into attributes should be run through <code>esc_attr()</code> so that single or double quotes do not end the attribute value and invalidate the HTML and cause a security issue. See <a href="http://codex.wordpress.org/Data_Validation">Data Validation</a> in the Codex for further details.
 -->
属性値の途中にシングルクォートやダブルクォートがあると属性値が途中で終了し、HTML は不正になり、セキュリティ問題を引き起こします。属性値は esc_attr() を通してください。詳細については「[データ検証](https://wpdocs.osdn.jp/%E3%83%87%E3%83%BC%E3%82%BF%E6%A4%9C%E8%A8%BC)」を参照してください。

<!-- 
<h3>Indentation</h3>
 -->
### インデント

<!-- 
Your indentation should always reflect logical structure. Use <strong>real tabs</strong> and <strong>not spaces</strong>, as this allows the most flexibility across clients.

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
For associative arrays, <em>each item</em> should start on a new line when the array contains more than one item:
 -->
連想配列では複数の要素を含む場合、値は新しい行から始めてください。

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
For <code>switch</code> structures <code>case</code> should indent one tab from the <code>switch</code> statement and <code>break</code> one tab from the <code>case</code> statement.
 -->
`switch` 構造では、`case` は `switch` 文から1タブ分インデントし、`break` は `case` 文から1タブ分インデントしてください。

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
<strong>Rule of thumb:</strong> Tabs should be used at the beginning of the line for indentation, while spaces can be used mid-line for alignment.
 -->
**ルール**: 行の先頭はタブでインデントし、途中を揃える場合にスペースを使用してください。

<!-- 
<h3>Brace Style</h3>
 -->
### ブレース (波かっこ) の形式

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
Note that requiring the use of braces just means that <em>single-statement inline control structures</em> are prohibited. You are free to use the <a href="http://php.net/manual/en/control-structures.alternative-syntax.php" rel="nofollow">alternative syntax for control structures</a> (e.g. <code>if</code>/<code>endif</code>, <code>while</code>/<code>endwhile</code>)—especially in your templates where PHP code is embedded within HTML, for instance:
 -->
注意: 「単一文のインライン制御構造」でのブレースは使用できません。「[制御構造に関する別の構文](http://php.net/manual/ja/control-structures.alternative-syntax.php)」は使用しても構いません (例: 「if」と「endif」、「while」と「endwhile」)。これらは特に、テンプレート内で HTML に PHPコードを埋め込む際に使用されます。

```php
<?php if ( have_posts() ) : ?>
	<div class="hfeed">
		<?php while ( have_posts() ) : the_post(); ?>
			<article id="post-<?php the_ID() ?>" class="<?php post_class() ?>">
				<!-- ... -->
			</article>
		<?php endwhile; ?>
	</div>
<?php endif; ?>
```
<!-- 
<h3>Use <code>elseif</code>, not <code>else if</code></h3>
 -->
### 「elseif」を使うこと。「else if」は使わない

<!-- 
<code>else if</code> is not compatible with the colon syntax for <code>if|elseif</code> blocks. For this reason, use <code>elseif</code> for conditionals.
 -->
「else if」は「if|elseif」ブロックのコロン構文と互換性がありません。条件式では「elseif」を使用してください。

<!-- 
<h3>Declaring Arrays</h3>
 -->
### 配列の宣言

<!-- 
Using long array syntax ( <code>array( 1, 2, 3 )</code> ) for declaring arrays is generally more readable than short array syntax ( <code>[ 1, 2, 3 ]</code> ), particularly for those with vision difficulties. Additionally, it's much more descriptive for beginners.

Arrays must be declared using long array syntax.
 -->
配列の宣言では、一般に長い配列構文 (array( 1, 2, 3 )) の方が短い配列構文 ([ 1, 2, 3 ]) よりも可読性に優れます。これは主に視覚的な面からから来ますが、加えて初心者にとっても分かりやすくなります。

配列は常に長い配列構文で宣言してください。

<!-- 
<h3>Closures (Anonymous Functions)</h3>
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
Closures must not be passed as filter or action callbacks, as they cannot be removed by <code>remove_action()</code> / <code>remove_filter()</code> (see <a href="https://core.trac.wordpress.org/ticket/46635">#46635</a> for a proposal to address this).
 -->
クロージャーをフィルターやアクションのコールバックとして渡すことはできません。これは `remove_action()` や `remove_filter()` で削除できないためです。この問題を解決する提案については [#46635](https://core.trac.wordpress.org/ticket/46635) を参照してください。

<!-- 
<h3>Multiline Function Calls</h3>
 -->
### 複数行での関数呼び出し

<!-- 
When splitting a function call over multiple lines, each parameter must be on a seperate line. Single line inline comments can take up their own line.

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
    esc_html__( 'Hello, %s!', 'yourtextdomain' ),
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
<h3>Regular Expressions</h3>
 -->
### 正規表現

<!-- 
Perl compatible regular expressions (<a href="http://php.net/pcre">PCRE</a>, <code>preg_</code> functions) should be used in preference to their POSIX counterparts. Never use the <code>/e</code> switch, use <code>preg_replace_callback</code> instead.
 -->
POSIX 互換関数 ではなく、Perl 互換の正規表現 ([PCRE](http://php.net/pcre) `preg_` 関数) を使用してください。決して「`/e`」修飾子は使わず、代わりに「`preg_replace_callback`」を使用してください。

<!-- 
It's most convenient to use single-quoted strings for regular expressions since, contrary to double-quoted strings, they have only two metasequences: <code>\'</code> and <code>\\</code>.
 -->
正規表現には、一重引用符で囲む文字列を使用するほうが便利です。二重引用符で囲む文字列とは異なり、一重引用符で囲む文字列には2つのメタシークエンス「`\’`」と「`\\`」しかないためです。

<!-- 
<h3>Opening and Closing PHP Tags</h3>
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
        echo bar(
            $baz,
            $bat
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
<h3>No Shorthand PHP Tags</h3>
 -->
### PHP ショートタグは禁止

<!-- 
<strong>Important:</strong> Never use shorthand PHP start tags. Always use full PHP tags.
 -->
**重要** 絶対に PHP のショートタグは使わないでください。

<!-- 
Correct:
 -->
正しい:

```php
<?php ... ?>
<?php echo $var; ?>
```
<!-- 
Incorrect:
 -->
間違い:

```php
<? ... ?>
<?= $var ?>
```

<!-- 
<h3>Remove Trailing Spaces</h3>
 -->
### 文末の空白の除去

<!-- 
Remove trailing whitespace at the end of each line of code. Omitting the closing PHP tag at the end of a file is preferred. If you use the tag, make sure you remove trailing whitespace.
 -->
コードの各行末尾のスペースは削除してください。ファイル末尾の PHP 終了タグの除去は推奨です。終了タグを使用する場合には、その後にスペースがないことを確認してください。

<!-- 
<h3>Space Usage</h3>
 -->
### スペースの使い方

<!-- 
Always put spaces after commas, and on both sides of logical, comparison, string and assignment operators.
 -->
コンマの後ろや、論理演算子、比較演算子、文字列演算子、代入演算子の両側には、常にスペースを入れてください。

```php
x === 23
foo && bar
! foo
array( 1, 2, 3 )
$baz . '-5'
$term .= 'X'
```

<!-- 
Put spaces on both sides of the opening and closing parentheses of <code>if</code>, <code>elseif</code>, <code>foreach</code>, <code>for</code>, and <code>switch</code> blocks.
 -->
「if」「elseif」「foreach」「for」「switch」ブロックの開きかっこ、閉じかっこの両側にも入れてください。

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
<a title="type casting" href="http://www.php.net/manual/en/language.types.type-juggling.php#language.types.typecasting" target="_blank">Type casts</a> must be lowercase. Always prefer the short form of type casts, <code>(int)</code> instead of <code>(integer)</code> and <code>(bool)</code> rather than <code>(boolean)</code>. For float casts use <code>(float)</code>.:
 -->
[型のキャスト](http://www.php.net/manual/en/language.types.type-juggling.php#language.types.typecasting) は小文字です。常に短い形式を使用してください。`(integer)` でなく `(int)`、`(boolean)` でなく `(bool)`。float については `(float)` を使用してください。

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
$x = $foo['bar']; // correct
$x = $foo[ 'bar' ]; // incorrect

$x = $foo[0]; // correct
$x = $foo[ 0 ]; // incorrect

$x = $foo[ $bar ]; // correct
$x = $foo[$bar]; // incorrect
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
In a <code>switch</code> block, there must be no space before the colon for a case statement.
 -->
`switch` ブロックでは、case 文のコロンの前にスペースを置かないでください。

<!-- 
```php
switch ( $foo ) {
	case 'bar': // correct
	case 'ba' : // incorrect
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
Unless otherwise specified, parentheses should have spaces inside of them.
 -->
特に指定のない限り、括弧はそれぞれの内側にスペースを置いてください。

```php
if ( $foo && ( $bar || $baz ) ) { ...

my_function( ( $x - 1 ) * 5, $y );
```

<!-- 
<h3>Formatting SQL statements</h3>
 -->
### SQL 文の書式

<!-- 
When formatting SQL statements you may break it into several lines and indent if it is sufficiently complex to warrant it. Most statements work well as one line though. Always capitalize the SQL parts of the statement like <code>UPDATE</code> or <code>WHERE</code>.

Functions that update the database should expect their parameters to lack SQL slash escaping when passed. Escaping should be done as close to the time of the query as possible, preferably by using <code>$wpdb-&gt;prepare()</code>

<code>$wpdb-&gt;prepare()</code> is a method that handles escaping, quoting, and int-casting for SQL queries. It uses a subset of the <code>sprintf()</code> style of formatting. Example :
 -->
SQL 文が非常に複雑な場合は、複数行に分割しインデントしても構いません。大部分の SQL 文は1行の場合と同様に動作するはずです。文の SQL の部分は「`UPDATE`」や「`WHERE`」のように常に大文字にしてください。

データベースを更新する関数は、渡されたパラメータが SQL 用にエスケープされていないと仮定して処理してください。エスケープはできるだけクエリの直前に、可能であれば「`$wpdb->prepare()`」を使用して実行してください。

「`$wpdb->prepare()`」は SQL クエリのエスケープ、クォート、整数へのキ ャストを処理するメソッドです。`sprintf()` 書式のサブセットを使用します。 例:

<!-- 
```php
$var = "dangerous'"; // raw data that may or may not need to be escaped
$id = some_foo_number(); // data we expect to be an integer, but we're not certain

$wpdb->query( $wpdb->prepare( "UPDATE $wpdb->posts SET post_title = %s WHERE ID = %d", $var, $id ) );
```
 -->
```php
$var = "dangerous'"; // 生データ。エスケープしてもしなくても良い
$id = some_foo_number(); // integer を期待するデータ。ただし確証はない

$wpdb->query( $wpdb->prepare( "UPDATE $wpdb->posts SET post_title = %s WHERE ID = %d", $var, $id ) );
```
<!-- 
<code>%s</code> is used for string placeholders and <code>%d</code> is used for integer placeholders. Note that they are not 'quoted'! <code>$wpdb-&gt;prepare()</code> will take care of escaping and quoting for us. The benefit of this is that we don't have to remember to manually use <code><a href="https://developer.wordpress.org/reference/functions/esc_sql/">esc_sql</a>()</code>, and also that it is easy to see at a glance whether something has been escaped or not, because it happens right when the query happens.

See <a title="Data Validation" href="http://codex.wordpress.org/Data_Validation" target="_blank">Data Validation</a> in the Codex for more information.
 -->
`%s` は文字列のプレースホルダーとして、`%d` は整数のプレースホルダーとして使用されます。注意: これらに「クォート」はありません。 「`$wpdb->prepare()`」がエスケープやクォートを実行します。この結果、毎回 [esc_sql()](https://developer.wordpress.org/reference/functions/esc_sql/) を使用する必要はありません。クエリを呼び出しさえすればエスケープは正しく処理されるため、各要素がエスケープされているかどうかを一々確認する必要もありません。

詳細については「[データ検証](https://wpdocs.osdn.jp/%E3%83%87%E3%83%BC%E3%82%BF%E6%A4%9C%E8%A8%BC)」を参照してください。

<!-- 
<h3>Database Queries</h3>
 -->
### データベースクエリ
<!-- 
Avoid touching the database directly. If there is a defined function that can get the data you need, use it. Database abstraction (using functions instead of queries) helps keep your code forward-compatible and, in cases where results are cached in memory, it can be many times faster.

If you must touch the database, get in touch with some developers by posting a message to the <a title="wp-hackers mailing list" href="http://codex.wordpress.org/Mailing_Lists#Hackers" target="_blank">wp-hackers mailing list</a>. They may want to consider creating a function for the next WordPress version to cover the functionality you wanted.
 -->
データベースには直接触らないでください。必要なデータを取得する関数があれば、それを使用してください。クエリの代わりに関数を使用したデータベースの抽象化を利用すると、コードは前方互換性を保ち、結果がメモリー内にキャッシュされる場合は何倍も速くなります。

データベースに触る必要があると考える場合は [wp-hackers メーリングリスト](http://codex.wordpress.org/Mailing_Lists#Hackers)にメッセージを投稿し、開発者と連携してください。必要な機能を備えた関数の作成が次の WordPress バージョンで検討されるかもしれません。

<!-- 
<h3>Naming Conventions</h3>
 -->
### 命名規則

<!-- 
Use lowercase letters in variable, action/filter, and function names (never <code>camelCase</code>). Separate words via underscores. Don't abbreviate variable names unnecessarily; let the code be unambiguous and self-documenting.
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
Class file names should be based on the class name with <code>class-</code> prepended and the underscores in the class name replaced with hyphens, for example <code>WP_Error</code> becomes:
 -->
クラスファイルの名前はクラス名を基にして、前に「class-」を付け、クラス名内部のアンダースコアはハイフンで置き換えます。 たとえば「WP_Error」の場合

```php
class-wp-error.php
```

<!-- 
This file-naming standard is for all current and new files with classes. There is one exception for three files that contain code that got ported into BackPress: class.wp-dependencies.php, class.wp-scripts.php, class.wp-styles.php. Those files are prepended with <code>class.</code>, a dot after the word class instead of a hyphen.

Files containing template tags in <code>wp-includes</code> should have <code>-template</code> appended to the end of the name so that they are obvious.
 -->
このファイル命名規則は、すべての現行のクラスファイル、将来のクラスファイルに適用されます。例外は BackPress に移植されたコードを含む3つのファイル「class.wp-dependencies.php」「class.wp-scripts.php」「class.wp-styles.php」で、これらは接頭辞が `class.` のように、ハイフンの代わりにドットで始まります。

`wp-includes` 内のテンプレートタグを含むファイルには、分かりやすさのため名前の末尾に `-template` を付けてくだださい。

```php
general-template.php
```
<!-- 
<h3>Only one object structure (class/interface/trait) should be declared per file</h3>
 -->
### 1つのファイルでは、1つのオブジェクト構造 (クラス、インターフェース、トレイト) のみを宣言する

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
<h3>Self-Explanatory Flag Values for Function Arguments</h3>
 -->
### 関数の引数には意味のあるフラグ値を使用する

<!-- 
Prefer string values to just <code>true</code> and <code>false</code> when calling functions.
 -->
関数を呼び出す場合は、単に `true` や `false` を使用するのではなく、文字列値を使用してください。

<!-- 
```php
// Incorrect
function eat( $what, $slowly = true ) {
...
}
eat( 'mushrooms' );
eat( 'mushrooms', true ); // what does true mean?
eat( 'dogfood', false ); // what does false mean? The opposite of true?
```
 -->
```
// 間違い
function eat( $what, $slowly = true ) {
...
}
eat( 'mushrooms' );
eat( 'mushrooms', true ); // true って、どういうこと?
eat( 'dogfood', false ); // false って、どういうこと? true の反対ってこと?
```

<!-- 
Since PHP doesn't support named arguments, the values of the flags are meaningless, and each time we come across a function call like the examples above, we have to search for the function definition. The code can be made more readable by using descriptive string values, instead of booleans.
 -->
PHP は名前付き引数をサポートしないためフラグの値には意味がありません。この結果、上のような例に出会うたびに関数定義を探す必要が出てきます。ブール値の代わりに説明的な文字列値を使用することで、コードは読みやすくなります。

<!-- 
```php
// Correct
function eat( $what, $speed = 'slowly' ) {
...
}
eat( 'mushrooms' );
eat( 'mushrooms', 'slowly' );
eat( 'dogfood', 'quickly' );
```
 -->
```
// 正しい
function eat( $what, $speed = 'slowly' ) {
...
}
eat( 'mushrooms' );
eat( 'mushrooms', 'slowly' );
eat( 'dogfood', 'quickly' );
```

<!-- 
When more words are needed to describe the function parameters, an <code>$args</code> array may be a better pattern.
 -->
関数パラメータに説明を加えたければ、配列 `$args` が良いパターンです。

<!-- 
```php
// Even Better
function eat( $what, $args ) {
...
}
eat ( 'noodles', array( 'speed' => 'moderate' ) );
```
 -->
```
// もっと良い
function eat( $what, $args ) {
...
}
eat ( 'noodles', array( 'speed' => 'moderate' ) );
```

<!-- 
<h3>Interpolation for Naming Dynamic Hooks</h3>
 -->
### ダイナミックフック名での変数展開の利用

<!-- 
Dynamic hooks should be named using interpolation rather than concatenation for readability and discoverability purposes.

Dynamic hooks are hooks that include dynamic values in their tag name, e.g. <code>{$new_status}_{$post-&gt;post_type}</code> (publish_post).

Variables used in hook tags should be wrapped in curly braces <code>{</code> and <code>}</code>, with the complete outer tag name wrapped in double quotes. This is to ensure PHP can correctly parse the given variables' types within the interpolated string.
 -->
ダイナミックフックの名前では読みやすさ、検索のしやすさのため、変数の連結でなく、展開を使用してください。

ダイナミックフックはタグ名に動的な値を含むフックです。例: `{$new_status}_{$post->post_type} (publish_post)`

フックタグで使用される変数は中括弧(「{」と「}」)で囲み、完全なタグ名全体をダブルクオートで囲んでください。こうすると PHP は、挿入された文字列内で指定された変数の型を正しくパースできます。

```php
do_action( "{$new_status}_{$post->post_type}", $post->ID, $post );
```
<!-- 
Where possible, dynamic values in tag names should also be as succinct and to the point as possible. <code>$user_id</code> is much more self-documenting than, say, <code>$this-&gt;id</code>.
 -->
このときタグ名内の動的な値はできるだけ簡潔で分かりやすいものにしてください。`$user_id` の方がたとえば `$this->id` などよりも明確です。

<!-- 
<h3>Ternary Operator</h3>
 -->
### 三項演算子

<!-- 
<a title="Ternary" href="http://en.wikipedia.org/wiki/Ternary_operation" target="_blank">Ternary</a> operators are fine, but always have them test if the statement is true, not false. Otherwise, it just gets confusing. (An exception would be using <code>! empty()</code>, as testing for false here is generally more intuitive.)

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
<h3>Yoda Conditions</h3>
 -->
### ヨーダ記法

```php
if ( true === $the_force ) {
	$victorious = you_will( $be );
}
```

<!-- 
When doing logical comparisons involving variables, always put the variable on the right side and put constants, literals, or function calls on the left side. If neither side is a variable, the order is not important. (In <a href="https://en.wikipedia.org/wiki/Value_(computer_science)#Assignment:_l-values_and_r-values">computer science terms</a>, in comparisons always try to put l-values on the right and r-values on the left.)

In the above example, if you omit an equals sign (admit it, it happens even to the most seasoned of us), you'll get a parse error, because you can't assign to a constant like <code>true</code>. If the statement were the other way around <code>( $the_force = true )</code>, the assignment would be perfectly valid, returning <code>1</code>, causing the if statement to evaluate to <code>true</code>, and you could be chasing that bug for a while.

A little bizarre, it is, to read. Get used to it, you will.

This applies to ==, !=, ===, and !==. Yoda conditions for &lt;, &gt;, &lt;= or &gt;= are significantly more difficult to read and are best avoided.
 -->
変数を伴う論理比較を行う場合、常に変数を右側に、定数や文字列や関数呼び出しを左側に置いてください。どちらも変数でなければ、順序は重要ではありません ([コンピューターサイエンスの言葉](https://en.wikipedia.org/wiki/Value_(computer_science)#Assignment:_l-values_and_r-values)では、比較時、常に l-value を右意、r-value を左に置きます)。

上の例で1つ等号を忘れると (白状すると、熟練のコアメンバーでもやらかします)、定数 `true` に代入できないためパースエラーが発生します。もし条件式が `( $the_force = true )` であれば、代入は構文として正しく `1` を返し、結果 if 文は `true` と評価し、そして、しばらくバグと闘うことになるでしょう。

ヨーダ記法は最初、奇妙に見えるかもしれませんが、そのうち慣れるはずです。

なおヨーダ記法は「`==`」「`!=`」「`===`」「`!==`」で使用してください。「<」「>」「<=」「>=」では読みづらいため避けてください。

<!-- 
<h3>Clever Code</h3>
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
if ( 0 === strpos( 'WordPress', 'foo' ) ) {
	echo __( 'Yay WordPress!' );
}
```
<!-- 
Incorrect:
 -->
間違い:

```php
if ( 0 == strpos( 'WordPress', 'foo' ) ) {
	echo __( 'Yay WordPress!' );
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
    // Use $data
}
```

<!-- 
Incorrect:
 -->
間違い:

```php
if ( $data = $wpdb->get_var( '...' ) ) {
    // Use $data
}
```

<!-- 
In a <code>switch</code> statement, it's okay to have multiple empty cases fall through to a common block. If a case contains a block, then falls through to the next block, however, this must be explicitly commented.
 -->
`switch` 文では、共通コードに落ちる複数の空白 case があっても構いません。しかし、case にコードがあって次のコードに落ちる場合にはその旨をコメントを記述してください。

<!-- 
```php
switch ( $foo ) {
	case 'bar':	      // Correct, an empty case can fall through without comment.
	case 'baz':
		echo $foo;    // Incorrect, a case with a block must break, return, or have a comment.
	case 'cat':
		echo 'mouse';
		break;        // Correct, a case with a break does not require a comment.
	case 'dog':
		echo 'horse';
		// no break   // Correct, a case can have a comment to explicitly mention the fall through.
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
The <code>goto</code> statement must never be used.

The <code>eval()</code> construct is <em>very dangerous</em>, and is impossible to secure. Additionally, the <code>create_function()</code> function, which internally performs an <code>eval()</code>, is deprecated in PHP 7.2. Both of these must not be used.
 -->
`goto` 文は決して使わないでください。

`eval()` 言語構造は **非常に危険** で、安全性を保つことが不可能です。また `create_function()` 関数は内部的に `eval()` を実行し、PHP 7.2 では非推奨となりました。両方の関数を使わないでください。

<!-- 
<h3>Error Control Operator <code>@</code></h3>
 -->
### エラー制御演算子 @

<!-- 
As noted in the <a href="http://www.php.net//manual/en/language.operators.errorcontrol.php">PHP docs</a>:
<blockquote>PHP supports one error control operator: the at sign (@). When prepended to an expression in PHP, any error messages that might be generated by that expression will be ignored.</blockquote>
While this operator does exist in Core, it is often used lazily instead of doing proper error checking. Its use is highly discouraged, as even the PHP docs also state:
<blockquote>Warning: Currently the "@" error-control operator prefix will even disable error reporting for critical errors that will terminate script execution. Among other things, this means that if you use "@" to suppress errors from a certain function and either it isn't available or has been mistyped, the script will die right there with no indication as to why.</blockquote>
 -->
[PHP ドキュメント](http://www.php.net//manual/ja/language.operators.errorcontrol.php) によると

> PHP はエラー制御演算子(@)をサポートしています。PHP の式の前に付けた場合、その式により生成されたエラーメッセージは無視されます。

この演算子がコア内に存在すると、適切なエラーチェックが行われずしばしば遅れて適用されます。決して使用しないでください。ちなみに PHP のドキュメントにさえ次のような箇所があります。

> 警告: 現在、エラー制御演算子プレフィックス”@”は、スクリプトの実行を 終了するような致命的なエラーの出力さえ抑圧します。このため、ある関数の エラー出力を抑制するために “@” を使用した場合、その関数が 利用できなかったり、ミスタイプがあった場合でも、原因を示すことなく その場所でスクリプトは終了してしまいます。

<!-- 
<h3>Don't <code>extract()</code></h3>
 -->
### extract() は使わない

<!-- 
Per <a title="Remove all, or at least most, uses of extract() within WordPress" href="https://core.trac.wordpress.org/ticket/22400">#22400</a>:
<blockquote><code>extract()</code> is a terrible function that makes code harder to debug and harder to understand. We should discourage it's [sic] use and remove all of our uses of it.

Joseph Scott has <a class="ext-link" href="https://blog.josephscott.org/archives/2009/02/i-dont-like-phps-extract-function/">a good write-up of why it's bad</a>.</blockquote>
 -->
[#22400: Remove all, or at least most, uses of extract() within WordPress](https://core.trac.wordpress.org/ticket/22400) によれば、

> `extract()` はデバッグしにくいし、コードも読みにくい、ひどい関数。使うのは禁止、中で使ってるのも全部削除しよう。
> Joseph Scott が [何がそんなにひどいか書いてる](http://josephscott.org/archives/2009/02/i-dont-like-phps-extract-function/)。

<!-- 
<h2>Credits</h2>
 -->
## クレジット

<!-- 
<ul>
 	<li>PHP standards: <a href="http://pear.php.net/manual/en/standards.php" target="_blank">Pear standards</a></li>
</ul>
 -->
- PHP 規約: [Pear standards](http://pear.php.net/manual/en/standards.php)

<!-- 
<h3>Major Changes</h3>
 -->
### 主な変更

<!-- 
<ul>
 	<li>November 13, 2013: <a href="http://make.wordpress.org/core/2013/11/13/proposed-coding-standards-change-always-require-braces/">Braces should always be used, even when they are optional</a></li>
 	<li>June 20, 2014: Add <a href="#error-control-operator">section</a> to discourage use of the <a href="http://www.php.net//manual/en/language.operators.errorcontrol.php">error control operator</a> (<code>@</code>). See <a href="https://irclogs.wordpress.org/chanlog.php?channel=wordpress-dev&amp;day=2014-06-20&amp;sort=asc#m873356">#wordpress-dev</a>.</li>
 	<li>October 20, 2014: Update brace usage to indicate that the alternate syntax for control structures is allowed, even encouraged. It is single-line inline control structures that are forbidden.</li>
 	<li>January 21, 2014: Add section to forbid extract().</li>
</ul>
 -->
- 2013/11/13: [ブレースは常に使う。オプションの場合でも使う](https://make.wordpress.org/core/2013/11/13/proposed-coding-standards-change-always-require-braces/)。
- 2014/6/20: 「エラー制御演算子 @」の説明を追加。[エラー制御演算子 (@)](http://www.php.net//manual/en/language.operators.errorcontrol.php) の使用は禁止。参照 [#wordpress-dev](https://irclogs.wordpress.org/chanlog.php?channel=wordpress-dev&day=2014-06-20&sort=asc#m873356)。
- 2014/10/20: ブレースの更新 – 「制御構造に関する別の構文」の使用の許可、というか推奨。禁じられた「単一行のインライン制御構造」。
- 2014/1/21: extract() 禁止を追加

[原文](https://github.com/WordPress/wpcs-docs/blob/master/wordpress-coding-standards/php.md) / [日本語訳](https://github.com/jawordpressorg/wpcs-docs/blob/master/wordpress-coding-standards/php.md)

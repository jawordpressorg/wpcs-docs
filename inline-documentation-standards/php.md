<!-- 
# PHP Documentation Standards
 -->
# PHP ドキュメント規約

<!-- 
WordPress uses a customized documentation schema that draws inspiration from PHPDoc, an evolving standard for providing documentation to PHP code, which is maintained by [phpDocumentor](http://phpdoc.org/).
 -->
WordPress では PHPDoc をベースにしたカスタムのドキュメントスキーマを使用しています。PHPDoc は現在、[phpDocumentor](http://phpdoc.org/) によって管理されている、策定中の PHP プログラム用のドキュメント標準です。

<!-- 
In some special cases - such as WordPress' implementation of hash notations - standards are derived from the [draft PSR-5 recommendations](https://github.com/phpDocumentor/fig-standards/blob/master/proposed/phpdoc.md). This does not mean we are attempting to be "PSR-5 compliant" at this time, it simply means that we've adopted PSR-5 recommendations _in part_.
 -->
<!-- 
一部の規則、たとえば WordPress のハッシュ記法の実装などでは [ドラフト版 PSR-5 recommendations](https://github.com/phpDocumentor/fig-standards/blob/master/proposed/phpdoc.md) から規約を採用していますが、現時点で WordPress が 「PSR-5 互換」を目指しているわけではありません。単に「ある部分」で PSR-5 recommendations を採用したに過ぎません。
 -->
<!-- 
## What Should Be Documented
 -->
## 何をドキュメントすべきか

<!-- 
PHP documentation in WordPress mostly takes the form of either formatted blocks of documentation or inline comments.
 -->
WordPress における PHP ドキュメントの形態は、フォーマットされたドキュメントブロックか、インラインコメントになります。

<!-- 
The following is a list of what should be documented in WordPress files:
 -->
以下のリストは WordPress ファイルでドキュメントする項目の例です。

<!-- 
- Functions and class methods
- Classes
- Class members (including properties and constants)
- Requires and includes
- Hooks (actions and filters)
- Inline comments
- File headers
- Constants
 -->
- 関数、およびクラスのメソッド
- クラス
- クラスのメンバー (プロパティや定数を含む)
- require と include
- アクションフックとフィルターフック
- インラインコメント
- ファイルヘッダー
- 定数

<!-- 
### Documenting Tips
 -->
### ドキュメントのヒント 

<!-- 
#### Language
 -->
#### 文体

<!-- 
Summaries should be clear, simple, and brief. Avoid describing "why" an element exists, rather, focus on documenting "what" and "when" it does something.
 -->
「Summary」を書く場合には、明確でシンプルな、短い文を心がけてください。ドキュメントする要素が「なぜ」存在するのかではなく、「いつ」「何を」実行するのかを記述してください。

<!-- 
A function, hook, class, or method is a _third-person singular_ element, meaning that _third-person singular verbs_ should be used to describe what each does.
 -->
関数、フック、クラス、メソッドは「三人称単数」の要素です。説明を記述する場合も「三人称単数の動詞」を使用してください。

<!-- 
[tip]
Need help remembering how to conjugate for third-person singular verbs? Imagine prefixing the function, hook, class, or method summary with "It":

- _Good_: "(It) Does something."
- _Bad_: "(It) Do something."

[/tip]
-->
ヒント: 三人称単数の動詞の活用に悩む場合は、関数、フック、クラス、メソッドの Summary を書く際、先頭に「It」をつけて考えてください。
- 正: “(It) Does something.”
- 誤: “(It) Do something.”

<!-- 
Summary examples:
 -->
Summary の例:

<!-- 
- **Functions**: _What_ does the function do?
    - Good: _Displays the last modified date for a post._
    - Bad: _Display the date on which the post was last modified._
- **Filters**: _What_ is being filtered?
    - Good: _Filters the post content._
    - Bad: _Lets you edit the post content that is output in the post template._
- **Actions:** _When_ does an action fire?
    - Good: _Fires after most of core is loaded, and the user is authenticated.
    - Bad: _Allows you to register custom post types, custom taxonomies, and other general housekeeping tasks after a lot of WordPress core has loaded.
 -->
- **関数:** 「何を」するのか?
  - 正: Displays the last modified date for a post. (投稿の最終更新日を表示する)
  - 誤: Display the date on which the post was last modified. (投稿が最後に更新された日を表示)
- **フィルター:** 「何を」フィルターするのか?
  - 正: Filters the post content. (投稿の内容をフィルターする)
  - 誤: Lets you edit the post content that is output in the post template. (投稿の内容を編集し、投稿テンプレートの出力とします)
- **アクション:** 「いつ」呼ばれるのか?
  - 正: Fires after most of core is loaded, and the user is authenticated. (コアの大部分がロードされ、ユーザーの認証後に呼ばれる)
  - 誤: Allows you to register custom post types, custom taxonomies, and other general housekeeping tasks after a lot of WordPress core has loaded. (大部分の WordPress コアがロードされた後で、カスタム投稿タイプ、カスタムタクソノミー、その他の汎用の整理用タスクを登録できます)

<!-- 
#### Grammar
 -->
#### 文法

<!-- 
Descriptive elements should be written as complete sentences. The one exception to this standard is file header summaries, which are intended as file "titles" more than sentences.
 -->
説明文の要素は完全な文として記述してください。例外はファイルヘッダーの Summary です。この Summary は文章ではなく「タイトル」を意図しているためです。

<!-- 
The serial (Oxford) comma should be used when listing elements in summaries, descriptions, and parameter or return descriptions.
 -->
概要、説明、パラメータや戻り値の説明内で複数の要素を書く際には serial comma (Oxford comma) を使用してください。(例: A, B and C)

<!-- 
#### Miscellaneous
 -->
#### その他

<!-- 
**`@since`**: The recommended tool to use when searching for the version something was added to WordPress is [`svn blame`](http://make.wordpress.org/core/handbook/svn/code-history/#using-subversion-annotate). An additional resource for older hooks is the [WordPress Hooks Database](http://adambrown.info/p/wp_hooks).
 -->
**@since**: WordPress に追加されたバージョン番号等を調べるには「[svn blame](http://make.wordpress.org/core/handbook/svn/code-history/#using-subversion-annotate)」の使用を推奨します。補完するツールとして古いフックの場合には「[WordPress Hooks Database](http://adambrown.info/p/wp_hooks)」も使用してください。

<!-- 
If the version number cannot be determined after using these tools, use `@since Unknown`.
 -->
バージョン番号を特定できない場合は、「`@since Unknown`」を使用してください。

<!-- 
Anything ported over from WPMU should use `@since MU (3.0.0)`. Existing `@since MU (3.0.0)` tags should not be changed.
 -->
WPMU からの移植は「`@since MU (3.0.0)`」を使用してください。既存の「`@since MU (3.0.0)`」タグは変更しないでください。

<!-- 
**Code Refactoring**: It is permissible to space out the specific action or filter lines being documented to meet the coding standards, but do not refactor other code in the file.
 -->
**コードのリファクタリング**: コーディング規約に合わせるため特定のアクションやフックの行にスペースを挿入、削除しても構いませんが、ファイルの他の部分はリファクタリングしないでください。

<!-- 
### Formatting Guidelines
 -->
### フォーマットガイドライン

<!-- 
[info]
WordPress' inline documentation standards for PHP are specifically tailored for optimum output on the [official Code Reference](https://developer.wordpress.org/reference/). As such, following the standards in core and formatting as described below are _extremely_ important to ensure expected output.
[/info]
 -->
**重要**: WordPress の「PHP インラインドキュメント規約」は最適な「[公式コードリファレンス](https://developer.wordpress.org/reference/)」が出力されるよう調整されています。そのため、コア内で規約に準拠し、以下の説明どおりにドキュメントをフォーマットすることは正しい出力のために**極めて**重要です。

<!-- 
#### General
 -->
#### 全般

<!--
DocBlocks should directly precede the hook, action, function, method, or class line. There should not be any opening/closing tags or other things between the DocBlock and the declarations to prevent the parser becoming confused.
 -->
DocBlock はフック、アクション、関数、メソッド、クラスの行の直前に記述してください。DocBlock とこれらの定義との間には開始タグ、終了タグを含め何も書かないでください。パーサーが混乱します。

#### Summary

<!--
No HTML markup or Markdown of any kind should be used in the summary. If the text refers to an HTML element or tag, then it should be written as "image tag" or "img" element, not "`<img>`". For example:

- Good: _Fires when printing the link tag in the header._
- Bad: _Fires when printing the `<link>` tag in the header._

Inline PHPDoc tags may be used.
-->
Summary では HTML、Markdown、その他のマークアップを使用しないでください。HTML 要素やタグに触れる場合は、「image tag」または「img element」と記述してください。「<img>」は使わないでください。

- 正: Fires when printing the link tag in the header.
- 誤: Fires when printing the <link> tag in the header.

インライン PHPDoc タグは使用できます。

#### Description

<!--
HTML markup should never be used outside of code examples, though Markdown can be used, as needed, in the description.
-->
コードの例以外では HTML マークアップを使用しないでください。Markdown は必要に応じて使用できます。

<!--
1. Lists:
-->
1. リスト

<!--
    Use a hyphen (-) to create an unordered list, with a blank line before and after.
-->
    順序のないリストの場合はハイフン「-」を使用してください。リストの前後には空白行を置いてください。

    ```php
     * Description which includes an unordered list:
     *
     * - This is item 1.
     * - This is item 2.
     * - This is item 3.
     *
     * The description continues on ...
    ```
<!-- 
    Use numbers to create an ordered list, with a blank line before and after.
 -->
    順序付きのリストの場合は数字を使用してください。リストの前後には空白行を置いてください。

    ```php
     * Description which includes an ordered list:
     *
     * 1. This is item 1.
     * 2. This is item 2.
     * 3. This is item 3.
     *
     * The description continues on ...
    ```

<!--
2. Code samples would be created by indenting every line of the code by 4 spaces, with a blank line before and after. Blank lines in code samples also need to be indented by four spaces. Note that examples added in this way will be output in `<pre>` tags and _not_ syntax-highlighted.
-->
2. コードの例では、すべての行を4個のスペースでインデントし、コード全体の前後には空白行を置いてください。コードの途中の空白行も、4個のスペースでインデントしてください。なおこの方法で追加された例は `<pre>` タグで出力され、シンタックスハイライトは**適用されません**。

    ```php
     * Description including a code sample:
     *
     *    $status = array(
     *        'draft'   => __( 'Draft' ),
     *        'pending' => __( 'Pending Review' ),
     *        'private' => __( 'Private' ),
     *        'publish' => __( 'Published' )
     *    );
     *
     * The description continues on ...
    ```

<!--
3. Links in the form of URLs, such as related Trac tickets or other documentation, should be added in the appropriate place in the DocBlock using the `@link` tag:
-->
3. 関連する Trac チケットや他のドキュメントへの URL 形式のリンクは DocBlock 内の適切な場所に `@link` タグを使用して追加してください。

    ```php
     * Description text.
     *
     * @link https://core.trac.wordpress.org/ticket/20000
    ```

<!--
#### `@since` Section (Changelogs)

Every function, hook, class, and method should have a corresponding `@since` version associated with it (more on that below).
-->
#### @since セクション (変更履歴)

すべての関数、フック、クラス、メソッドには関連する `@since` バージョンを記述してください。詳細は後述します。

<!--
No HTML should be used in the descriptions for `@since` tags, though limited Markdown can be used as necessary, such as for adding backticks around variables, arguments, or parameter names, e.g. `$variable`.
-->
`@since` タグの説明で HTML は使えません。いくつかの Markdown は必要に応じて使用できます。たとえば変数名、引数名、パラメータ名をバッククォートで囲むことができます。例: `$variable`

<!--
Versions should be expressed in the 3-digit `x.x.x` style:
-->
バージョンは 3組の数字「x.x.x」 で記述してください。

```php
 * @since 4.4.0
```

<!--
If significant changes have been made to a function, hook, class, or method, additional `@since` tags, versions, and descriptions should be added to provide a changelog for that function.
-->
関数、フック、クラス、メソッドに重大な変更がある場合には、機能の変更履歴を残す意味で追加の `@since` タグ、バージョン、説明を加えてください。

<!--
"Significant changes" include but are not limited to:

- Adding new arguments or parameters.
- Required arguments becoming optional.
- Changing default/expected behaviors.
- Functions or methods becoming wrappers for new APIs.
- Parameters which have been renamed (once PHP 8.0 support has been announced).

PHPDoc supports multiple `@since` versions in DocBlocks for this explicit reason. When adding changelog entries to the `@since` block, a version should be cited, and a description should be added in sentence case and form and end with a period:
-->
たとえば「重大な変更」には以下のような項目が含まれますが、これに限りません。

- 新しい引数やパラメータの追加
- 必須の引数がオプションになった
- デフォルトや期待する振る舞いの変更
- 関数やメソッドが新しい API のラッパーになった
- 名前が変更されたパラメータ (いったん PHP 8.0 のサポートが発表された)

以上の説明で明らかですが PHPDoc は DocBlock 内に複数の `@since` バージョンをサポートします。`@since` ブロックに変更履歴の行を追加する場合は、バージョンに続けて、大文字で始め、ピリオドで終わる完全な文として説明を追加してください。

```php
 * @since 3.0.0
 * @since 3.8.0 Added the `post__in` argument.
 * @since 4.1.0 The `$force` parameter is now optional.
```

<!--
#### Other Descriptions

`@param`, `@type`, `@return`: No HTML should be used in the descriptions for these tags, though limited Markdown can be used as necessary, such as for adding backticks around variables, e.g. `$variable`.

- Inline `@see` tags can also be used to auto-link hooks in core:
    - Hooks, e.g. `{@see 'save_post'}`
    - Dynamic hooks, e.g. `{@see '$old_status_to_$new_status'}` (Note that any extra curly braces have been removed inside the quotes)
- Default or available values should use single quotes, e.g. 'draft'. Translatable strings should be identified as such in the description.
- HTML elements and tags should be written as "audio element" or "link tag".
 -->
#### その他の説明

`@param`、`@type`、`@return`: タグの説明で HTML は使えません。いくつかの Markdown は必要に応じて使用できます。たとえばバッククォートで変数名を囲むことができます。例: `$variable`

- インライン `@see` タグも、コア内でフックに自動的にリンクする目的で使用できます。
  - フック。例: `{@see 'save_post'}`
  - 動的なフック。例: `{@see '$old_status_to_$new_status'}` (注意: シングルクォート内の余分なブレースは除去されています)
- デフォルト値や指定可能な値にはシングルクォートを使用してください。例:「’draft’」。翻訳対象の文字列は説明内で明示してください。
- HTML 要素やタグは「audio element」や「link tag」のように記述してください。

<!-- 
#### Line wrapping

DocBlock text should wrap to the next line after 80 characters of text. If the DocBlock itself is indented on the left 20 character positions, the wrap could occur at position 100, but should not extend beyond a total of 120 characters wide.
 -->
#### 行の折り返し

DocBlock のテキストは80文字分で次の行に折り返してください。例えば DocBlock が20文字分インデントしている場合には、100文字目の位置で折り返します。120文字目以上は超えないでください。

<!-- 
## DocBlock Formatting

The examples provided in each section below show the expected DocBlock content and tags, as well as the exact formatting. Use spaces inside the DocBlock, not tabs, and ensure that items in each tag group are aligned according to the examples.
 -->
## DocBlock フォーマット

以下の各セクションの例では、期待する DocBlock の内容とタグを正しいフォーマットで記述しています。DocBlock の中ではタブでなく、スペースを使用してください。各タググループの内容は例と同様に並べてください。

<!--
### 1. Functions &amp; Class Methods

Functions and class methods should be formatted as follows:

- **Summary**: A brief, one sentence explanation of the purpose of the function spanning a maximum of two lines. Use a period at the end.
- **Description**: A supplement to the summary, providing a more detailed description. Use a period at the end of sentences.
- **`@ignore`**: Used when an element is meant only for internal use and should be skipped from parsing.
- **`@since x.x.x`**: Should always be 3-digit (e.g. `@since 3.9.0`). Exception is `@since MU (3.0.0)`.
- **`@access`**: Only used for core-only functions or classes implementing "private" core APIs. If the element is private it will be output with a message stating its intention for internal use.
- **`@see`**: Reference to a function, method, or class that is heavily-relied on within. See the note above about inline `@see` tags for expected formatting.
- **`@link`**: URL that provides more information. This should never been used to reference another function, hook, class, or method, see `@see`.
- **`@global`**: List PHP globals that are used within the function or method, with an optional description of the global. If multiple globals are listed, they should be aligned by type, variable, and description, with each other as a group.
- **`@param`**: Note if the parameter is _Optional_ before the description, and include a period at the end. The description should mention accepted values as well as the default. For example: _Optional. This value does something. Accepts 'post', 'term', or empty. Default empty._
- **`@return`**: Should contain all possible return types, and a description for each. Use a period at the end. Note: `@return void` should not be used outside of the default bundled themes.
-->
### 1. 関数およびクラスのメソッド #1. 関数およびクラスのメソッド

関数およびクラスのメソッドは次のようにフォーマットしてください。

- **Summary(概要)**: 関数の目的を説明する簡潔な単一の文。最大でも2行。最後はピリオド。
- **Description(説明)**: Summary を補足する詳細な説明。文の最後はピリオド。
- **@ignore**: 要素は内部でのみ使用され、パースの対象外とする場合に使用。
- **@since x.x.x**: 常に3組の数字(例 @since 3.9.0)。例外は @since MU (3.0.0)。
- **@access**: コアのみの関数、または、private なコア API を実装するクラスでのみ使用される。要素が private の場合、内部使用を意図する旨のメッセージと共に出力される。
- **@see**: 強く依存する関数、メソッド、クラスへの参照。インライン `@see` タグの期待するフォーマットについては上の注意を参照。
- **@link**: 追加の情報用の URL。別の関数、フック、クラス、メソッドへの参照の場合には使わないでください。`@see` 参照。
- **@global**: 関数またはメソッド内で使用される PHP グローバル変数のリスト。オプションでグローバル変数の説明も記述できます。複数のグローバル変数がある場合、型、変数、説明ごとに並べてグループ分けしてください。
- **@param**: パラメータがオプションであれば説明の前に「Optional」と付けてください。最後はピリオドです。説明には指定可能な値の範囲、デフォルト値も含めてください。例: Optional. This value does something. Accepts ‘post’, ‘term’, or empty. Default empty.
- **@return**: すべての戻り値の型とその説明を記述してください。最後はピリオです。注意: WordPress 本体に同梱されるテーマ以外では、`@return` void は使用しないでください。

```php
/**
 * Summary.
 *
 * Description.
 *
 * @since x.x.x
 *
 * @see Function/method/class relied on
 * @link URL
 * @global type $varname Description.
 * @global type $varname Description.
 *
 * @param type $var Description.
 * @param type $var Optional. Description. Default.
 * @return type Description.
 */
```

<!--
#### 1.1 Parameters That Are Arrays

Parameters that are an array of arguments should be documented in the "originating" function only, and cross-referenced via an `@see` tag in corresponding DocBlocks.

Array values should be documented using WordPress' flavor of hash notation style similar to how [Hooks](http://make.wordpress.org/core/handbook/inline-documentation-standards/php-documentation-standards/#4-hooks-actions-and-filters) can be documented, each array value beginning with the `@type` tag, and taking the form of:
-->
#### 1.1 配列パラメータ

引数の配列をパラメータに取る場合には、最初の送信を行う関数でのみドキュメントし、関連する DocBlock 内では `@see` タグを使用して相互参照してください。

配列値のドキュメントでは、[フック](http://make.wordpress.org/core/handbook/inline-documentation-standards/php-documentation-standards/#4-hooks-actions-and-filters)のドキュメントと同じ WordPress 流のハッシュ記法スタイルを使用してください。各配列の値は `@type` タグで始め、次の形式をとります。

<!-- 
```php
*     @type type $key Description. Default 'value'. Accepts 'value', 'value'.
*                     (aligned with Description, if wraps to a new line)
```
 -->
```php
*     @type type $key Description. Default 'value'. Accepts 'value', 'value'.
*                     (複数行の場合は、Description で並べる)
```

<!--
An example of an "originating" function and re-use of an argument array is [`wp_remote_request|post|get|head()`](https://core.trac.wordpress.org/browser/tags/6.0/src/wp-includes/http.php/#L114).
-->
最初の送信を行う関数と、配列引数の再利用については [wp_remote_request|post|get|head()](https://core.trac.wordpress.org/browser/branches/4.0/src/wp-includes/http.php#L115) を参照してください。

<!-- 
```php
/**
 * Summary.
 *
 * Description.
 *
 * @since x.x.x
 *
 * @param type  $var Description.
 * @param array $args {
 *     Optional. An array of arguments.
 *
 *     @type type $key Description. Default 'value'. Accepts 'value', 'value'.
 *                     (aligned with Description, if wraps to a new line)
 *     @type type $key Description.
 * }
 * @param type  $var Description.
 * @return type Description.
 */
```
 -->
```php
/**
 * Summary.
 *
 * Description.
 *
 * @since x.x.x 
 *
 * @param type  $var Description.
 * @param array $args {
 *     Optional. An array of arguments.
 *
 *     @type type $key Description. Default 'value'. Accepts 'value', 'value'.
 *                     (複数行の場合は、Description で並べる)
 *     @type type $key Description.
 * }
 * @param type  $var Description.
 * @return type Description.
 */
```

<!--
In most cases, there is no need to mark individual arguments in a hash notation as _optional_, as the entire array is usually optional. Specifying "Optional." in the hash notation description should suffice. In the case where the array is NOT optional, individual key/value pairs may be optional and should be marked as such as necessary.

#### 1.2 Deprecated Functions

If the function is deprecated and should not be used any longer, the `@deprecated` tag, along with the version and description of what to use instead, should be added. Note the additional use of an `@see` tag - the Code Reference uses this information to attempt to link to the replacement function.
-->
ほとんどの場合、ハッシュ記法内の個々の引数に「optional」を付ける必要はありません。これは配列全体がオプションの場合が多いためです。配列がオプションでなく必須の場合で、個々の key と value のペアがオプションの場合には、必要に応じて「Optional.」を記述してください。

#### 1.2 非推奨の関数

関数が非推奨となり、今後使用されない場合には、`@deprecated` タグを使用し、バージョンと代替の関数を記述してください。注意: これは `@see` タグの別の用法です。コードリファレンスではこの情報を使用して代替の関数へのリンクを作成します。

```php
/**
 * Summary.
 *
 * Description.
 *
 * @since x.x.x
 * @deprecated x.x.x Use new_function_name()
 * @see new_function_name()
 *
 * @param type $var Optional. Description.
 * @param type $var Description.
 * @return type Description.
 */
```

<!--
### 2. Classes

Class DocBlocks should be formatted as follows:

- **Summary**: A brief, one sentence explanation of the **purpose** of the class spanning a maximum of two lines. Use a period at the end.
- **Description**: A supplement to the summary, providing a more detailed description. Use a period at the end.
- **`@since x.x.x`**: Should always be 3-digit (e.g. `@since 3.9.0`). Exception is `@since MU (3.0.0)`.
-->
<h3>2. クラス</h3>

クラスの DocBlock は次のようにフォーマットしてください。

- **Summary(概要)**: クラスの**目的**を説明する簡潔な単一の文。最大でも2行。最後はピリオド。
- **Description(説明)**: Summary を補足する詳細な説明。最後はピリオド。
- **@since x.x.x**: 常に3組の数字(例 `@since 3.9.0`)。例外は `@since MU (3.0.0)`。

```php
/**
 * Summary.
 *
 * Description.
 *
 * @since x.x.x
 */
```

<!--
If documenting a sub-class, it's also helpful to include an `@see` tag reference to the super class:
-->
子クラスのドキュメントでは、`@see` タグを使用して親クラスへの参照を含めてください。

```php
/**
 * Summary.
 *
 * Description.
 *
 * @since x.x.x
 *
 * @see Super_Class
 */
```

<!--
#### 2.1 Class Members

##### 2.1.1 Properties

Class properties should be formatted as follows:

- **Summary**: Use a period at the end.
- **`@since x.x.x`**: Should always be 3-digit (e.g. `@since 3.9.0`). Exception is `@since MU (3.0.0)`.
- **`@var`**: Formatted the same way as `@param`, though the description may be omitted.
-->
#### 2.1 クラスのメンバー

##### 2.1.1 プロパティ

クラスのプロパティは次のようにフォーマットしてください。

- **Summary(概要)**: 最後はピリオド。
- **@since x.x.x**: 常に3組の数字(例 `@since 3.9.0`)。例外は `@since MU (3.0.0)`。
- **@var**: `@param` と同様の形式。ただし説明は省略可能

```php
/**
 * Summary.
 *
 * @since x.x.x
 * @var type $var Description.
 */
```

<!--
##### 2.1.2 Constants

- **Summary**: Use a period at the end.</li>
- **`@since x.x.x`**: Should always be 3-digit (e.g. `@since 3.9.0`). Exception is `@since MU (3.0.0)`.
- **`@var`**: Formatted the same way as `@param`, though the description may be omitted.
-->
##### 2.1.2 定数

- **Summary(概要)**: 最後はピリオド。
- **@since x.x.x**: 常に3組の数字(例 `@since 3.9.0`)。例外は `@since MU (3.0.0)`。
- **@var**: `@param` と同様の形式。ただし説明は省略可能

```php
/**
 * Summary.
 *
 * @since x.x.x
 * @var type $var Description.
 */
const NAME = value;
```

<!--
### 3. Requires and Includes

Files required or included should be documented with a summary description DocBlock. Optionally, this may apply to inline `get_template_part()` calls as needed for clarity.
-->
### 3. require と include 

require または include するファイルは、概要説明の DocBlock でドキュメントしてください。オプションで必要に応じて、インライン `get_template_part()` から呼び出すファイルもドキュメントしてください。

```php
/**
 * Summary.
 */
require_once( ABSPATH . WPINC . '/filename.php' );
```

<!--
### 4. Hooks (Actions and Filters)

Both action and filter hooks should be documented on the line immediately preceding the call to `do_action()` or `do_action_ref_array()`, or `apply_filters()` or `apply_filters_ref_array()`, and formatted as follows:

- **Summary**: A brief, one line explanation of the purpose of the hook. Use a period at the end.
- **Description**: A supplemental description to the summary, if warranted.
- **`@ignore`**: Used when a hook is meant only for internal use and should be skipped from parsing.
- **`@since x.x.x`**: Should always be 3-digit (e.g. `@since 3.9.0`). Exception is `@since MU (3.0.0)`.
- **`@param`**: If the parameter is an array of arguments, document each argument using a hash notation (described above in the _Parameters That Are Arrays_ section), and include a period at the end of each line.

Note that `@return` is _not_ used for hook documentation, because action hooks return nothing, and filter hooks always return their first parameter.
-->
### 4. フック (アクションとフィルター)

アクションフックもフィルターフックも、`do_action()` や `do_action_ref_array()`、または `apply_filters()` や `apply_filters_ref_array()` 呼び出し行の直前でドキュメントしてください。次のようにフォーマットしてください。

- **Summary(概要)**: フックの目的を説明する簡潔な単一の文。最後はピリオド。
- **Description(説明)**: 必要な場合は Summary を補足する詳細な説明。
- **@ignore**: フックは内部でのみ使用され、パースの対象外とする場合に使用。
- **@since x.x.x**: 常に3組の数字(例 `@since 3.9.0`)。例外は `@since MU (3.0.0)`。
- **@param:** パラメータが引数の配列であれば、ハッシュ記法を使用して各引数をドキュメント。詳細は「1.1 配列パラメータ」参照。各行の最後はピリオド。

注意: フックのドキュメントに `@return` は**使用しません**。アクションフックは何も返さず、フィルターフックは常に第1パラメータを返すためです。

```php
/**
 * Summary.
 *
 * Description.
 *
 * @since x.x.x
 *
 * @param type  $var Description.
 * @param array $args {
 *     Short description about this hash.
 *
 *     @type type $var Description.
 *     @type type $var Description.
 * }
 * @param type  $var Description.
 */
```

<!--
If a hook is in the middle of a block of HTML or a long conditional, the DocBlock should be placed on the line immediately before the start of the HTML block or conditional, even if it means forcing line-breaks/PHP tags in a continuous line of HTML.
-->
フックが HTML ブロックや長い条件の途中にある場合、DocBlock は HTML ブロックや条件の開始行の直前に置いてください。この結果、連続した HTML 行の途中に改行や PHP タグを含める形になっても構いません。

<!--
Tools to use when searching for the version a hook was added are [`svn blame`](http://make.wordpress.org/core/handbook/svn/code-history/#using-subversion-annotate), or the [WordPress Hooks Database](http://adambrown.info/p/wp_hooks) for older hooks. If, after using these tools, the version number cannot be determined, use `@since Unknown`.

#### 4.1 Duplicate Hooks

Occasionally, hooks will be used multiple times in the same or separate core files. In these cases, rather than list the entire DocBlock every time, only the first-added or most logically-placed version of an action or filter will be fully documented. Subsequent versions should have a single-line comment.
-->
フックが追加されたバージョンを調べるには「[svn blame](http://make.wordpress.org/core/handbook/svn/code-history/#using-subversion-annotate)」、または古いフックの場合には「[WordPress Hooks Database](http://adambrown.info/p/wp_hooks)」を使用してください。ツールを使用してもバージョン番号を特定できない場合は、`@since Unknown` を使用してください。

#### 4.1 重複したフック

フックは同じコアファイル内、異なるコアファイルで複数回使用される場合があります。このような場合は毎回、完全な DocBlock 全体を書かずに、アクションフックやフィルターフックが最初に登場した場所、あるいはもっとも論理的な場所で完全にドキュメントし、残りの場所には単一行コメントを加えてください。

<!--
For actions:
-->
アクションの場合

```php
/** This action is documented in path/to/filename.php */
```

<!--
For filters:
-->
フィルターの場合

```php
/** This filter is documented in path/to/filename.php */
```

<!--
To determine which instance should be documented, search for multiples of the same hook tag, then use [`svn blame`](http://make.wordpress.org/core/handbook/svn/code-history/#using-subversion-annotate) to find the first use of the hook in terms of the earliest revision. If multiple instances of the hook were added in the same release, document the one most logically-placed as the "primary".

### 5. Inline Comments

Inline comments inside methods and functions should be formatted as follows:

#### 5.1 Single line comments
-->
どのインスタンスをドキュメントすべきかを決めるには、すべてのフックタグの登場を [svn blame](http://make.wordpress.org/core/handbook/svn/code-history/#using-subversion-annotate) で検索し、最初に使用されるリビジョンを見つけてください。複数のインスタンスが同時に同じリリースで登場した場合はもっとも論理的な場所を「代表」としてドキュメントしてください。

### 5. インラインコメント

メソッドや関数のインラインコメントは次のようにフォーマットしてください。

#### 5.1 単一行コメント

```php
// Allow plugins to filter an array.
```

<!--
#### 5.2 Multi-line comments
-->
#### 5.2 複数行コメント

```php
/*
 * This is a comment that is long enough to warrant being stretched over
 * the span of multiple lines. You'll notice this follows basically
 * the same format as the PHPDoc wrapping and comment block style.
 */
```

<!--
**Important note**: Multi-line comments must not begin with `/**` (double asterisk) as the parser might mistake it for a DocBlock. Use `/*` (single asterisk) instead.

### 6. File Headers

The file header DocBlock is used to give an overview of what is contained in the file.
-->
**重要な注意**: 複数行コメントを「`/**`」(2つのアスタリスク) で始めないでください。パーサーが DocBlock と間違えます。代わりに「`/*`」(1つのアスタリスク) で始めてください。

### 6. ファイルヘッダー

ファイルヘッダー DocBlock にはファイルに含まれる内容の概要を書きます。

<!--
Whenever possible, **all** WordPress files should contain a header DocBlock, regardless of the file's contents - this includes files containing classes.
-->
可能であれば常に**すべて**の WordPress ファイルにヘッダー DocBlock を記述してください。ファイルの内容に関わらず、またクラスを定義するファイルも含めすべてのファイルが対象です。

```php
/**
 * Summary (no period for file headers)
 *
 * Description. (use period)
 *
 * @link URL
 *
 * @package WordPress
 * @subpackage Component
 * @since x.x.x (when the file was introduced)
 */
```

<!--
The _Summary_ section is meant to serve as a succinct description of **what** specific purpose the file serves.
-->
*Summary* セクションではファイルが具体的に「**何を**」提供するのかを簡潔に説明してください。

<!--
- Good: _"Widgets API: WP_Widget class"_
- Bad: _"Core widgets class"_

The _Description_ section can be used to better explain overview information for the file such as how the particular file fits into the overall makeup of an API or component.
-->
例:

- 正: “Widgets API: WP_Widget class”
- 誤: “Core widgets class”

*Description* セクションではファイルの概要をより詳細に説明します。たとえば API やコンポーネント全体におけるファイルの位置づけなどです。


<!--
Examples:

- Good: _"The Widgets API is comprised of the WP_Widget and WP_Widget_Factory classes in addition to a variety of top-level functionality that implements the Widgets and related sidebar APIs. WordPress registers a number of common widgets by default."_

### 7. Constants

The constant DocBlock is used to give a description of the constant for better use and understanding.
-->
例:

- 正: “The Widgets API is comprised of the WP_Widget and WP_Widget_Factory classes in addition to a variety of top-level functionality that implements the Widgets and related sidebar APIs. WordPress registers a number of common widgets by default.”

### 7. 定数

定数の DocBlock では、定数の理解と利用のための説明を加えます。

<!--
Constants should be formatted as follows:

- **Summary**: Use a period at the end.
- **`@since x.x.x`**: Should always be 3-digit (e.g. `@since 3.9.0`). Exception is `@since MU (3.0.0)`.
- **`@var`**: Formatted the same way as `@param`. The description is optional.
-->
定数は次のようにフォーマットしてください。

- **Summary(概要)**: 最後はピリオド。
- **@since x.x.x**: 常に3組の数字(例 `@since 3.9.0`)。例外は `@since MU (3.0.0)`。
- **@var**: `@param` と同様の形式。ただし説明は省略可能

<!-- 
```php
/**
 * Summary.
 *
 * @since x.x.x (if available)
 * @var type $var Description.
 */
```
 -->
```php
/**
 * Summary.
 *
 * @since x.x.x (可能であれば)
 * @var type $var Description.
 */
```

<!--
## PHPDoc Tags

Common PHPDoc tags used in WordPress include `@since`, `@see`, `@global` `@param`, and `@return` (see table below for full list).

For the most part, tags are used correctly, but not all the time. For instance, sometimes you'll see an `@link` tag inline, linking to a separate function or method. "Linking" to known classes, methods, or functions is not necessary, as the Code Reference automatically links these elements. For "linking" hooks inline, the proper tag to use is `@see` - see the _Other Descriptions_ section.
-->
## PHPDoc タグ

WordPress で使用される主な PHPDoc タグには `@since`、`@see`、`@global`、`@param`、`@return` があります。完全なリストについては以下の表を参照してください。

ほとんどの場面でタグは正しく使用されていますが、まだ誤用されている場合もあります。例えばインラインの `@link` タグは、別の関数やメソッドへのリンクで使用される場合がありますが、実際には既知のクラス、メソッド、関数へのリンクはコードリファレンスが自動で作成するため不要です。インラインでフックをリンクする際の正しいタグは `@see` です。上の「その他の説明」節も参照してください。

<!--
| Tag               | Usage                                                       | Description                                                                                                                                                                                                                                    |
|-------------------|-------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **`@access`**     | private                                                     | Only used in limited circumstances, like when visibility modifiers cannot be used in the code, and only when private, such as for core-only functions or core classes implementing "private" APIs. Used directly below the `@since` line in block.                                                        |
| **`@deprecated`** | version x.x.x Use _replacement function name_ instead       | What version of WordPress the function/method was deprecated. Use 3-digit version number. Should be accompanied by a matching `@see` tag.                                                                                                      |
| **`@global`**     | datatype $variable description                              | Document global(s) used in the function/method. For boolean and integer types, use `bool` and `int`, respectively.                                                                                                                             |
| **`@internal`**   | information string                                          | Typically used wrapped in `{}` for adding notes for internal use only.                                                                                                                                                                                         |
| **`@ignore`**     | (standalone)                                                | Used to skip parsing of the entire element.                                                                                                                                                                                                    |
| **`@link`**       | URL                                                         | Link to additional information for the function/method. For an external script/library, links to source. Not to be used for related functions/methods; use `@see` instead.                                                                     |
| **`@method`**     | returntype description                                      | Shows a "magic" method found inside the class.                                                                                                                                                                                                 |
| **`@package`**    | packagename                                                 | Specifies package that all functions, includes, and defines in the file belong to. Found in DocBlock at top of the file. For core (and bundled themes), this is always **WordPress**.                                                          |
| **`@param`**      | datatype $variable description                              | Function/method parameter of the format: parameter type, variable name, description, default behavior. For boolean and integer types, use `bool` and `int`, respectively.                                                                      |
| **`@return`**     | datatype description                                        | Document the return value of functions or methods. `@return void` should not be used outside of the default bundled themes. For boolean and integer types, use `bool` and `int`, respectively.                                                 |
| **`@see`**        | elementname                                                 | References another function/method/class the function/method relies on. Should only be used inline for "linking" hooks.                                                                                                                        |
| **`@since`**      | version x.x.x                                               | Documents release version function/method was added. Use 3-digit version number - this is to aid with version searches, and for use when comparing versions in code. Exception is `@since MU (3.0.0)`.                                         |
| **`@static`**     | (standalone)                                                | Note: This tag has been used in the past, but should no longer be used. Just using the static keyword in your code is enough for phpDocumentor on PHP5+ to recognize static variables and methods, and PhpDocumentor will mark them as static. |
| **`@staticvar`**  | datatype $variable description                              | Note: This tag has been used in the past, but should no longer be used. Document a static variable's use in a function/method. For boolean and integer types, use `bool` and `int`, respectively.                                              |
| **`@subpackage`** | subpackagename                                              | For page-level DocBlock, specifies the Component that all functions and defines in file belong to. For class-level DocBlock, specifies the subpackage/component the class belongs to.                                                          |
| **`@todo`**       | information string                                          | Documents planned changes to an element that have not been implemented.                                                                                                                                                                        |
| **`@type`**       | datatype description for an argument array value            | Used to denote argument array value types. See the **Hooks** or **Parameters That Are Arrays** sections for example syntax.                                                                                                                    |
| **`@uses`**       | class::methodname() / class::$variablename / functionname() | Note: This tag has been used in the past, but should no longer be used. References a key function/method used. May include a short description.                                                                                                |
| **`@var`**        | datatype description                                        | Data type for a class variable and short description. Callbacks are marked callback.                                                                                           
-->

|タグ |用法 |説明 |
|----|-----|-----|
|**@access** |private |コード内でアクセス修飾子が使えないなど、限られた条件下で、private に対してのみ使用される。たとえば “private” API を実装するコア専用関数やコアクラス。ブロックでは **@since** 直下で使用される。|
|**@deprecated** |version x.x.x 代替の関数名 |関数やメソッドがどの WordPress バージョンで非推奨になったかを示す。3組の数字を使用。該当する **@see** タグを付ける。|
|**@global** |型 global $変数名 説明 |関数やメソッドで使用されるグローバル変数をドキュメントする。boolean または integer 型の場合、それぞれ `bool` と `int` を使用する。|
|**@internal** |説明文 |典型的な用法として `{}` で囲まれ、内部利用のみであることを明記する。|
|**@ignore** |(単体) |要素全体のパースをスキップする。|
|**@link** |URL |関数やメソッドの追加情報へのリンク。 外部のスクリプトやライブラリーにリンクする場合は、ソースにリンクする。 関連する関数やメソッドには使用せず、代わりに **@see** を使用する。|
|**@method** |戻り値の型 説明 |クラス内にある「マジック」メソッドを記述する。|
|**@package** |パッケージ名 |すべての関数、インクルード、ファイル内の定義が属するパッケージを指定する。ファイル先頭の DocBlock に位置する。コアおよび同梱されるテーマでは常に「**WordPress**」。|
|**@param** |データ型 $variable 説明 |関数やメソッドのパラメータ。フォーマット: パラメータの型 変数名 説明 デフォルトの動き。boolean および integer 型の場合、それぞれ `bool` と `int` を使用。|
|**@return** |データ型 説明 |関数やメソッドの戻り値をドキュメントする。WordPress 本体に同梱されるテーマ以外では、`@return void` は使用しない。boolean および integer 型の場合、それぞれ `bool` と `int` を使用。|
|**@see** |要素名 |関数やメソッドが依存する別の関数、メソッド、クラスへの参照。フックとのリンクでのみインラインでの使用可。|
|**@since** |version x.x.x |関数やメソッドが追加されたリリースバージョンをドキュメントする。バージョンでの検索の容易性、およびコードでのバージョン比較のため、3組の数字のバージョン番号を使用する。例外は `@since MU (3.0.0)`。|
|**@static** |(単体) |注意: 過去にはこのタグが使われていたが現在では使用しない。コード内で static キーワードを使えば、PHP5 の PhpDocumentor は static 変数、static メソッドを識別し、static としてマークする。|
|**@staticvar** | データ型 $変数名 説明 |注意: 過去にはこのタグが使われていたが現在では使用しない。関数やメソッド内での static 変数の使用をドキュメントする。boolean および integer 型の場合、それぞれ `bool` と `int` を使用。|
|**@subpackage** |サブパッケージ名 |ページレベルの DocBlock の場合、ファイル内のすべての関数や定義が属するコンポーネントを指定する。クラスレベルの DocBlock の場合、クラスが属するサブパッケージやコンポーネントを指定する。|
|**@todo** |説明文 |現在はまだ未実装だが、将来予定されている要素の変更をドキュメントする。|
|**@type** |データ型 引数配列値の説明 |引数配列値の型を示すために使用する。構文例については「フック」節または「配列パラメータ」節を参照。|
|**@uses** |クラス::メソッド名() クラス::$変数名 関数名() |**注意**: 過去にはこのタグが使われていたが現在では使用しない。使用している重要な関数やメソッドを参照する。短い説明を含めてもよい。|
|**@var** |データ型 説明 |クラス変数のデータ型と短い説明。コールバックには「**callback**」を付ける。|

<!-- 
[info]
PHPDoc tags work with some text editors/IDEs to display more information about a piece of code. It is useful to developers using those editors to understand what the purpose is, and where they would use it in their code. PhpStorm and Netbeans already support PHPDoc.
 -->
ヒント: テキストエディターや IDE の中には PHPDoc タグを解釈し、コードに関する詳細な情報を表示するものもあります。開発者は各要素の目的が何か、コードのどこで使用するかを容易に理解できます。PhpStorm と Netbeans は PHPDoc をサポートしています。

<!--
The following text editors/IDEs have extensions/bundles you can install that will help you auto-create DocBlocks:

- Notepad++: [DocIt for Notepad++](http://sourceforge.net/projects/nppdocit/) (Windows)
- TextMate: [php.tmbundle](https://github.com/textmate/php.tmbundle) (Mac)
- SublimeText: [sublime packages](https://packagecontrol.io/search/phpdoc) (Windows, Mac, Linux)
-->
次のテキストエディターや IDE では DocBlock の自動作成を支援するエクステンションや部品をインストールできます。

- Notepad++: [DocIt for Notepad++](http://sourceforge.net/projects/nppdocit/) (Windows)
- TextMate: [php.tmbundle](https://github.com/textmate/php.tmbundle) (Mac)
- SublimeText: [sublime packages](https://packagecontrol.io/search/phpdoc) (Windows, Mac, Linux)

<!--
Note: Even with help generating DocBlocks, most code editors don't do a very thorough job - it's likely you'll need to manually fill in certain areas of any generated DocBlocks.
[/info]

### Deprecated Tags

> **Preface:** For the time being, and for the sake of consistency, WordPress Core will continue to use `@subpackage` tags - both when writing new DocBlocks, and editing old ones.
-->
注意: DocBlock 生成エクステンション等を使用しても、大部分のコードエディターの出力は完全ではありません。生成された DocBlock を手動で調整する必要があります。

### 非推奨のタグ

**はじめに**: WordPress コアは新しい DocBlock の記述でも、古いタグの編集でも、しばらくは過去との一貫性のため `@subpackage` タグを使用します。

<!--
>
> Only when the new - external - PSR-5 recommendations are finalized, will across-the-board changes be considered, such as deprecating certain tags.

As proposed in the [new PSR-5](https://github.com/phpDocumentor/fig-standards/blob/master/proposed/phpdoc.md) recommendations, the following PHPDoc tag should be deprecated:

- `@subpackage` (in favor of a unified package tag: `@package Package\Subpackage`)
- `@static` (no longer needed)
- `@staticvar` (no longer needed)

### Other Tags

**`@package` Tag in Plugins and Themes (bundled themes excluded)**
-->
外部で策定中の新しい PSR-5 recommendations 完成後に、タグを非推奨にする等の全体的な変更が検討される予定です。

[新しい PSR-5](https://github.com/phpDocumentor/fig-standards/blob/master/proposed/phpdoc.md) recommendations の提案では、次の PHPDoc タグは非推奨になる予定です。

- `@subpackage` (package タグへ統合の予定: `@package Package\Subpackage`)
- `@static` (不要になった)
- `@staticvar` (不要になった)

### その他のタグ

**プラグインやテーマでの @package タグ (同梱されるテーマは除く)**

<!--
Third-party plugin and theme authors **must not** use `@package WordPress` in their plugins or themes. The `@package` name for plugins should be the plugin name; for themes, it should be the theme name, spaced with underscores: `Twenty_Fifteen`.
-->
サードパーティのプラグイン作成者やテーマ作成者は、自身のプラグインやテーマに「`@package WordPress`」を使わないでください。プラグインの `@package` 名はプラグイン名です。テーマであればテーマ名です。このときスペースは下線で置き換えてください。例: `Twenty_Fifteen`

<!--
**`@author` Tag**
-->
**@author タグ**

<!--
It is WordPress' policy not to use the `@author` tag, except in the case of maintaining it in external libraries. We do not want to imply any sort of "ownership" over code that might discourage contribution.
-->
外部ライブラリでメンテナンスされている場合を除き、 WordPress のポリシーとして @author タグは使用しません。コードに対しては貢献の妨げになるような、いかなる「所有」的なものも含めません。

<!--
**`@copyright` and `@license` Tags**
-->
**@copyright タグと @license タグ**

<!--
The `@copyright` and `@license` tags are used in external libraries and scripts, and should not be used in WordPress core files.

- `@copyright` is used to specify external script copyrights.
- `@license` is used to specify external script licenses.

## Resources

- [Wikipedia on PHPDoc](http://en.wikipedia.org/wiki/PHPDoc)
- [PEAR Standards](http://pear.php.net/manual/en/standards.sample.php)
- [phpDocumentor](http://www.phpdoc.org/)
- [phpDocumentor Tutorial Tags](http://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.pkg.html)
- [Draft PSR-5 recommendations](https://github.com/phpDocumentor/fig-standards/blob/master/proposed/phpdoc.md)
- [Draft PSR-19 recommendations](https://github.com/phpDocumentor/fig-standards/blob/master/proposed/phpdoc-tags.md)
-->
`@copyright` タグと `@license` タグは外部ライブラリやスクリプトに使用されます。WordPress コアファイルには使用しません。

- `@copyright` は外部スクリプトの著作権を明示する場合に使用する。
- `@license` 外部スクリプトのライセンスを明示する場合に使用する。

## リソース

- [Wikipedia](http://en.wikipedia.org/wiki/PHPDoc)
- [PEAR Standards](http://pear.php.net/manual/en/standards.sample.php)
- [phpDocumentor](http://www.phpdoc.org/)
- [phpDocumentor Tutorial Tags](http://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.pkg.html)
- [ドラフト版 PSR-5 recommendations](https://github.com/phpDocumentor/fig-standards/blob/master/proposed/phpdoc.md)
- [ドラフト版 PSR-19 recommendations](https://github.com/phpDocumentor/fig-standards/blob/master/proposed/phpdoc-tags.md)

[原文](https://github.com/WordPress/wpcs-docs/blob/master/inline-documentation-standards/php.md)

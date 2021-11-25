<!-- 
# JavaScript Documentation Standards
 -->
# JavaScript インラインドキュメント規約

<!-- 
WordPress follows the <a href="http://usejsdoc.org/" target="_blank" rel="noopener">JSDoc 3 standard</a> for inline JavaScript documentation.
 -->
WordPress は、インラインの JavaScript ドキュメント規約として「[JSDoc 3 Standard](http://usejsdoc.org/)」に遵守します。

<!-- 
<h2>What Should Be Documented</h2>
 -->
## 何をドキュメントするか

<!-- 
JavaScript documentation in WordPress takes the form of either formatted blocks of documentation or inline comments.
 -->
WordPress での JavaScript ドキュメント形式は、フォーマットされたドキュメントブロックかインラインコメントになります。

<!-- 
The following is a list of what should be documented in WordPress JavaScript files:
 -->
以下のリストは WordPress JavaScript ファイル内でドキュメントする項目の例です。

<!-- 
<ul>
	<li>Functions and class methods</li>
	<li>Objects</li>
	<li>Closures</li>
	<li>Object properties</li>
	<li>Requires</li>
	<li>Events</li>
	<li>File headers</li>
</ul>
 -->
- 関数、およびクラスのメソッド
- オブジェクト
- クロージャ
- オブジェクトプロパティ
- require
- イベント
- ファイルヘッダー

<!-- 
<h2>Documenting Tips</h2>
 -->
## ドキュメントのヒント

<!-- 
<h3>Language</h3>
 -->
### 文体

<!-- 
Short descriptions should be clear, simple, and brief. Document "what" and "when" – "why" should rarely need to be included. The "why" can go in the long description if needed. For example:

Functions and closures are <em>third-person singular</em> elements, meaning <em>third-person singular verbs</em> should be used to describe what each does.
 -->
短い説明を書く場合には、明確でシンプルな、短い文を心がけてください。「いつ」「何を」実行するのかをドキュメントしてください。「なぜ」を含める必要性はほとんどないはずです。 どうしても「なぜ」が必要であれば長い説明に記述してください。

関数やクロージャは「三人称単数」の要素です。説明を記述する場合も「三人称単数の動詞」を使用してください。

<!-- 
[tip]Need help remembering how to conjugate for third-person singular verbs? Imagine prefixing the function, hook, class, or method summary with "It":
<ul>
	<li><em>Good:</em> "(It) Does something."</li>
	<li><em>Bad:</em> "(It) Do something."</li>
</ul>
[/tip]
 -->
ヒント: 三人称単数の動詞の活用に悩む場合は、関数やクロージャの説明を書く場合、先頭に「It」をつけて考えてください。
- 正: “(It) Does something.”
- 誤: “(It) Do something.”

<!-- 
<strong>Functions:</strong> What does the function do?
 -->
関数: この関数は「何を」するのか?
<!-- 
<ul>
	<li>Good: Handles a click on X element.</li>
	<li>Bad: Included for back-compat for X element.</li>
</ul>
 -->
- 正: Handles a click on X element. (要素「X」のクリックを処理する)
- 誤: Included for back-compat for X element. (要素「X」の後方互換性のために追加された)

<!-- 
<strong>@since</strong>: The recommended tool to use when searching for the version something was added to WordPress is <a href="https://make.wordpress.org/core/handbook/svn/code-history/#using-subversion-annotate">svn blame</a>.

If, after using these tools, the version number cannot be determined, use <code>@since Unknown</code>.

<strong>Code Refactoring:</strong> Do not refactor code in the file when changes to the documentation.
 -->
@since: WordPress に追加されたバージョン番号等を調べる場合は、ツール「[svn blame](https://make.wordpress.org/core/handbook/svn/code-history/#using-subversion-annotate)」の使用を推奨します。

ツールを使用してもバージョン番号を特定できない場合は、「@since Unknown」を使用してください。

**コードリファクタリング**: ドキュメントを編集する際に、ファイル内のコードはリファクタリングしないでください。

<!-- 
<h3>Grammar</h3>
 -->
### 文法

<!-- 
Descriptive elements should be written as complete sentences. The one exception to this standard is file header summaries, which are intended as file "titles" more than sentences.

The serial (Oxford) comma should be used when listing elements in summaries, descriptions, and parameter or return descriptions.
 -->
説明文の要素は完全な文として記述してください。例外はファイルヘッダーの Summary です。この Summary は文章ではなく「タイトル」を意図しているためです。

Summary、Description、Parameter や Return の Description 内で要素を並べる際には serial comma (Oxford comma) を使用してください。(例: A, B and C)

<!-- 
<h2>Formatting Guidelines</h2>
 -->
## フォーマットガイドライン

<!-- 
The following guidelines should be followed to ensure that the content of the doc blocks can be parsed properly for inclusion in the code reference.
 -->
次のガイドラインに従うことで DocBlock の内容が、コードリファレンス用に正しくパースされます。

<!-- 
<strong>Short descriptions:</strong>
 -->
**短い説明:**

<!-- 
Short descriptions should be a single sentence and contain no markup of any kind. If the description refers to an HTML element or tag, then it should be written as "link tag", not "&lt;a&gt;". For example: "Fires when printing the link tag in the header".
 -->
短い説明は単一の文で書き、マークアップしないでください。説明が HTML 要素やタグを参照する場合は、「&lt;a&gt;」ではなく、「link タグ」のように記述してください。例: “Fires when printing the link tag in the header”。

<!-- 
<strong>Long descriptions:</strong>
 -->
**長い説明:**

<!-- 
Markdown can be used, if needed, in a long description.
 -->
長い説明では必要であればマークダウンを使用できます。

<!-- 
<strong>@param and @return tags:</strong>
 -->
**@param および @return タグ:**

<!-- 
No HTML or markdown is permitted in the descriptions for these tags. HTML elements and tags should be written as "audio element" or "link tag".
 -->
これらのタグの説明では HTML もマークダウンも許されません。HTML 要素やタグは「audio 要素」や「link タグ」のように記述してください。

<!-- 
<h3>Line wrapping</h3>
 -->
### 行の折り返し

<!-- 
DocBlock text should wrap to the next line after 80 characters of text. If the DocBlock itself is indented on the left 20 character positions, the wrap could occur at position 100, but should not extend beyond a total of 120 characters wide.
 -->
DocBlock のテキストは80文字分で次の行に折り返してください。例えば DocBlock が20文字分インデントしている場合には、100文字目の位置で折り返します。ただし120文字目以上は超えないでください。

<!-- 
<h3>Aligning comments</h3>
 -->
### コメントの行揃え

<!-- 
Related comments should be spaced so that they align to make them more easily readable.

For example:
 -->
関連するコメントは、スペースを使用して位置を揃え、可読性を上げてください。

例:

```javascript
/**
 * @param {very_long_type} name           説明。
 * @param {type}           very_long_name 説明。
 */
```

<!-- 
<h2>Functions</h2>
 -->
## 関数

<!-- 
Functions should be formatted as follows:
 -->
関数は次のようにフォーマットしてください。

<!-- 
<ul>
	<li><strong>Summary:</strong> A brief, one line explanation of the purpose of the function. Use a period at the end.</li>
	<li><strong>Description:</strong> A supplement to the summary, providing a more detailed description. Use a period at the end.</li>
	<li><strong>@deprecated x.x.x:</strong> Only use for deprecated functions, and provide the version the function was deprecated which should always be 3-digit (e.g. @since 3.6.0), and the function to use instead.</li>
	<li><strong>@since x.x.x:</strong> Should be 3-digit for initial introduction (e.g. @since 3.6.0). If significant changes are made, additional @since tags, versions, and descriptions should be added to serve as a changelog.</li>
	<li><strong>@access:</strong> Only use for functions if private. If the function is private, it is intended for internal use only, and there will be no documentation for it in the code reference.</li>
	<li><strong>@class:</strong> Use for class constructors.</li>
	<li><strong>@augments:</strong> For class constuctors, list direct parents.</li>
	<li><strong>@mixes:</strong> List mixins that are mixed into the object.</li>
	<li><strong>@alias:</strong> If this function is first assigned to a temporary variable this allows you to change the name it's documented under.</li>
	<li><strong>@memberof:</strong> Namespace that this function is contained within if JSDoc is unable to resolve this automatically.</li>
	<li><strong>@static:</strong> For classes, used to mark that a function is a static method on the class constructor.</li>
	<li><strong>@see:</strong> A function or class relied on.</li>
	<li><strong>@link:</strong> URL that provides more information.</li>
	<li><strong>@fires:</strong> Event fired by the function. Events tied to a specific class should list the class name.</li>
	<li><strong>@listens:</strong> Events this function listens for. An event must be prefixed with the event namespace. Events tied to a specific class should list the class name.</li>
	<li><strong>@global:</strong> Marks this function as a global function to be included in the global namespace.</li>
	<li><strong>@param:</strong> Give a brief description of the variable; denote particulars (e.g. if the variable is optional, its default) with <a href="http://usejsdoc.org/tags-param.html">JSDoc @param syntax</a>. Use a period at the end.</li>
	<li><strong>@yield:</strong> For <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*">generator functions</a>, a description of the values expected to be yielded from this function. As with other descriptions, include a period at the end.</li>
	<li><strong>@return:</strong> Note the period after the description.</li>
</ul>
 -->
- **要約:** 関数の目的を説明する簡潔な単一の文。末尾はピリオド。
- **説明:** Summary を補足する詳細な説明。文の末尾はピリオド。
- **@deprecated x.x.x:** 非推奨になった関数のみに使用する。どの WordPress バージョンで非推奨になったかを示す常に3組の数字 (例 @deprecated 3.6.0) と代替の関数。
- **@since x.x.x:** 最初に導入されたバージョンを表す3組の数字 (例: @since 3.6.0)。大きな変更が合った場合は、履歴の目的で、追加の @since タグ、バージョン、説明を追加する。 
- **@access:** 関数が private の場合のみ使用。関数が private なら、内部使用専用であり、コードリファレンスにドキュメントされない。
- **@class:** クラスのコンストラクタに使用
- **@augments:** クラスのコンストラクタで、クラスの直接の親をリストする。
- **@mixes:** オブジェクトにミックスされる mixin をリストする。
- **@alias:** 最初にこの関数が一時変数に割り当てられた場合、名前を変更することができる。
- **@memberof:** JSDoc が自動的に解決できない場合、この関数が含まれる名前空間
- **@static:** クラスに対し、クラスコンストラクタで関数が static メソッドであることを示す。
- **@see:** 依存する関数やクラス
- **@link:** 詳細情報への URL
- **@fires:** 関数から発火されるイベント。特定のクラスに紐付けられたイベントはクラス名をリストしなければならない。
- **@listens:** この関数が期待するイベント。イベントはイベント名前空間の接頭辞を付ける必要がある。特定のクラスに紐付けられたイベントはクラス名をリストしなければならない。
- **@global:** この関数をグローバル名前空間に含まれるグローバル関数としてマークする。
- **@param:** 変数の簡単な説明。[JSDoc @param 構文](http://usejsdoc.org/tags-param.html)を使用して、例えば、変数がオプションなら、そのデフォルト値などの事項を記述する。最後はピリオド。
- **@yield:** [ジェネレータ関数](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) に関して、この関数から yield されると期待する値の説明。他の説明同様、最後はピリオドで終える。
- **@return:** 注意: 説明の末尾はピリオド

<!-- 
```javascript
/**
 * Summary. (use period)
 *
 * Description. (use period)
 *
 * @since      x.x.x
 * @deprecated x.x.x Use new_function_name() instead.
 * @access     private
 *
 * @class
 * @augments parent
 * @mixes    mixin
 * 
 * @alias    realName
 * @memberof namespace
 *
 * @see  Function/class relied on
 * @link URL
 * @global
 *
 * @fires   eventName
 * @fires   className#eventName
 * @listens event:eventName
 * @listens className~event:eventName
 *
 * @param {type}   var           Description.
 * @param {type}   [var]         Description of optional variable.
 * @param {type}   [var=default] Description of optional variable with default variable.
 * @param {Object} objectVar     Description.
 * @param {type}   objectVar.key Description of a key in the objectVar parameter.
 *
 * @yield {type} Yielded value description.
 *
 * @return {type} Return value description.
 */
```
 -->
```javascript
/**
 * 要約 (末尾はピリオド)
 *
 * 説明 (末尾はピリオド)
 *
 * @since      x.x.x
 * @deprecated x.x.x Use new_function_name() instead. (代替の関数)
 * @access     private
 *
 * @class
 * @augments parent
 * @mixes    mixin
 * 
 * @alias    realName
 * @memberof namespace
 *
 * @see  依存する Function/class
 * @link URL
 * @global
 *
 * @fires   eventName
 * @fires   className#eventName
 * @listens event:eventName
 * @listens className~event:eventName
 *
 * @param {type}   var           説明。
 * @param {type}   [var]         オプション値の説明。
 * @param {type}   [var=default] デフォルト値のあるオプション変数の説明。
 * @param {Object} objectVar     説明。
 * @param {type}   objectVar.key objectVar パラメータ内のキーの説明。
 *
 * @yield {type} yield 値の説明。
 *
 * @return {type} 戻り値の説明。
 */
```

<!-- 
<h2>Backbone classes</h2>
 -->
## Backbone クラス

<!-- 
Backbone's <code>extend</code> calls should be formatted as follows:
 -->
Backbone の `extend` 呼び出しは次のようにフォーマットしてください。

<!-- 
<ul>
	<li><strong>@lends</strong> This tag will allow JSDoc to recognize the <code>extend</code> function from Backbone as a class definition. This should be placed right before the Object that contains the class definition.</li>
</ul>
 -->
- **@lends** このタグは JSDoc に Backbone からの `extend` 関数をクラス定義として認識させます。クラス定義を含む Object の直前に置いてください。

<!-- 
Backbone's <code>initialize</code> functions should be formatted as follows:
 -->
Backbone の `initialize` 関数は次のようにフォーマットしてください。

<!-- 
<ul>
	<li><strong>Summary:</strong> A brief, one line explanation of the purpose of the function. Use a period at the end.</li>
	<li><strong>Description:</strong> A supplement to the summary, providing a more detailed description. Use a period at the end.</li>
	<li><strong>@deprecated x.x.x:</strong> Only use for deprecated classes, and provide the version the class was deprecated which should always be 3-digit (e.g. @since 3.6.0), and the class to use instead.</li>
	<li><strong>@since x.x.x:</strong> Should be 3-digit for initial introduction (e.g. @since 3.6.0). If significant changes are made, additional @since tags, versions, and descriptions should be added to serve as a changelog.</li>
	<li><strong>@constructs</strong> Marks this function as the constructor of this class.</li>
	<li><strong>@augments:</strong> List direct parents.</li>
	<li><strong>@mixes:</strong> List mixins that are mixed into the class.</li>
	<li><strong>@requires:</strong> Lists modules that this class requires. Multiple <strong>@requires</strong> tags can be used.</li>
	<li><strong>@alias:</strong> If this class is first assigned to a temporary variable this allows you to change the name it's documented under.</li>
	<li><strong>@memberof:</strong> Namespace that this class is contained within if JSDoc is unable to resolve this automatically.</li>
	<li><strong>@static:</strong> For classes, used to mark that a function is a static method on the class constructor.</li>
	<li><strong>@see:</strong> A function or class relied on.</li>
	<li><strong>@link:</strong> URL that provides more information.</li>
	<li><strong>@fires:</strong> Event fired by the constructor. Should list the class name.</li>
	<li><strong>@param:</strong> Document the arguments passed to the constructor even if not explicitly listed in <code>initialize</code>. Use a period at the end.
<ul>
	<li>Backbone Models are passed <code>attributes</code> and <code>options</code> parameters.</li>
	<li>Backbone Views are passed an <code>options</code> parameter.</li>
</ul>
</li>
</ul>
 -->
- **要約:** 関数の目的を説明する簡潔な単一の文。末尾はピリオド。
- **説明:** Summary を補足する詳細な説明。文の末尾はピリオド。
- **@deprecated x.x.x:** 非推奨になったクラスのみに使用する。どの WordPress バージョンで非推奨になったかを示す常に3組の数字 (例 @deprecated 3.6.0) と代替のクラス。
- **@since x.x.x:** 最初に導入されたバージョンを表す3組の数字 (例: @since 3.6.0)。大きな変更が合った場合は、履歴の目的で、追加の @since タグ、バージョン、説明を追加する。 
- **@constructs:** この関数をクラスのコンストラクタとしてマークする。
- **@augments:** 直接の親をリストする。
- **@mixes:** クラスにミックスされる mixin をリストする。
- **@requires:** このクラスが必要とするモジュールをリストする。複数の @requires タグを使用可能。
- **@alias:** 最初にこのクラスが一時変数に割り当てられた場合、名前を変更することができる。
- **@memberof:** JSDoc が自動的に解決できない場合、このクラスが含まれる名前空間
- **@static:** クラスに対し、クラスコンストラクタで関数が static メソッドであることを示す。
- **@see:** 依存する関数やクラス
- **@link:** 詳細情報への URL
- **@fires:** コンストラクターから発火されるイベント。クラス名をリストする。
- **@param:** initializeに明示的にリストしていないものも含め、コンストラクターに渡す引数をドキュメントする。最後はピリオド。
  - Backbone Models は attributes と options パラメータに渡される。
  - Backbone Views は options パラメータに渡される。

<!-- 
```javascript
Class = Parent.extend( /** @lends namespace.Class.prototype */{
	/**
	 * Summary. (use period)
	 *
	 * Description. (use period)
	 *
	 * @since      x.x.x
	 * @deprecated x.x.x Use new_function_name() instead.
	 * @access     private
	 *
	 * @constructs namespace.Class
	 * @augments   Parent
	 * @mixes      mixin
	 *
	 * @alias    realName
	 * @memberof namespace
	 *
	 * @see   Function/class relied on
	 * @link  URL
	 * @fires Class#eventName
	 *
	 * @param {Object} attributes     The model's attributes.
	 * @param {type}   attributes.key One of the model's attributes.
	 * @param {Object} [options]      The model's options.
	 * @param {type}   attributes.key One of the model's options.
	 */
	initialize: function() {
		//Do stuff.
	}
} );
```
 -->
```javascript
Class = Parent.extend( /** @lends namespace.Class.prototype */{
	/**
	 * 要約 (末尾はピリオド)
	 *
	 * 説明 (末尾はピリオド)
	 *
	 * @since      x.x.x
	 * @deprecated x.x.x Use new_function_name() instead. (代替の関数)
	 * @access     private
	 *
	 * @constructs namespace.Class
	 * @augments   Parent
	 * @mixes      mixin
	 *
	 * @alias    realName
	 * @memberof namespace
	 *
	 * @see   依存する Function/class
	 * @link  URL
	 * @fires Class#eventName
	 *
	 * @param {Object} attributes     モデルの属性。
	 * @param {type}   attributes.key モデルの属性の1つ。
	 * @param {Object} [options]      モデルのオプション。
	 * @param {type}   attributes.key モデルのオプションの1つ。
	 */
	initialize: function() {
		// 何かを実行する。
	}
} );
```

<!-- 
If a Backbone class does not have an initialize function it should be documented by using @inheritDoc as follows:
 -->
Backbone クラスに initialize 関数がない場合、次のように @inheritDoc を使用してドキュメントしてください。

<!-- 
```javascript
/**
 * Summary. (use period)
 *
 * Description. (use period)
 *
 * @since      x.x.x
 * @deprecated x.x.x Use new_function_name() instead.
 * @access     private
 *
 * @constructs namespace.Class
 * @memberOf   namespace
 * @augments   Parent
 * @mixes      mixin
 * @inheritDoc
 *
 * @alias    realName
 * @memberof namespace
 *
 * @see   Function/class relied on
 * @link  URL
 */
Class = Parent.extend( /** @lends namespace.Class.prototype */{
// Functions and properties.
} );
```
 -->
```javascript
/**
 * 要約 (末尾はピリオド)
 *
 * 説明 (末尾はピリオド)
 *
 * @since      x.x.x
 * @deprecated x.x.x Use new_function_name() instead. (代替の関数)
 * @access     private
 *
 * @constructs namespace.Class
 * @memberOf   namespace
 * @augments   Parent
 * @mixes      mixin
 * @inheritDoc
 *
 * @alias    realName
 * @memberof namespace
 *
 * @see   依存する Function/class
 * @link  URL
 */
Class = Parent.extend( /** @lends namespace.Class.prototype */{
// 関数とプロパティ。
} );
```

<!-- 
<blockquote>Note: This currently doesn't provide the expected functionality due to a bug with JSDoc's inheritDoc tag. See the issue <a href="https://github.com/jsdoc3/jsdoc/issues/1012">here</a></blockquote>
 -->
> 注意: 現在、JSDoc の inheritDoc タグのバグのため、期待どおりに機能しません。こちらの [issue](https://github.com/jsdoc3/jsdoc/issues/1012) を参照してください。

<!-- 
<h2>Local functions</h2>
 -->
## ローカル関数

<!-- 
At times functions will be assigned to a local variable before being assigned as a class member.
Such functions should be marked as inner functions of the namespace that uses them using <code>~</code>.
The functions should be formatted as follows:
 -->
関数がクラスメンバーとして割り当てられる前に、ローカル変数に割り当てられる場合があります。
このような関数は、<code>~</code> を使用して名前空間の内部関数としてマークしてください。
次のようにフォーマットします。

<!-- 
```javascript
/**
 * Function description, you can use any JSDoc here as long as the function remains private.
 *
 * @alias namespace~doStuff
 */
var doStuff = function () {
// Do stuff.
};

Class = Parent.extend( /** @lends namespace.Class.prototype */{
	/**
	 * Class description
	 *
	 * @constructs namespace.Class
	 *
	 * @borrows namespace~doStuff as prototype.doStuff
	 */
	initialize: function() {
	//Do stuff.
	},

	/*
	 * This function will automatically have it's documentation copied from above.
	 * You should make a comment ( not a DocBlock using /**, instead use /* or // )
	 * noting that you're describing this function using @borrows.
	 */
	doStuff: doStuff,
} );
```
 -->
```javascript
/**
 * 関数の説明。関数が private である限り、ここで任意の JSDoc を使用可能
 *
 * @alias namespace~doStuff
 */
var doStuff = function () {
// 何かを実行する。
};

Class = Parent.extend( /** @lends namespace.Class.prototype */{
	/**
	 * クラス定義
	 *
	 * @constructs namespace.Class
	 *
	 * @borrows namespace~doStuff as prototype.doStuff
	 */
	initialize: function() {
	// 何かを実行する。
	},

	/*
	 * この関数は自動的に、上からコピーされたドキュメントを持つ。
	 * コメントで @borrows を使用して関数を説明していることを注記しなければならない。
	 * このとき DocBlock の /** ではなく、/* または // を使用すること。
	 */
	doStuff: doStuff,
} );
```
<!-- 
<h2>Local ancestors</h2>
 -->
<h2>ローカルの ancestor</h2>

<!-- 
At times classes will have Ancestors that are only assigned to a local variable. Such classes should be assigned to the namespace their children are and be made inner classes using <code>~</code>.
These should be documented as follows:
 -->
クラスは、ローカル変数にしか割り当てられない ancestor (先祖) を持つ場合があります。このようなクラスは、その子クラスの名前空間に割り当て、<code>~</code> を使用して内部クラスにする必要があります。

<!-- 
<h2>Class members</h2>
 -->
<h2>クラスメンバー</h2>

<!-- 
Class members should be formatted as follows:
 -->
クラスメンバーは次のようにフォーマットしてください。

<!-- 
<ul>
	<li><strong>Short description:</strong> Use a period at the end.</li>
	<li><strong>@since x.x.x:</strong> Should be 3-digit for initial introduction (e.g. @since 3.6.0). If significant changes are made, additional @since tags, versions, and descriptions should be added to serve as a changelog.</li>
	<li><strong>@access:</strong> If the members is private, protected or public. Private members are intended for internal use only.</li>
	<li><strong>@type:</strong> List the type of the class member.</li>
	<li><strong>@property</strong> List all properties this object has in case it's an Object. Use a period at the end.</li>
	<li><strong>@member:</strong> Optionally use this to override JSDoc's member detection in place of <strong>@type</strong> to force a class member.</li>
	<li><strong>@memberof:</strong> Optionally use this to override what class this is a member of.</li>
</ul>
 -->

- **短い説明:** 末尾にはピリオドを使用する。
- **@since x.x.x:** 常に3組の数字 (例: @since 3.6.0)
- **@access:** メンバーが private、protected、public のどれかを示す。private メンバーは内部のみでの使用を想定する。
- **@type:** クラスメンバーのタイプをリストする。
- **@property:** Object の場合、このオブジェクトが持つすべてのプロパティをリストする。最後にピリオドを使用する。
- **@member:** オプションとして、 JSDoc のメンバー検知を上書きする。@type の代わりにクラスメンバーに強制する。
- **@memberof:** オプションとして、どのクラスのメンバーかを上書きする。

<!-- 
```javascript
/**
 * Short description. (use period)
 *
 * @since  x.x.x
 * @access (private, protected, or public)
 *
 * @type     {type}
 * @property {type} key Description.
 *
 * @member   {type} realName
 * @memberof className
 */
```
 -->
```javascript
/**
 * 短い説明 (末尾はピリオド)
 *
 * @since  x.x.x
 * @access (private、protected、または public)
 *
 * @type     {type}
 * @property {type} key 説明。
 *
 * @member   {type} realName
 * @memberof className
 */
```
<!-- 
<h2>Namespaces</h2>
 -->
<h2>名前空間</h2>
<!-- 
Namespaces should be formatted as follows:
 -->
名前空間は次のようにフォーマットしてください。

<!-- 
<ul>
	<li><strong>Short description:</strong> Use a period at the end.</li>
	<li><strong>@namespace:</strong> Marks this symbol as a namespace, optionally provide a name as an override.</li>
	<li><strong>@since x.x.x:</strong> Should be 3-digit for initial introduction (e.g. @since 3.6.0). If significant changes are made, additional @since tags, versions, and descriptions should be added to serve as a changelog.</li>
	<li><strong>@memberof:</strong> Namespace that this namespace is contained in.</li>
	<li><strong>@property:</strong> Properties that this namespace exposes. Use a period at the end.</li>
</ul>
 -->
- **短い説明:** 最後にピリオドを使用する。
- **@namespace:** このシンボルを名前空間としてマークする。オプションとして上書きする名前を提供する。
- **@since x.x.x:** 常に3組の数字 (例: @since 3.6.0)
- **@memberof:** この名前空間が含まれる名前空間。
- **@property:** この名前空間が expose するプロパティ。最後にピリオドを使用する。

<!-- 
```javascript
/**
 * Short description. (use period)
 *
 * @namespace realName
 * @memberof  parentNamespace
 *
 * @since x.x.x
 *
 * @property {type} key Description.
 */
```
 -->
```javascript
/**
 * 短い説明 (末尾はピリオド)
 *
 * @namespace realName
 * @memberof  parentNamespace
 *
 * @since x.x.x
 *
 * @property {type} key 説明。
 */
```
<!-- 
<h2>Inline Comments</h2>
 -->
## インラインコメント

<!-- 
Inline comments inside methods and functions should be formatted as follows:
 -->
メソッドや関数のインラインコメントは次のようにフォーマットしてください。

<!-- 
<h3>Single line comments</h3>
 -->
### 単一行コメント

<!-- 
```javascript
// Extract the array values.
```
 -->
```javascript
// Extract the array values.
```

<!-- 
<h3>Multi-line comments</h3>
 -->
### 複数行コメント

```javascript
/*
 * This is a comment that is long enough to warrant being stretched over
 * the span of multiple lines. You'll notice this follows basically
 * the same format as the JSDoc wrapping and comment block style.
 */
```
<!-- 
<strong>Important note:</strong> Multi-line comments must not begin with <code>/**</code> (double asterisk). Use <code>/*</code> (single asterisk) instead.
 -->
**重要な注意:** 複数行のコメントを `/**` (2つのアスタリスク) で始めないでください。代わりに `/*` (1つのアスタリスク) を使用してください。

<!-- 
<h2>File Headers</h2>
 -->
## ファイルヘッダー

<!-- 
The JSDoc file header block is used to give an overview of what is contained in the file.

Whenever possible, all WordPress JavaScript files should contain a header block.

WordPress uses JSHint for general code quality testing. Any inline configuration options should be placed at the end of the header block.
 -->
JSDoc ファイルヘッダーブロックにはファイルに含まれる内容の概要を書きます。

可能であれば常にすべての WordPress JavaScript ファイルにヘッダーブロックを記述してください。

WordPress は JSHint を使用して全般的なコードの品質を検証します。インライン構成オプションはヘッダーブロックの最後に記述してください。

<!-- 
```javascript
/**
 * Summary. (use period)
 *
 * Description. (use period)
 *
 * @link   URL
 * @file   This files defines the MyClass class.
 * @author AuthorName.
 * @since  x.x.x
 */
 
/** jshint {inline configuration here} */
```
 -->
```javascript
/**
 * 要約 (末尾はピリオド)
 *
 * 説明 (末尾はピリオド)
 *
 * @link   URL
 * @file   This files defines the MyClass class.
 * @author AuthorName.
 * @since  x.x.x
 */
 
/** jshint {ここにインライン構成} */
```
<!-- 
<h2>Supported JSDoc Tags</h2>
 -->
## サポートされる JSDoc タグ

<!-- 
<table>
<thead>
<tr>
<th style="width: 15%">Tag</th>
<th style="width: 85%">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>@abstract</td>
<td>This method can be implemented (or overridden) by the inheritor.</td>
</tr>
<tr>
<td>@access</td>
<td>Specify the access level of this member (private, public, or protected).</td>
</tr>
<tr>
<td>@alias</td>
<td>Treat a member as if it had a different name.</td>
</tr>
<tr>
<td>@augments</td>
<td>This class inherits from a parent class.</td>
</tr>
<tr>
<td>@author</td>
<td>Identify the author of an item.</td>
</tr>
<tr>
<td>@borrows</td>
<td>This object uses something from another object.</td>
</tr>
<tr>
<td>@callback</td>
<td>Document a callback function.</td>
</tr>
<tr>
<td>@class</td>
<td>This function is a class constructor.</td>
</tr>
<tr>
<td>@classdesc</td>
<td>Use the following text to describe the entire class.</td>
</tr>
<tr>
<td>@constant</td>
<td>Document an object as a constant.</td>
</tr>
<tr>
<td>@constructs</td>
<td>This function member will be the constructor for the previous class.</td>
</tr>
<tr>
<td>@copyright</td>
<td>Document some copyright information.</td>
</tr>
<tr>
<td>@default</td>
<td>Document the default value.</td>
</tr>
<tr>
<td>@deprecated</td>
<td>Document that this is no longer the preferred way.</td>
</tr>
<tr>
<td>@description</td>
<td>Describe a symbol.</td>
</tr>
<tr>
<td>@enum</td>
<td>Document a collection of related properties.</td>
</tr>
<tr>
<td>@event</td>
<td>Document an event.</td>
</tr>
<tr>
<td>@example</td>
<td>Provide an example of how to use a documented item.</td>
</tr>
<tr>
<td>@exports</td>
<td>Identify the member that is exported by a JavaScript module.</td>
</tr>
<tr>
<td>@external</td>
<td>Document an external class/namespace/module.</td>
</tr>
<tr>
<td>@file</td>
<td>Describe a file.</td>
</tr>
<tr>
<td>@fires</td>
<td>Describe the events this method may fire.</td>
</tr>
<tr>
<td>@function</td>
<td>Describe a function or method.</td>
</tr>
<tr>
<td>@global</td>
<td>Document a global object.</td>
</tr>
<tr>
<td>@ignore</td>
<td>[todo] Remove this from the final output.</td>
</tr>
<tr>
<td>@inner</td>
<td>Document an inner object.</td>
</tr>
<tr>
<td>@instance</td>
<td>Document an instance member.</td>
</tr>
<tr>
<td>@kind</td>
<td>What kind of symbol is this?</td>
</tr>
<tr>
<td>@lends</td>
<td>Document properties on an object literal as if they belonged to a symbol with a given name.</td>
</tr>
<tr>
<td>@license</td>
<td>[todo] Document the software license that applies to this code.</td>
</tr>
<tr>
<td>@link</td>
<td>Inline tag - create a link.</td>
</tr>
<tr>
<td>@member</td>
<td>Document a member.</td>
</tr>
<tr>
<td>@memberof</td>
<td>This symbol belongs to a parent symbol.</td>
</tr>
<tr>
<td>@mixes</td>
<td>This object mixes in all the members from another object.</td>
</tr>
<tr>
<td>@mixin</td>
<td>Document a mixin object.</td>
</tr>
<tr>
<td>@module</td>
<td>Document a JavaScript module.</td>
</tr>
<tr>
<td>@name</td>
<td>Document the name of an object.</td>
</tr>
<tr>
<td>@namespace</td>
<td>Document a namespace object.</td>
</tr>
<tr>
<td>@param</td>
<td>Document the parameter to a function.</td>
</tr>
<tr>
<td>@private</td>
<td>This symbol is meant to be private.</td>
</tr>
<tr>
<td>@property</td>
<td>Document a property of an object.</td>
</tr>
<tr>
<td>@protected</td>
<td>This member is meant to be protected.</td>
</tr>
<tr>
<td>@public</td>
<td>This symbol is meant to be public.</td>
</tr>
<tr>
<td>@readonly</td>
<td>This symbol is meant to be read-only.</td>
</tr>
<tr>
<td>@requires</td>
<td>This file requires a JavaScript module.</td>
</tr>
<tr>
<td>@return</td>
<td>Document the return value of a function.</td>
</tr>
<tr>
<td>@see</td>
<td>Refer to some other documentation for more information.</td>
</tr>
<tr>
<td>@since</td>
<td>Documents the version at which the function was added, or when significant changes are made.</td>
</tr>
<tr>
<td>@static</td>
<td>Document a static member.</td>
</tr>
<tr>
<td>@this</td>
<td>What does the 'this' keyword refer to here?</td>
</tr>
<tr>
<td>@throws</td>
<td>Describe what errors could be thrown.</td>
</tr>
<tr>
<td>@todo</td>
<td>Document tasks to be completed.</td>
</tr>
<tr>
<td>@tutorial</td>
<td>Insert a link to an included tutorial file.</td>
</tr>
<tr>
<td>@type</td>
<td>Document the type of an object.</td>
</tr>
<tr>
<td>@typedef</td>
<td>Document a custom type.</td>
</tr>
<tr>
<td>@variation</td>
<td>Distinguish different objects with the same name.</td>
</tr>
<tr>
<td>@version</td>
<td>Documents the version number of an item.</td>
</tr>
<tr>
<td>@yield</td>
<td>Document the yielded values of a generator function.</td>
</tr>
</tbody>
</table>
 -->
|タグ |	説明|
|----|-----|
|@abstract | このメソッドは継承側から実装、またはオーバーライドできる。|
|@access|このメンバーのアクセスレベルを指定する (private、public、protected)|
|@alias|メンバーに別名があるものとして扱う。|
|@augments|このクラスは親クラスから継承する。|
|@author|項目の作者を識別|
|@borrows|このオブジェクトは別のオブジェクトの何かを使用する。|
|@callback|コールバック関数をドキュメント|
|@class|この関数はクラスのコンストラクター|
|@classdesc|クラス全体の記述に次のテキストを使用する。|
|@constant|オブジェクトを定数としてドキュメント|
|@constructs|この関数メンバーは前のクラスのコンストラクターになる。|
|@copyright|著作権情報をドキュメント|
|@default|デフォルト値をドキュメント|
|@deprecated|非推奨の機能であることをドキュメント|
|@description|シンボルについて記述|
|@enum|関連するプロパティのコレクションをドキュメント|
|@event|イベントをドキュメント|
|@example|ドキュメントされた項目の使用例を提示|
|@exports|JavaScript モジュールからエクスポートされるメンバーを識別|
|@external|外部クラス、名前空間、モジュールをドキュメント|
|@file|ファイルについて記述|
|@fires|このメソッドが発火するイベントを説明する。|
|@function|関数、またはメソッドについて記述|
|@global|グローバルオブジェクトをドキュメント|
|@ignore|[todo] 最終出力かこれらを除去|
|@inner|内部オブジェクトをドキュメント|
|@instance|インスタンスメンバーをドキュメント|
|@kind|このシンボルの種類は何か?|
|@lends|与えられた名前でシンボルに属すようにオブジェクトリテラルのプロパティをドキュメント|
|@license|[todo] このコードに適用されるソフトウエアライセンスをドキュメント|
|@link|インラインタグ – リンクを作成|
|@member|メンバーをドキュメント|
|@memberof|このシンボルは親のシンボルに属す。|
|@mixes|このオブジェクトは他のオブジェクトのすべてのメンバーを mixin する。|
|@mixin|mixin オブジェクトをドキュメント|
|@module|JavaScript モジュールをドキュメント|
|@name|オブジェクトの名前をドキュメント|
|@namespace|名前空間オブジェクトをドキュメント|
|@param|関数へのパラメータをドキュメント|
|@private|このシンボルは private|
|@property|オブジェクトのプラパティをドキュメント|
|@protected|メンバーは protected|
|@public|このシンボルは public|
|@readonly|このシンボルはリードオンリー|
|@requires|このファイルは JavaScript モジュールが必要|
|@returns|関数の戻り値をドキュメント|
|@see|詳細については他のドキュメントを参照|
|@since|いつ、この機能は追加されたか?|
|@static|static メンバーをドキュメント|
|@this|‘this’ キーワードはここで何を参照するか?|
|@throws|どんなエラーがスローされるかを記述|
|@todo|完了すべきタスクをドキュメント|
|@tutorial|同梱されるチュートリアルファイルへのリンクを挿入|
|@type|オブジェクトの型をドキュメント|
|@typedef|カスタムタイプをドキュメント|
|@variation|同一名で異なるオブジェクトを区別|
|@version|アイテムのバージョン番号をドキュメント|

<!-- 
<h2>Unsupported JSDoc Tags</h2>
 -->
## サポートされない JSDoc タグ

<!-- 
<table>
<thead>
<tr>
<th style="width: 15%">Tag</th>
<th style="width: 85%">Why it's not supported</th>
</tr>
</thead>
<tbody>
<tr>
<td>@summary</td>
<td>Should not be used. See the example of how to separate a summary from the full description.</td>
</tr>
<tr>
<td>@virtual</td>
<td>An unsupported synonym. Use @abstract instead.</td>
</tr>
<tr>
<td>@extends</td>
<td>An unsupported synonym. Use @augments instead.</td>
</tr>
<tr>
<td>@constructor</td>
<td>An unsupported synonym. Use @class instead.</td>
</tr>
<tr>
<td>@const</td>
<td>An unsupported synonym. Use @constant instead.</td>
</tr>
<tr>
<td>@defaultvalue</td>
<td>An unsupported synonym. Use @default instead.</td>
</tr>
<tr>
<td>@desc</td>
<td>An unsupported synonym. Use @description instead.</td>
</tr>
<tr>
<td>@host</td>
<td>An unsupported synonym. Use @external instead.</td>
</tr>
<tr>
<td>@fileoverview</td>
<td>An unsupported synonym. Use @file instead.</td>
</tr>
<tr>
<td>@overview</td>
<td>An unsupported synonym. Use @file instead.</td>
</tr>
<tr>
<td>@emits</td>
<td>An unsupported synonym. Use @fires instead.</td>
</tr>
<tr>
<td>@func</td>
<td>An unsupported synonym. Use @function instead.</td>
</tr>
<tr>
<td>@method</td>
<td>An unsupported synonym. Use @function instead.</td>
</tr>
<tr>
<td>@var</td>
<td>An unsupported synonym. Use @member instead.</td>
</tr>
<tr>
<td>@emits</td>
<td>An unsupported synonym. Use @fires instead.</td>
</tr>
<tr>
<td>@arg</td>
<td>An unsupported synonym. Use @param instead.</td>
</tr>
<tr>
<td>@argument</td>
<td>An unsupported synonym. Use @param instead.</td>
</tr>
<tr>
<td>@prop</td>
<td>An unsupported synonym. Use @property instead.</td>
</tr>
<tr>
<td>@returns</td>
<td>An unsupported synonym. Use @return instead.</td>
</tr>
<tr>
<td>@exception</td>
<td>An unsupported synonym. Use @throws instead.</td>
</tr>
</tbody>
</table>
 -->


|タグ|なぜサポートされないか|
|----|------------------|
|@summary|使わない。完全な説明 (full description) から要約 (summary) を分離する方法については例を参照。|
|@virtual|サポートされないシノニム。代わりに @abstract を使用。|
|@extends|サポートされないシノニム。代わりに @augments を使用。|
|@constructor|サポートされないシノニム。代わりに @class を使用。|
|@const|サポートされないシノニム。代わりに @constant を使用。|
|@defaultvalue|サポートされないシノニム。代わりに @default を使用。|
|@desc|サポートされないシノニム。代わりに @description を使用。|
|@host|サポートされないシノニム。代わりに @external を使用。|
|@fileoverview|サポートされないシノニム。代わりに @file を使用。|
|@overview|サポートされないシノニム。代わりに @file を使用。|
|@emits|サポートされないシノニム。代わりに @fires を使用。|
|@func|サポートされないシノニム。代わりに @function を使用。|
|@method|サポートされないシノニム。代わりに @function を使用。|
|@var|サポートされないシノニム。代わりに @member を使用。|
|@emits|サポートされないシノニム。代わりに @fires を使用。|
|@arg|サポートされないシノニム。代わりに @param を使用。|
|@argument|サポートされないシノニム。代わりに @param を使用。|
|@prop|サポートされないシノニム。代わりに @property を使用。|
|@return|サポートされないシノニム。代わりに @returns を使用。|
|@exception|サポートされないシノニム。代わりに @throws を使用。|

[原文](https://github.com/WordPress/wpcs-docs/blob/master/inline-documentation-standards/javascript.md)
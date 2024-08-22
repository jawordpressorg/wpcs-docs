<!-- 
# JavaScript Documentation Standards
 -->
# JavaScript ドキュメント規約

<!-- 
WordPress follows the [JSDoc 3 standard](http://jsdoc.app/) for inline JavaScript documentation.
 -->
WordPress は、インラインの JavaScript ドキュメント規約として「[JSDoc 3 Standard](http://jsdoc.app/)」に遵守します。

<!-- 
## What Should Be Documented
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
- Functions and class methods
- Objects
- Closures
- Object properties
- Requires
- Events
- File headers
 -->
- 関数、およびクラスのメソッド
- オブジェクト
- クロージャ
- オブジェクトプロパティ
- require
- イベント
- ファイルヘッダー

<!-- 
## Documenting Tips
 -->
## ドキュメントのヒント

<!-- 
### Language
 -->
### 文体

<!-- 
Short descriptions should be clear, simple, and brief. Document "what" and "when" - "why" should rarely need to be included. The "why" can go in the long description if needed. For example:

Functions and closures are _third-person singular_ elements, meaning _third-person singular verbs_ should be used to describe what each does.
 -->
「短い説明 (short description)」を書く場合には、明確でシンプルな、短い文を心がけてください。「いつ」「何を」実行するのかをドキュメントしてください。「なぜ」を含める必要性はほとんどないはずです。 どうしても「なぜ」が必要であれば「長い説明 (long description)」に記述してください。

関数やクロージャは「三人称単数」の要素です。説明を記述する場合も「三人称単数の動詞」を使用してください。

<!-- 
[tip]
Need help remembering how to conjugate for third-person singular verbs? Imagine prefixing the function, hook, class, or method summary with "It":

- _Good_: "(It) Does something."
- _Bad:_ "(It) Do something."

[/tip]
 -->
ヒント: 三人称単数の動詞の活用に悩む場合は、関数、フック、クラス、メソッドの説明を書く場合、先頭に「It」をつけて考えてください。
- 正: “(It) Does something.”
- 誤: “(It) Do something.”

<!-- 
**Functions**: What does the function do?
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

- _Good_: Handles a click on X element.
- _Bad_: Included for back-compat for X element.

**`@since`**: The recommended tool to use when searching for the version something was added to WordPress is [`svn blame`](https://make.wordpress.org/core/handbook/svn/code-history/#using-subversion-annotate).

If, after using these tools, the version number cannot be determined, use `@since Unknown`.

**Code Refactoring**: Do not refactor code in the file when changes to the documentation.
 -->
@since: WordPress に追加されたバージョン番号等を調べる場合は、ツール「[svn blame](https://make.wordpress.org/core/handbook/svn/code-history/#using-subversion-annotate)」の使用を推奨します。

ツールを使用してもバージョン番号を特定できない場合は、「@since Unknown」を使用してください。

**コードリファクタリング**: ドキュメントを編集する際に、ファイル内のコードはリファクタリングしないでください。

<!-- 
### Grammar
 -->
### 文法

<!-- 
Descriptive elements should be written as complete sentences. The one exception to this standard is file header summaries, which are intended as file "titles" more than sentences.

The serial (Oxford) comma should be used when listing elements in summaries, descriptions, and parameter or return descriptions.
 -->
説明文の要素は完全な文として記述してください。例外はファイルヘッダーの 要約 (summary) です。この要約は文章ではなく「タイトル」を意図しているためです。

要約、説明 (description)、Parameter や Return の説明内で要素を並べる際には serial comma (Oxford comma) を使用してください。(例: A, B and C)

<!-- 
## Formatting Guidelines
 -->
## フォーマットガイドライン

<!-- 
The following guidelines should be followed to ensure that the content of the doc blocks can be parsed properly for inclusion in the code reference.
 -->
次のガイドラインに従うことで DocBlock の内容が、コードリファレンス用に正しくパースされます。

<!-- 
**Short descriptions**:
 -->
**短い説明 (Short description):**

<!-- 
Short descriptions should be a single sentence and contain no markup of any kind. If the description refers to an HTML element or tag, then it should be written as "link tag", not "&lt;a&gt;". For example: "Fires when printing the link tag in the header".
 -->
「短い説明」は単一の文で書き、マークアップしないでください。説明が HTML 要素やタグを参照する場合は、「&lt;a&gt;」ではなく、「link タグ」のように記述してください。例: “Fires when printing the link tag in the header”。

<!-- 
**Long descriptions**:
 -->
**長い説明 (Long description):**

<!-- 
Markdown can be used, if needed, in a long description.
 -->
「長い説明」では、必要であればマークダウンを使用できます。

<!-- 
**`@param` and `@return` tags**:
 -->
**@param および @return タグ:**

<!-- 
No HTML or markdown is permitted in the descriptions for these tags. HTML elements and tags should be written as "audio element" or "link tag".
 -->
これらのタグの説明では HTML もマークダウンも許されません。HTML 要素やタグは「audio 要素」や「link タグ」のように記述してください。

<!-- 
### Line wrapping
 -->
### 行の折り返し

<!-- 
DocBlock text should wrap to the next line after 80 characters of text. If the DocBlock itself is indented on the left 20 character positions, the wrap could occur at position 100, but should not extend beyond a total of 120 characters wide.
 -->
DocBlock のテキストは80文字分で次の行に折り返してください。例えば DocBlock が20文字分インデントしている場合には、100文字目の位置で折り返します。ただし120文字目以上は超えないでください。

<!-- 
### Aligning comments
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
## Functions
 -->
## 関数

<!-- 
Functions should be formatted as follows:
 -->
関数は次のようにフォーマットしてください。

<!-- 
- **Summary**: A brief, one line explanation of the purpose of the function. Use a period at the end.
- **Description**: A supplement to the summary, providing a more detailed description. Use a period at the end.
- **`@deprecated x.x.x`**: Only use for deprecated functions, and provide the version the function was deprecated which should always be 3-digit (e.g. `@deprecated 3.6.0`), and the function to use instead.
- **`@since x.x.x`**: Should be 3-digit for initial introduction (e.g. `@since 3.6.0`). If significant changes are made, additional `@since` tags, versions, and descriptions should be added to serve as a changelog.
- **`@access`**: Only use for functions if private. If the function is private, it is intended for internal use only, and there will be no documentation for it in the code reference.
- **`@class`**: Use for class constructors.
- **`@augments`**: For class constructors, list direct parents.
- **`@mixes`**: List mixins that are mixed into the object.
- **`@alias`**: If this function is first assigned to a temporary variable this allows you to change the name it's documented under.
- **`@memberof`**: Namespace that this function is contained within if JSDoc is unable to resolve this automatically.
- **`@static`**: For classes, used to mark that a function is a static method on the class constructor.
- **`@see`**: A function or class relied on.
- **`@link`**: URL that provides more information.
- **`@fires`**: Event fired by the function. Events tied to a specific class should list the class name.
- **`@listens`**: Events this function listens for. An event must be prefixed with the event namespace. Events tied to a specific class should list the class name.
- **`@global`**: Marks this function as a global function to be included in the global namespace.
- **`@param`**: Give a brief description of the variable; denote particulars (e.g. if the variable is optional, its default) with [JSDoc `@param` syntax](http://jsdoc.app/tags-param.html). Use a period at the end.
- **`@yield`**: For [generator functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*), a description of the values expected to be yielded from this function. As with other descriptions, include a period at the end.
- **`@return`**: Note the period after the description.
 -->
- **要約:** 関数の目的を説明する簡潔な単一の文。末尾はピリオド。
- **説明:** 要約を補足する詳細な説明。文の末尾はピリオド。
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
- **@param:** 変数の簡単な説明。[JSDoc @param 構文](http://jsdoc.app/tags-param.html)を使用して、例えば、変数がオプションなら、そのデフォルト値などの事項を記述する。最後はピリオド。
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
## Backbone classes
 -->
## Backbone クラス

<!-- 
Backbone's `extend` calls should be formatted as follows:
 -->
Backbone の `extend` 呼び出しは次のようにフォーマットしてください。

<!-- 
- **`@lends`** This tag will allow JSDoc to recognize the `extend` function from Backbone as a class definition. This should be placed right before the Object that contains the class definition.
 -->
- **@lends** このタグは JSDoc に Backbone からの `extend` 関数をクラス定義として認識させます。クラス定義を含む Object の直前に置いてください。

<!-- 
Backbone's `initialize` functions should be formatted as follows:
 -->
Backbone の `initialize` 関数は次のようにフォーマットしてください。

<!-- 
- **Summary**: A brief, one line explanation of the purpose of the function. Use a period at the end.
- **Description**: A supplement to the summary, providing a more detailed description. Use a period at the end.
- **`@deprecated x.x.x`**: Only use for deprecated classes, and provide the version the class was deprecated which should always be 3-digit (e.g. `@deprecated 3.6.0`), and the class to use instead.
- **`@since x.x.x`**:</strong> Should be 3-digit for initial introduction (e.g. `@since 3.6.0`). If significant changes are made, additional `@since` tags, versions, and descriptions should be added to serve as a changelog.
- **`@constructs`**: Marks this function as the constructor of this class.
- **`@augments`**: List direct parents.
- **`@mixes`**: List mixins that are mixed into the class.
- **`@requires`**: Lists modules that this class requires. Multiple `@requires` tags can be used.
- **`@alias`**: If this class is first assigned to a temporary variable this allows you to change the name it's documented under.
- **`@memberof`**: Namespace that this class is contained within if JSDoc is unable to resolve this automatically.
- **`@static`**: For classes, used to mark that a function is a static method on the class constructor.
- **`@see`**: A function or class relied on.
- **`@link`**: URL that provides more information.
- **`@fires`**: Event fired by the constructor. Should list the class name.
- **`@param`**: Document the arguments passed to the constructor even if not explicitly listed in `initialize`. Use a period at the end.
    - Backbone Models are passed `attributes` and `options` parameters.
    - Backbone Views are passed an `options` parameter.
 -->
- **要約:** 関数の目的を説明する簡潔な単一の文。末尾はピリオド。
- **説明:** 要約を補足する詳細な説明。文の末尾はピリオド。
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
	 * @param {type}   options.key One of the model's options.
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
	 * @param {type}   options.key モデルのオプションの1つ。
	 */
	initialize: function() {
		// 何かを実行する。
	}
} );
```

<!-- 
If a Backbone class does not have an initialize function it should be documented by using `@inheritDoc` as follows:
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
> Note: This currently doesn't provide the expected functionality due to a bug with JSDoc's inheritDoc tag. See [JSDocs3 issue 1012](https://github.com/jsdoc3/jsdoc/issues/1012).
 -->
> 注意: 現在、JSDoc の inheritDoc タグのバグのため、期待どおりに機能しません。こちらの [issue](https://github.com/jsdoc3/jsdoc/issues/1012) を参照してください。

<!-- 
## Local functions
 -->
## ローカル関数

<!-- 
At times functions will be assigned to a local variable before being assigned as a class member.
Such functions should be marked as inner functions of the namespace that uses them using `~`.
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
## Local ancestors
 -->
<h2>ローカルの ancestor</h2>

<!-- 
At times classes will have Ancestors that are only assigned to a local variable. Such classes should be assigned to the namespace their children are and be made inner classes using `~`.
 -->
クラスは、ローカル変数にしか割り当てられない ancestor (先祖) を持つ場合があります。このようなクラスは、その子クラスの名前空間に割り当て、<code>~</code> を使用して内部クラスにする必要があります。

<!-- 
## Class members
 -->
<h2>クラスメンバー</h2>

<!-- 
Class members should be formatted as follows:
 -->
クラスメンバーは次のようにフォーマットしてください。

<!-- 
- **Short description**: Use a period at the end.
- **`@since x.x.x`**: Should be 3-digit for initial introduction (e.g. `@since 3.6.0`). If significant changes are made, additional `@since` tags, versions, and descriptions should be added to serve as a changelog.
- **`@access`**: If the members is private, protected or public. Private members are intended for internal use only.
- **`@type`**: List the type of the class member.
- **`@property`** List all properties this object has in case it's an Object. Use a period at the end.
- **`@member`**: Optionally use this to override JSDoc's member detection in place of `@type` to force a class member.
- **`@memberof`**: Optionally use this to override what class this is a member of.
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
## Namespaces
 -->
<h2>名前空間</h2>
<!-- 
Namespaces should be formatted as follows:
 -->
名前空間は次のようにフォーマットしてください。

<!-- 
- **Short description**: Use a period at the end.
- **`@namespace`**: Marks this symbol as a namespace, optionally provide a name as an override.
- **`@since x.x.x`**: Should be 3-digit for initial introduction (e.g. `@since 3.6.0`). If significant changes are made, additional `@since` tags, versions, and descriptions should be added to serve as a changelog.
- **`@memberof`**: Namespace that this namespace is contained in.
- **`@property`**: Properties that this namespace exposes. Use a period at the end.
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
## Inline Comments
 -->
## インラインコメント

<!-- 
Inline comments inside methods and functions should be formatted as follows:
 -->
メソッドや関数のインラインコメントは次のようにフォーマットしてください。

<!-- 
### Single line comments
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
### Multi-line comments
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
**Important note:** Multi-line comments must not begin with `/**` (double asterisk). Use `/*` (single asterisk) instead.
 -->
**重要な注意:** 複数行のコメントを `/**` (2つのアスタリスク) で始めないでください。代わりに `/*` (1つのアスタリスク) を使用してください。

<!-- 
## File Headers
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
## Supported JSDoc Tags
 -->
## サポートされる JSDoc タグ

<!-- 

| Tag            | Description                                                                                  |
|----------------|----------------------------------------------------------------------------------------------|
| `@abstract`    | This method can be implemented (or overridden) by the inheritor.                             |
| `@access`      | Specify the access level of this member (private, public, or protected).                     |
| `@alias`       | Treat a member as if it had a different name.                                                |
| `@augments`    | This class inherits from a parent class.                                                     |
| `@author`      | Identify the author of an item.                                                              |
| `@borrows`     | This object uses something from another object.                                              |
| `@callback`    | Document a callback function.                                                                |
| `@class`       | This function is a class constructor.                                                        |
| `@classdesc`   | Use the following text to describe the entire class.                                         |
| `@constant`    | Document an object as a constant.                                                            |
| `@constructs`  | This function member will be the constructor for the previous class.                         |
| `@copyright`   | Document some copyright information.                                                         |
| `@default`     | Document the default value.                                                                  |
| `@deprecated`  | Document that this is no longer the preferred way.                                           |
| `@description` | Describe a symbol.                                                                           |
| `@enum`        | Document a collection of related properties.                                                 |
| `@event`       | Document an event.                                                                           |
| `@example`     | Provide an example of how to use a documented item.                                          |
| `@exports`     | Identify the member that is exported by a JavaScript module.                                 |
| `@external`    | Document an external class/namespace/module.                                                 |
| `@file`        | Describe a file.                                                                             |
| `@fires`       | Describe the events this method may fire.                                                    |
| `@function`    | Describe a function or method.                                                               |
| `@global`      | Document a global object.                                                                    |
| `@ignore`      | [todo] Remove this from the final output.                                                    |
| `@inner`       | Document an inner object.                                                                    |
| `@instance`    | Document an instance member.                                                                 |
| `@kind`        | What kind of symbol is this?                                                                 |
| `@lends`       | Document properties on an object literal as if they belonged to a symbol with a given name.  |
| `@license`     | [todo] Document the software license that applies to this code.                              |
| `@link`        | Inline tag - create a link.                                                                  |
| `@member`      | Document a member.                                                                           |
| `@memberof`    | This symbol belongs to a parent symbol.                                                      |
| `@mixes`       | This object mixes in all the members from another object.                                    |
| `@mixin`       | Document a mixin object.                                                                     |
| `@module`      | Document a JavaScript module.                                                                |
| `@name`        | Document the name of an object.                                                              |
| `@namespace`   | Document a namespace object.                                                                 |
| `@param`       | Document the parameter to a function.                                                        |
| `@private`     | This symbol is meant to be private.                                                          |
| `@property`    | Document a property of an object.                                                            |
| `@protected`   | This member is meant to be protected.                                                        |
| `@public`      | This symbol is meant to be public.                                                           |
| `@readonly`    | This symbol is meant to be read-only.                                                        |
| `@requires`    | This file requires a JavaScript module.                                                      |
| `@return`      | Document the return value of a function.                                                     |
| `@see`         | Refer to some other documentation for more information.                                      |
| `@since`       | Documents the version at which the function was added, or when significant changes are made. |
| `@static`      | Document a static member.                                                                    |
| `@this`        | What does the 'this' keyword refer to here?                                                  |
| `@throws`      | Describe what errors could be thrown.                                                        |
| `@todo`        | Document tasks to be completed.                                                              |
| `@tutorial`    | Insert a link to an included tutorial file.                                                  |
| `@type`        | Document the type of an object.                                                              |
| `@typedef`     | Document a custom type.                                                                      |
| `@variation`   | Distinguish different objects with the same name.                                            |
| `@version`     | Documents the version number of an item.                                                     |
| `@yield`       | Document the yielded values of a generator function.                                         |
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
## Unsupported JSDoc Tags
 -->
## サポートされない JSDoc タグ

<!-- 

| Tag             | Why it's not supported                                                                        |
|-----------------|-----------------------------------------------------------------------------------------------|
| `@summary`      | Should not be used. See the example of how to separate a summary from the full description.   |
| `@virtual`      | An unsupported synonym. Use `@abstract` instead.                                              |
| `@extends`      | An unsupported synonym. Use `@augments` instead.                                              |
| `@constructor`  | An unsupported synonym. Use `@class` instead.                                                 |
| `@const`        | An unsupported synonym. Use `@constant` instead.                                              |
| `@defaultvalue` | An unsupported synonym. Use `@default` instead.                                               |
| `@desc`         | An unsupported synonym. Use `@description` instead.                                           |
| `@host`         | An unsupported synonym. Use `@external` instead.                                              |
| `@fileoverview` | An unsupported synonym. Use `@file` instead.                                                  |
| `@overview`     | An unsupported synonym. Use `@file` instead.                                                  |
| `@emits`        | An unsupported synonym. Use `@fires` instead.                                                 |
| `@func`         | An unsupported synonym. Use `@function` instead.                                              |
| `@method`       | An unsupported synonym. Use `@function` instead.                                              |
| `@var`          | An unsupported synonym. Use `@member` instead.                                                |
| `@emits`        | An unsupported synonym. Use `@fires` instead.                                                 |
| `@arg`          | An unsupported synonym. Use `@param` instead.                                                 |
| `@argument`     | An unsupported synonym. Use `@param` instead.                                                 |
| `@prop`         | An unsupported synonym. Use `@property` instead.                                              |
| `@returns`      | An unsupported synonym. Use `@return` instead.                                                |
| `@exception`    | An unsupported synonym. Use `@throws` instead.                                                |
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

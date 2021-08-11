<!-- 
# HTML Coding Standards
 -->
# HTML コーディング規約

## HTML

<!-- 
### Validation
 -->
### 検証

<!-- 
All HTML pages should be verified against [the W3C validator](https://validator.w3.org/) to ensure that the markup is well formed. This in and of itself is not directly indicative of good code, but it helps to weed out problems that are able to be tested via automation. It is no substitute for manual code review. (For other validators, see [HTML Validation](https://codex.wordpress.org/Validating_a_Website#HTML_-_Validation) in the Codex.)
 -->
すべての HTML ページは「[W3C Validator](https://validator.w3.org/)」を使用してマークアップが整形式であることを検証してください。このツールだけで HTML が正しいコードであるとは言い切れませんが、自動化テストで見つかる程度の問題は取り除くことができます。なお目視によるコードレビューは依然必要ですので注意してください。他の検証ツールについては「[HTML Validation](https://codex.wordpress.org/Validating_a_Website#HTML_-_Validation)」を参照してください。

<!-- 
### Self-closing Elements
 -->
### 終了を含む要素

<!-- 
All tags must be properly closed. For tags that can wrap nodes such as text or other elements, termination is a trivial enough task. For tags that are self-closing, the forward slash should have exactly one space preceding it:
 -->
すべてのタグは正しく閉じる必要があります。テキストや他の要素を囲むタグであれば、終了タグを置くことは自明の作業でしょう。一方、自身が終了タグを含むタグの場合、スラッシュの前に1個のスペースを挿入してください。

```html
<br />
```
<!-- 
rather than the compact but incorrect:
 -->
スペースのない書き方は誤りです。

```html
<br/>
```
<!-- 
The W3C specifies that a single space should precede the self-closing slash ([source](https://w3.org/TR/xhtml1/#C_2)).
 -->
W3C でも自身を閉じるスラッシュの前に単一のスペースを規定しています ([原典](https://w3.org/TR/xhtml1/#C_2))。

<!-- 
### Attributes and Tags
 -->
### 属性とタグ

<!-- 
All tags and attributes must be written in lowercase. Additionally, attribute values should be lowercase when the purpose of the text therein is only to be interpreted by machines. For instances in which the data needs to be human readable, proper title capitalization should be followed.
 -->
すべてのタグと属性は小文字で書いてください。また文字列の属性値も、コンピューター内のみで処理される場合は小文字にしてください。ユーザーが目にするデータ等はその限りでなく、通常どおり先頭を大文字にするなど適切に記述してください。

<!-- 
For machines:
 -->
コンピューター用

```html
<meta http-equiv="content-type" content="text/html; charset=utf-8" />
```

<!-- 
For humans:
 -->
人間用
```html
<a href="http://example.com/" title="Description Here">Example.com</a>
```

<!-- 
### Quotes
 -->
### クオート

<!-- 
According to the W3C specifications for XHTML, all attributes must have a value, and must use double- or single-quotes ([source](https://www.w3.org/TR/xhtml1/#h-4.4)). The following are examples of proper and improper usage of quotes and attribute/value pairs.
 -->
W3C の XHTML 規約ではすべての属性には値が必要で、ダブルクオート、またはシングルクオートで囲む必要があります ([原典](https://www.w3.org/TR/xhtml1/#h-4.4)))。以下はクオート、および、属性と値のペアの正しい用例と誤った用例です。

<!-- 
Correct:
 -->
正しい:

```html
<input type="text" name="email" disabled="disabled" />
<input type='text' name='email' disabled='disabled' />
```
<!-- 
Incorrect:
 -->
間違い:

```html
<input type=text name=email disabled>
```

<!-- 
In HTML, attributes do not all have to have values, and attribute values do not always have to be quoted. While all of the examples above are valid HTML, _failing to quote attributes can lead to security vulnerabilities_. Always quote attributes.
 -->
HTML ではすべての属性が値を持つとは限らず、また属性値をクオートで囲む必要もありません。上のすべての例は妥当な HTML ですが、クオートで属性を囲まなければセキュリティ上の脆弱性となります。常に属性はクオートで囲んでください。

<!-- 
### Indentation
 -->
### インデント

<!-- 
As with PHP, HTML indentation should always reflect logical structure. Use tabs and not spaces.

When mixing PHP and HTML together, indent PHP blocks to match the surrounding HTML code. Closing PHP blocks should match the same indentation level as the opening block.
 -->
PHP と同様、HTML のインデントでも常に論理的な構造を反映してください。本物のタブを使用し、スペースは使用しないでください。

PHP と HTML を一緒に書く場合、PHP ブロックは周囲の HTML コードと一致するようにインデントしてください。PHP ブロックの終了レベルは、開始レベルに一致する必要があります。

<!-- 
Correct:
 -->
正しい:

```php
<?php if ( ! have_posts() ) : ?>
<div id="post-1" class="post">
	<h1 class="entry-title">Not Found</h1>
	<div class="entry-content">
		<p>Apologies, but no results were found.</p>
		<?php get_search_form(); ?>
	</div>
</div>
<?php endif; ?>
```

<!-- 
Incorrect:
 -->
間違い:

```php
<?php if ( ! have_posts() ) : ?>
<div id="post-0" class="post error404 not-found">
<h1 class="entry-title">Not Found</h1>
<div class="entry-content">
<p>Apologies, but no results were found.</p>
<?php get_search_form(); ?>
</div>
</div>
<?php endif; ?>
```

<!-- 
## Credits
 -->
## クレジット

<!-- 
- HTML code standards adapted from [Fellowship Tech Code Standards](https://developer.fellowshipone.com/patterns/code.php) ([CC license](https://creativecommons.org/licenses/by-nc-sa/3.0/http://creativecommons.org/licenses/by-nc-sa/3.0/)).
 -->
- HTML コーディング規約は [Fellowship Tech Code Standards](https://developer.fellowshipone.com/patterns/code.php) ([CC license](https://creativecommons.org/licenses/by-nc-sa/3.0/http://creativecommons.org/licenses/by-nc-sa/3.0/)) を基にしています。


[原文](https://github.com/WordPress/wpcs-docs/blob/master/wordpress-coding-standards/html.md) / [日本語訳](https://github.com/jawordpressorg/wpcs-docs/blob/master/wordpress-coding-standards/html.md)

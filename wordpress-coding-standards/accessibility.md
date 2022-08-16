<!-- 
# Accessibility Coding Standards
 -->
# アクセシビリティコーディング規約

<!--
Code integrated into the WordPress ecosystem - including WordPress core, WordPress.org websites, and official plugins, is expected to conform to the Web Content Accessibility Guidelines (WCAG), version 2.1, at level AA.
-->
WordPressのエコシステム (WordPressコア、WordPress.org サイト、公式プラグインを含む) に統合されるコードは、Web Content Accessibility Guidelines (WCAG) version 2.1 レベル AA に適合することが求められます。

<!--
New or updated interfaces are encouraged to incorporate the Authoring Tool Accessibility Guidelines (ATAG) 2.0. The most significant way that ATAG 2.0 guidelines can be incorporated is by emphasizing choices that help people make more accessible content: encouraging alternative text, captions, and semantic structures, for example.
-->
新規または更新するインターフェースは、Authoring Tool Accessibility Guidelines (ATAG) 2.0を組み込むことが推奨されます。ATAG 2.0ガイドラインを組み込む最も重要な意味は、よりアクセシブルなコンテンツ作成を支援するオプションを強調することです。例えば代替テキスト、キャプション、セマンティクス構造の推奨などです。

<!--
Official information about web accessibility standards can be divided into two groups: "normative" and "informative" documents. Only the guidelines themselves are normative, and establish the actual requirements for conforming to WCAG 2.1. Other documents should be considered to be informational, and offer help in interpreting the guidelines, but are not definitive.
-->
ウェブアクセシビリティ規格に関する公式情報は、2つのグループに分けられます。「規範的 (normative)」な文書と「情報的 (informative)」な文書です。ガイドライン自体は規範的であり、WCAG 2.1に準拠するための実際の要件を定めています。その他の文書は情報提供であり、ガイドラインの解釈の助けとなりますが、決定的ではありません。

<!--
The WordPress A11y team is in the process of developing a library of recommended accessibility patterns to help describe the WordPress recommended way to accomplish a variety of interfaces. These may not be the only reasonable way to create an accessible example of the pattern, but are preferred for the sake of consistency across WordPress.
-->
WordPress アクセシビリティチームは、推奨アクセシビリティパターンのライブラリを開発しています。ライブラリは、さまざまなインターフェースを実現する WordPress 推奨方法の説明を支援します。これらは、パターンのアクセシブルな例を作成する、唯一の合理的な方法ではないかもしれませんが、WordPress 全体の一貫性のために推奨されています。

<!--
Normative Documents:
-->
基本的な文書:

<!-- 
- [W3C WCAG 2.1](https://www.w3.org/TR/WCAG21)
- [W3C ATAG 2.0](https://www.w3.org/TR/ATAG20/)
- [W3C WAI ARIA 1.1](https://www.w3.org/TR/wai-aria/)
 -->
- [W3C WCAG 2.1](https://www.w3.org/TR/WCAG21) / [日本語訳](https://waic.jp/docs/WCAG21/)
- [W3C ATAG 2.0](https://www.w3.org/TR/ATAG20/) / [日本語訳](https://waic.jp/docs/ATAG20/)
- [W3C WAI ARIA 1.1](https://www.w3.org/TR/wai-aria/) / [日本語訳](https://momdo.github.io/wai-aria-1.1/) 

訳注: この文書の翻訳では、[ウェブアクセシビリティ基盤委員会](https://waic.jp/)の翻訳を基にしています。

<!--
Informative Documents:
-->
情報的な文書:

<!-- 
- [W3C Understanding WCAG 2.1](https://www.w3.org/WAI/WCAG21/Understanding/)
- [W3C Using ARIA](https://www.w3.org/TR/using-aria/)
- [W3C WAI-ARIA Authoring Practices 1.1 (accessible design patterns)](https://www.w3.org/TR/wai-aria-practices-1.1/)
- [W3C Introduction to ATAG](https://www.w3.org/WAI/standards-guidelines/atag)
 -->
- [W3C Understanding WCAG 2.1](https://www.w3.org/WAI/WCAG21/Understanding/) / [日本語訳](https://waic.jp/docs/WCAG21/Understanding/)
- [W3C Using ARIA](https://www.w3.org/TR/using-aria/) 
- [W3C WAI-ARIA Authoring Practices 1.1 (accessible design patterns)](https://www.w3.org/TR/wai-aria-practices-1.1/) / [日本語訳](https://waic.jp/docs/2019/NOTE-wai-aria-practices-1.1-20190207/) 
- [W3C Introduction to ATAG](https://www.w3.org/WAI/standards-guidelines/atag)

<!--
## About WCAG A, AA, and AAA Conformance Levels

The WordPress commitment is to conform to all WCAG 2.1 Level A and Level AA guidelines. Conformance to level AAA success criteria is encouraged where relevant, as is exceeding the accessibility of any of these guidelines.
-->
## WCAG A, AA, AAA 適合レベル

WordPress のコミットメントは、すべての WCAG 2.1レベル A およびレベル AA ガイドラインへの適合です。レベル AAA 達成基準への適合は、これらのガイドラインのアクセシビリティを超えるため、関連する場合に推奨されます。

<!--
**Level A** success criteria address concerns considered to be accessibility barriers on a very wide scale that will prevent many people from accessing the site and the minimum set of accomplished goals required for the majority of web-based interfaces.
-->
**レベル A** 達成基準は、多くの人がサイトにアクセスできないような、非常に広い範囲でのアクセシビリティバリアと考えられる懸念事項への対処と、大多数のウェブベースのインターフェースに求められる最低限の達成目標です。

<!--
**Level AA** success criteria address concerns that are generally somewhat more complicated to address and may impact smaller groups of people, but are still common needs with broad reach.
-->
**レベル AA** 達成基準は、一般的に対処がやや複雑で、より少数の人々にしか影響を与えないかもしれないが、それでも 共通のニーズである懸念事項を扱います。

<!--
**Level AAA** success criteria are mostly targeted at very specific needs and may be quite difficult to implement effectively.
-->
**レベル AAA** 達成基準は、ほとんどが非常に特殊なニーズを対象としており、効果的な実装はかなり難しいと思われます。

<!--
[W3C Quick Reference to WCAG 2.1 Level A and Level AA Requirements](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.1&currentsidebar=%23col_overview&levels=aaa)
-->
[W3C Quick Reference to WCAG 2.1 Level A and Level AA Requirements](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.1&currentsidebar=%23col_overview&levels=aaa) / [WCAG 2.0 版の日本語訳](https://waic.jp/docs/WCAG20/quickref/)

<!--
## Applying WCAG Conformance Levels

WCAG 2.1 consists of 4 layers:

- Principles
- Guidance
- Success criteria
- Sufficient and advisory techniques
-->
## WCAG 適合レベルの適用 

WCAG 2.1 は4つのレイヤーからなります。
- 原則 (Principles)
- ガイダンス (Guidance) (訳注: 日本語訳では「ガイドライン」)
- 達成基準 (Success criteria)
- 十分な達成方法及び参考達成方法 (Sufficient and advisory techniques)

<!--
### Principles

When applying WCAG 2.1, the guidance and success criteria are organized around 4 principles. These principles place emphasis on how people interact with content and must be:

- **Perceivable** - interacting with the content using the medium that they are familiar with. For example, providing text alternatives for those who are blind.
- **Operable** - finding and using content is accessible. For example, being able to use a keyboard or a screen reader.
- **Understandable** - content uses clear language and is understandable. For example, use meaningful labels, explain all abbreviations.
- **Robust** - content can be interpreted in a range of ways. For example, assistive technologies are able to interpret and parse content.
-->
### 原則
WCAG2.1を適用する場合、ガイダンスと達成基準は4つの原則を中心に構成されます。これらの原則は、人々がコンテンツとどのように相互作用するかに重点を置いています。以下でなければなりません。

- **知覚可能 (Perceivable)** - 親しんだメディアを使ったコンテンツと対話できること。例えば、目の不自由な人のために代替テキストを提供すること。

- **操作可能 (Operable)** - コンテンツの検索、使用がアクセシブルであること。例えば、キーボードやスクリーンリーダーを使用できること。

- **理解可能 (Understandable)** - コンテンツは明確な言語を使用し、理解可能であること。例えば、意味のあるラベルを使用し、すべての略語を説明すること。

- **堅牢 (Robust)** - コンテンツは、さまざまな方法で解釈できること。たとえば、支援技術は、コンテンツを解釈し、解析できること。

<!--
### Guidance

Each principle is supported by a list of guidelines to ensure that content is more accessible and presentable across the different devices that meet a user’s disability. The guidelines are listed below, the full detail can be found in the WCAG 2.1.
-->
### ガイダンス

各原則は、ユーザーの障害に応じたさまざまなデバイスでコンテンツがよりアクセスしやすく、見やすくなるように、ガイドラインのリストでサポートされています。ガイドラインは以下の通りです。詳細については、WCAG 2.1を参照してください。

<!--
#### Principle: Perceivable

**Guideline 1.1 Text Alternatives**
Provide text alternatives for any non-text content so that it can be changed into other forms people need, such as large print, braille, speech, symbols or simpler language.
-->
#### 原則: 知覚可能

**ガイドライン 1.1 テキストによる代替**
すべての非テキストコンテンツには、拡大印刷、点字、音声、シンボル、平易な言葉などの利用者が必要とする形式に変換できるように、テキストによる代替を提供すること。

<!--
**Guideline 1.2 Time-based Media**
Provide alternatives for time-based media. For example, include captions and transcripts for audio or video clips.
-->
**ガイドライン 1.2 時間依存メディア**
時間依存メディアには代替を提供すること。例えば、音声や映像にはキャプンションやトランスクリプトを含めること。

<!--
**Guideline 1.3 Adaptable**
Create content that can be presented in different ways (for example simpler layout) without losing information or structure.
-->
**ガイドライン 1.3 適応可能**
情報、及び構造を損なうことなく、様々な方法 (例えば、よりシンプルなレイアウト) で提供できるようにコンテンツを制作すること。

<!--
**Guideline 1.4 Distinguishable**
Make it easier for users to see and hear content including separating foreground from background.
-->
**ガイドライン 1.4 判別可能**
コンテンツを、利用者にとって見やすく、聞きやすいものにすること。これには、前景と背景を区別することも含む。

<!--
#### Principle: Operable

**Guideline 2.1 Keyboard Accessible**
Make all functionality available from a keyboard.
-->
#### 原則: 操作可能
**ガイドライン 2.1 キーボード操作可能**
すべての機能をキーボードから利用できるようにすること。

<!--
**Guideline 2.2 Enough Time**
Provide users enough time to read and use content.
-->
**ガイドライン 2.2 十分な時間**
利用者がコンテンツを読み、使用するために十分な時間を提供すること。

<!--
**Guideline 2.3 Seizures and Physical Reactions**
Do not design content in a way that is known to cause seizures or physical reactions.
-->
**ガイドライン 2.3 発作と身体的反応**
発作や身体的反応を引き起こすようなコンテンツを設計しないこと。

<!--
**Guideline 2.4 Navigable**
Provide ways to help users navigate, find content, and determine where they are.
-->
**ガイドライン 2.4 ナビゲーション可能**
利用者がナビゲートしたり、コンテンツを探し出したり、現在位置を確認したりすることを手助けする手段を提供すること。

<!--
**Guideline 2.5 Input Modalities**
Make it easier for users to operate functionality through various inputs beyond keyboard.
-->
**ガイドライン 2.5 入力モダリティ**
利用者がキーボード以外の様々な入力を通じて機能を操作しやすくすること。

<!--
#### Principle: Understandable

**Guideline 3.1 Readable**
Make text content readable and understandable.
-->
#### 原則: 理解可能
**ガイドライン 3.1 読みやすさ**
テキストのコンテンツを読みやすく理解可能にすること。

<!--
**Guideline 3.2 Predictable**
Make Web pages appear and operate in predictable ways.
-->
**ガイドライン 3.2 予測可能**
ウェブページの表示や挙動を予測可能にすること。

<!--
**Guideline 3.3 Input Assistance**
Help users avoid and correct mistakes.
-->
**ガイドライン 3.3 入力支援**
利用者の間違いを防ぎ、修正を支援すること。

<!--
#### Principle: Robust

**Guideline 4.1 Compatible**
Maximize compatibility with current and future user agents, including assistive technologies.
-->
#### 原則: 堅牢
**ガイドライン 4.1 互換性**
現在及び将来の、支援技術を含むユーザエージェントとの互換性を最大化すること。

<!--
### Success Criteria

Each guidance has a [specific list requirements that must be met for your content to be accessible](https://www.w3.org/WAI/WCAG21/quickref/). These tests can be carried out using automated software and or human testers. You can find more information on how to meet the success criteria in [Understanding Levels of Conformance](https://www.w3.org/WAI/WCAG21/Understanding/conformance#levels). Whilst these criteria are important, usability testing is still important and should be carried out alongside any accessibility testing.
-->
### 達成基準

各ガイダンスには、[コンテンツがアクセス可能であるために満たさなければならない具体的な要求リスト](https://www.w3.org/WAI/WCAG21/quickref/) / [WCAG 2.0 版の日本語訳](https://waic.jp/docs/WCAG20/quickref/) があります。これらのテストは、自動化されたソフトウェアや人間のテスタを使って実施できます。達成基準を満たす方法の詳細については、「[Understanding Levels of Conformance](https://www.w3.org/WAI/WCAG21/Understanding/conformance#levels)」 / [日本語訳](https://waic.jp/docs/UNDERSTANDING-WCAG20/conformance.html#uc-levels-head) を参照してください。これらの基準は重要ですが、ユーザビリティテストも依然として重要であり、アクセシビリティテストと並行して実施する必要があります。


<!--
### Techniques: Sufficient, Advisory, and Failures

Techniques (code examples, resources, and tests) for guidance and success criteria that can help in making content more accessible, are divided into three categories:

- Sufficient - required and help meet the success criteria
- Advisory - suggestions and go beyond what is required
- Failures - cause problems and fail to meet the success criteria

For more information on techniques, visit [Understanding Techniques for WCAG Success Criteria](https://www.w3.org/WAI/WCAG21/Understanding/understanding-techniques).
-->
### 達成方法集: 十分な達成方法、参考達成方法、失敗例

コンテンツをよりアクセシブルにするためのガイダンスと達成基準のための達成方法集 (Techniques) (コード例、リソース、テスト) は、3つのカテゴリーに分けられます。

- 十分な達成方法 (Sufficient) - 達成基準を満たすために必要であり、これを支援する
- 参考達成方法 (Advisory) - 提案であり、必要以上を求める
- 失敗例 (Failures) - 問題を引き起こし、達成基準の実現に失敗する

達成方法集の詳細については、[Understanding Techniques for WCAG Success Criteria](https://www.w3.org/WAI/WCAG21/Understanding/understanding-techniques) / [日本語](https://waic.jp/docs/WCAG21/Techniques/
) にアクセスしてください。

<!--
## Authoritative Resources

- [WebAIM: Web Accessibility In Mind](https://webaim.org/) (see Articles and Resources)
- [Government Digital Service](https://gds.blog.gov.uk)
- [Accessibility in government](https://accessibility.blog.gov.uk/)
- [Blog | TPG – The Accessibility Experts](https://developer.paciellogroup.com/blog/)
- [Web Accessibility Blog (Deque)](https://www.deque.com/blog/)
- [Tink - Léonie Watson](https://tink.uk) (Léonie Watson)
- [Adrian Roselli](https://adrianroselli.com)
- [Scott O'Hara](https://www.scottohara.me)
- [Joe Dolson](https://www.joedolson.com/blog)
- [Sarah Higley](https://sarahmhigley.com/)
- [Marco's Accessibility Blog](https://www.marcozehe.de/)
- [Karl Groves](https://karlgroves.com/)
- [Inclusive Components](https://inclusive-components.design) (Heydon Pickering)
- [Accessibility London (London, United Kingdom)](https://www.meetup.com/London-Accessibility-Meetup/) (London accessibility meetup: they live stream meetups on youtube)
- [24 Accessibility](https://www.24a11y.com/)
- [Mozilla Accessibility - Users first, no matter their abilities](https://blog.mozilla.org/accessibility/)
-->
## 信頼できるリソース

- [WebAIM: Web Accessibility In Mind](https://webaim.org/) (Articles と Resources を参照)
- [Government Digital Service](https://gds.blog.gov.uk)
- [Accessibility in government](https://accessibility.blog.gov.uk/) 
- [Blog | TPG – The Accessibility Experts](https://developer.paciellogroup.com/blog/)
- [Web Accessibility Blog (Deque)](https://www.deque.com/blog/)
- [Tink - Léonie Watson](https://tink.uk) (Léonie Watson)
- [Adrian Roselli](https://adrianroselli.com)
- [Scott O'Hara](https://www.scottohara.me)
- [Joe Dolson](https://www.joedolson.com/blog)
- [Sarah Higley](https://sarahmhigley.com/) 
- [Marco's Accessibility Blog](https://www.marcozehe.de/) 
- [Karl Groves](https://karlgroves.com/) 
- [Inclusive Components](https://inclusive-components.design) (Heydon Pickering)
- [Accessibility London (London, United Kingdom)](https://www.meetup.com/London-Accessibility-Meetup/) (London accessibility meetup: YouTube でライブストリームミートアップを実施している)
- [24 Accessibility](https://www.24a11y.com/)
- [Mozilla Accessibility - Users first, no matter their abilities](https://blog.mozilla.org/accessibility/)
- [ウェブアクセシビリティ基盤委員会](https://waic.jp/) ... 「ウェブアクセシビリティ基盤委員会（Web Accessibility Infrastructure Committee）は、日本におけるウェブアクセシビリティの公的規格であるJIS X 8341-3の理解と普及を促進するとともに、JIS X 8341-3を利用してウェブアクセシビリティを高めていくために必要な基盤を構築するために、さまざまな活動を行っています。」

<!--
### Technical and / or specific topics

- [Accessibility Support](https://a11ysupport.io/) (Will your code work with assistive technologies?)
- [Accessibility APIs: A Key To Web Accessibility](https://www.smashingmagazine.com/2015/03/web-accessibility-with-accessibility-api/) (by Léonie Watson)
- [How accessibility trees inform assistive tech](https://hacks.mozilla.org/2019/06/how-accessibility-trees-inform-assistive-tech/) (by Hidde de Vries)
- [What is this thing and what does it do?](https://www.youtube.com/watch?v=YLihNhn_MO4 ) (presentation by Karl Groves)
- [The Browser Accessibility Tree](https://developer.paciellogroup.com/blog/2015/01/the-browser-accessibility-tree/) (by Steve Faulkner)
- [Brief history of browser accessibility support](https://www.paciellogroup.com/blog/2011/10/brief-history-of-browser-accessibility-support/) (by Steve Faulkner)
- [ARIA Landmarks Example: General Principles](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/)
- [ARIA Landmarks Example: HTML Sectioning Elements](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/HTML5.html)
-->
### 技術や特定のトピック:

- [Accessibility Support](https://a11ysupport.io/) (コードが支援技術で動作するか?)
- [Accessibility APIs: A Key To Web Accessibility](https://www.smashingmagazine.com/2015/03/web-accessibility-with-accessibility-api/) (by Léonie Watson)  
- [How accessibility trees inform assistive tech](https://hacks.mozilla.org/2019/06/how-accessibility-trees-inform-assistive-tech/) (by Hidde de Vries) 
- [What is this thing and what does it do?](https://www.youtube.com/watch?v=YLihNhn_MO4 ) (by Karl Groves プレゼンテーション)
- [The Browser Accessibility Tree](https://developer.paciellogroup.com/blog/2015/01/the-browser-accessibility-tree/) (by Steve Faulkner)
- [Brief history of browser accessibility support](https://www.paciellogroup.com/blog/2011/10/brief-history-of-browser-accessibility-support/) (by Steve Faulkner) 
- [ARIA Landmarks Example: General Principles](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/)
- [ARIA Landmarks Example: HTML Sectioning Elements](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/HTML5.html) 

<!--
[原文](https://github.com/WordPress/wpcs-docs/blob/master/wordpress-coding-standards/accessibility.md) / [日本語訳](https://github.com/jawordpressorg/wpcs-docs/blob/master/wordpress-coding-standards/accessibility.md)
-->
[原文](https://github.com/WordPress/wpcs-docs/blob/master/wordpress-coding-standards/accessibility.md) / [日本語訳](https://github.com/jawordpressorg/wpcs-docs/blob/master/wordpress-coding-standards/accessibility.md)

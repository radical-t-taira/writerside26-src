# MyDocumentについて

<!--Writerside adds this topic when you create a new documentation project.
You can use it as a sandbox to play with Writerside features, and remove it from the TOC when you don't need it anymore.-->

## 新しいトピックを追加する
空のトピックを作成したり、開始に役立つ定型構造を含むさまざまな種類のコンテンツのテンプレートを選択したりできます。

![Create new topic options](new_topic_options.png){ width=290 }{border-effect=line}

## コンテンツを書く
Writersideは、MarkdownとXMLの2種類のマークアップをサポートしています。 
新しいヘルプ記事を作成するときは、2つのトピック タイプから選択できますが、これは単一の形式に固執する必要があるという意味ではありません。
Markdownでコンテンツを作成してセマンティック属性で拡張したり、XML要素全体を挿入したりできます。

## XMLを挿入する
たとえば、プロシージャを挿入する方法は次のとおりです。

<procedure title="手順を導入する" id="inject-a-procedure">
    <step>
        <p>入力を開始し、完了の提案からプロシージャの種類を選択します。</p>
        <img src="completion_procedure.png" alt="completion suggestions for procedure" border-effect="line"/>
    </step>
    <step>
        <p><shortcut>Tab</shortcut> または<shortcut>Enter</shortcut>を押してマークアップを挿入します。</p>
    </step>
</procedure>

## インタラクティブな要素を追加する

### タブ
切り替え可能なコンテンツを追加するには、タブを利用できます（新しい行に入力を開始してタブを挿入します）。

<tabs>
    <tab title="Markdown">
        <code-block lang="plain text">![Alt Text](new_topic_options.png){ width=450 }</code-block>
    </tab>
    <tab title="Semantic markup">
        <code-block lang="xml">
            <![CDATA[<img src="new_topic_options.png" alt="Alt text" width="450px"/>]]></code-block>
    </tab>
</tabs>

### 折りたたみ可能なブロック
XML 要素全体を挿入するだけでなく、属性を使用して特定の要素の動作を構成することもできます。 たとえば、必須ではない情報を含む章を折りたたむことができます。

#### 補足情報 {collapsible="true"}
折りたたみ可能なヘッダーの下のコンテンツはデフォルトで折りたたまれますが、次の属性を追加することで動作を変更できます。
`default-state="expanded"`

### 選択範囲をXMLに変換する
より多くの関数を使用して要素を拡張する必要がある場合は、選択したコンテンツをMarkdownからセマンティックマークアップに変換できます。
たとえば、テーブル内のセルをマージしたい場合は、Markdownでこれを行うよりもXMLに変換する方がはるかに簡単です。 キャレットをテーブルの任意の場所に置き、次のボタンを押します<shortcut>Alt+Enter</shortcut>。 

<img src="convert_table_to_xml.png" alt="Convert table to XML" width="706" border-effect="line"/>

## フィードバックとサポート
問題、ユーザビリティの改善、または機能のリクエストがある場合は、<a href="https://youtrack.jetbrains.com/newIssue?project=WRS">YouTrack project</a>に報告してください(登録する必要があります)。

<a href="https://jb.gg/WRS_Slack">公開Slackワークスペース</a>への参加を歓迎します。
その前に、当社の[行動規範](https://www.jetbrains.com/help/writerside/writerside-code-of-conduct.html)をお読みください。
参加前に読んで確認済みであることを前提としています。

いつでも[writerside@jetbrains.com](mailto:writerside@jetbrains.com)までメールでお問い合わせください

<seealso>
    <category ref="wrs">
        <a href="https://www.jetbrains.com/help/writerside/markup-reference.html">Markup reference</a>
        <a href="https://www.jetbrains.com/help/writerside/manage-table-of-contents.html">Reorder topics in the TOC</a>
        <a href="https://www.jetbrains.com/help/writerside/local-build.html">Build and publish</a>
        <a href="https://www.jetbrains.com/help/writerside/configure-search.html">Configure Search</a>
    </category>
</seealso>
# テンプレートを作成する

sampleapp フォルダ内にtemplates フォルダを作成する

    makedir templates

templates フォルダ内にsampleappフォルダを作成

    makedir sampleapp

templates/sampleapp フォルダ内にpost_list.html を作成する  


とりあえず、いかにアクセスする  

    http://localhost:8000/
    http://127.0.0.1:8000/

空白ページが表示される  

以下を書くと、表示が更新される  

    <html>
    <body>
        <p>Hi there!</p>
        <p>It works!</p>
    </body>
    </html>


head を追加する  

    <html>
        <head>
            <title>Ola's blog</title>
        </head>
        <body>
            <p>Hi there!</p>
            <p>It works!</p>
        </body>
    </html>

自由にテンプレートを作ってみる  

-  \<h1>ヘッダー\</h1> 最も重要性の高い見出し  
-  \<h2>サブのヘッダー\</h2> その次のレベルの見出し  
-  \<h3>サブのサブのヘッダー\</h3>... など\<h6>まで  
-  \<p>文章の段落\</p>  
-  \<em>文章\</em>で文章を強調する  
-  \<strong>文章\</strong>でさらに文章を強調する  
-  \<br>は改行(brタグの中には何も書いてはいけません。閉じタグも無しです)  
-  \<a href="https://djangogirls.org">リンク\</a> はリンクを生成します  
-  \<ul>\<li>第１の項目\</li>\<li>第２の項目\</li>\</ul> でリストを作成する、こんな感じに！  
-  \<div>\</div>はページ内のセクションを定義  


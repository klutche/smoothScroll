# 【jQuery】ページ内リンクをするするーっとスムースにスクロールするJavascript

最近ではページ内でリンクを飛ばす際には当然の仕様となっているスムーススクロールを簡単なタグで実現します。
<!--more-->

## どうだい？スムースだろ？

<a href="http://klutche.org/demo/smooth/" target="_blank">デモページ</a>

個人的にこの動きが大好きです。
1時間くらいならずっとスクロールを見ていられます。
鬱の時なら半日はいけます！

## HTML

`<a href="#bottom">下へスムース！</a>`

なにも工夫しなくて良いです。
ただ＃をつけてアンカーポイントへリンクを貼るだけです。

## Javascript

jQuery依存のスクリプトなので、head内でjQueryを呼び出しましょう。


`<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>`

その後に以下のスクリプトを書きます。

    <script type="text/javascript">
    $(function(){
      $('a[href^=#]').click(function(){
    		var speed = 500;
    		var href= $(this).attr("href");
    		var target = $(href == "#" || href == "" ? 'html' : href);
    		var position = target.offset().top;
    		$("html, body").animate({scrollTop:position}, speed, "swing");
    		return false;
    	});
    });
    </script>

これで、ページ内リンクであれば勝手にスムーススクロール処理をしてくれます。

`var speed = 500;`の部分がスクロール完了までの時間です。
数字が小さいほどシャッ!と動きます。

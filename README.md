# original_master_thesis
東工大の博士論文や修士論文に良さそうです．

## コンパイル関係
**環境** UTF-8

**実行** pdfLaTeX

**文字** 現在の所，英語推奨です．

## 構成
mainファイルを中心に構成されています．
### figures
いわずもがな，画像ファイルが保存されています．pdf形式かeps形式が好まれます．
### sections
論文の各章がそれぞれ収められています．Appendixもここに追加してください．

必要に応じて増やしてください．

mainファイルへは以下のように追加．
```
%%%%% CHAPTERS
% Add or remove any chapters you'd like here, by file name (excluding '.tex'):
\flushbottom
\include{sections/ch1-intro}
\include{sections/ch2-litreview}

%% APPENDICES %% 
% Starts lettered appendices, adds a heading in table of contents, and adds a
%    page that just says "Appendices" to signal the end of your main text.
\startappendices
% Add or remove any appendices you'd like here:
\include{sections/appendix-1}
```
### text
アブストラクト，謝辞，略語集，およびLaTeX設定で必要なpreambleとsettingが入っています．

書き方は実際ファイル見てください．

preambleとsettingには自分の所属や名前を書いたりするところがあるので，読んでください．
## 日本語にしたいんだけど…
**pdfLaTeXエンジンではまず無理です!**

本フォーマットはLuaLaTeXでもコンパイルできるため，[lualatexja.styパッケージ](https://www.ctan.org/pkg/luatexja)を用いた日本語設定も可能です．

説明文は長いですが，ここからダウンロードしたフォルダの中からlualatexja.styファイルだけをmainファイルと同じディレクトリに置けば最低限動きます．

しかしパッケージ制作者も述べている通り，コンパイル時間が尋常じゃないくらい長くなるのであまりお勧めできないです…

やりましたがコンパイルに3分くらいかかりました．

日本語でのコンパイルは[こちら](https://qiita.com/wtsnjp/items/76557b1598445a1fc9da#%E6%96%B0%E5%B8%B8%E8%AD%98-4-%E6%97%A5%E6%9C%AC%E8%AA%9E-latex-%E3%81%AF-uplatex-%E3%81%A0%E3%81%91%E3%81%98%E3%82%83%E3%81%AA%E3%81%84)も参考にしてください．

## Overleaf
Overleafにてサンプル例を作りました．  
プロジェクトをコピーして自分で編集してもらってもコンパイルができると思います．  
<https://www.overleaf.com/read/tvqmjjtzrwwj>

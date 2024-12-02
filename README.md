# original_master_thesis
*Science Tokyo*の博士論文や修士論文に良さそうです．

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

## VSCode LaTeX Workshopでの利用
VSCodeの [$\LaTeX$ Workshop extension](https://github.com/James-Yu/LaTeX-Workshop) を用いてコンパイルできる事を確認しています. 
この拡張機能の使用方法については他の記事を参照してください. 

<https://qiita.com/rainbartown/items/d7718f12d71e688f3573>

以下はコンパイル時のVSCode内setting.jsonの設定箇所です.
```
"[tex]": {
    // スニペット補完中にも補完を使えるようにする
    "editor.suggest.snippetsPreventQuickSuggestions": false,
    // インデント幅を2にする
    "editor.tabSize": 2
},

"[latex]": {
    // スニペット補完中にも補完を使えるようにする
    "editor.suggest.snippetsPreventQuickSuggestions": false,
    // インデント幅を2にする
    "editor.tabSize": 2
},

"[bibtex]": {
    // インデント幅を2にする
    "editor.tabSize": 2
},


// ---------- LaTeX Workshop ----------

// 使用パッケージのコマンドや環境の補完を有効にする
"latex-workshop.intellisense.package.enabled": true,
// 生成ファイルを削除するときに対象とするファイル
// デフォルト値に "*.synctex.gz" を追加
"latex-workshop.latex.clean.fileTypes": [
    "*/*.aux",
    "*/*.bbl",
    "*/*.blg",
    "*/*.idx",
    "*/*.ind",
    "*/*.lof",
    "*/*.lot",
    "*/*.out",
    "*/*.toc",
    "*/*.acn",
    "*/*.acr",
    "*/*.alg",
    "*/*.glg",
    "*/*.glo",
    "*/*.gls",
    "*/*.ist",
    "*/*.fls",
    "*/*.log",
    "*/*.fdb_latexmk",
    "*/*.snm",
    "*/*.nav",
    "*/*.dvi",
    "*/*.synctex.gz"
],

// 生成ファイルを "out" ディレクトリに吐き出す
"latex-workshop.latex.outDir": "out.nosync",
// ビルドのレシピ
"latex-workshop.latex.recipes": [
    {
        "name": "pdflatex",
        "tools": [
            "pdflatex",
            "makeglossaries",
            "biber",
            "pdflatex",
            "pdflatex",
        ]
    },
],

// ビルドのレシピに使われるパーツ
"latex-workshop.latex.tools": [
    {"name": "pdflatex",
    "command": "pdflatex",
    "args": [
        "--shell-escape", // if you want to have the shell-escape flag
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "-output-directory=out.nosync",
        //"-output-directory=out",
        //"-aux-directory=out.nosync",
        "%DOC%" 
        ]
    },
    {"name": "biber",
    "command": "biber",
    "args": [
        "--output-directory=out.nosync",
        "%DOCFILE%"
        ]
    },
    {"name": "makeglossaries",
    "command": "makeglossaries",
    "args": [
        "-dout.nosync",
        "%DOCFILE%"
        ]
    },
],

"latex-workshop.latex.rootFile.indicator": "\\begin{document}",
"latex-workshop.view.pdf.viewer": "tab",
"latex-workshop.latex.autoClean.run": "onSucceeded",
"latex-workshop.latex.rootFile.useSubFile": true,
"latex-workshop.latex.recipe.default": "lastUsed",
"latex-workshop.latex.clean.subfolder.enabled": true,
```

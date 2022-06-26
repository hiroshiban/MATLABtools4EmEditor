# **README on MATLABtools4EmEditor**

<div align="right">
Created    : "2009-01-21 15:08:02 ban"<br>
Last Update: "2022-06-27 01:59:23 ban"
</div>

<br>
<div align="center">
<img src="https://img.shields.io/badge/LANGUAGE-MATLAB-brightgreen" />
<img src="https://img.shields.io/badge/EDITED%20BY-EmEditor-blue" />
<img src="https://img.shields.io/badge/LICENSE-BSD-red" /><br>
<img src="https://img.shields.io/badge/KEYWORDS-EmEditor,MATLAB,%20Macro,%20Syntax,%20Highlighting,%20Linter,%20-blue?style=social&logo=webauthn" /><br>
<img src="https://img.shields.io/badge/CONTACT-lightgrey" /> <img src="doc/images/ban_hiroshi_address.png" />
</div>
<br>

# **MATLABtools4EmEditor -- EmEditor用MATLABスクリプト記述支援ツール**

English version of README.md is available from [here.](https://github.com/hiroshiban/MATLABtools4EmEditor)  
英語版 README.mdは[こちら](https://github.com/hiroshiban/MATLABtools4EmEditor)  

![matlabtools4emeditor](doc/images/matlabtools4emeditor.png)  
*MATLABtools4EmEditor は、EmEditor上でのMATLABプログラミングを支援する機能を提供します。*  
<br>

このパッケージは、**MATLAB**コードを**EmEditor**上で記述する際に役立つ、構文定義ファイル(*.esy)、コード・スニペット(*.eesnip)、JavaScriptによる簡易マクロ(*.jsee)の一連のファイルからなります。これらのファイルを組み込むことで、EmEditor上でMATLABキーワード(オペレータや関数名)をハイライトしたり、MATLAB標準の構文チェッカー・mlint.extと連携してコードのエラーや警告を検出したり、マクロとスニペットによるコード記述の半自動化などの支援機能が使えるようになります。このパッケージがみなさまのお役に立ちましたら幸いです。

(EmEditorは、[***Emurasoft, Inc.*** ](https://www.emeditor.com/)の登録商標です)  
(Matlabは、[***The Mathworks Inc.*** ](https://www.mathworks.com/)の登録商標です)  


## **パッケージの構成**

![mlint](doc/images/mlint.gif)  

*スニペット(あるいはマクロ)の1つ、mMLINTを用いることで EmEditorからmlint.exeを呼び出してMALTAB構文の解析が可能です。*  

![time_stamp](doc/images/time_stamp.gif)  

*mINS_TSTAMPを用いることで、MATLABファイルの保存時に保存時間を自動挿入できます。*  
<br>
<pre>
matlab_with_toolboxes.esy : MATLABとMATLAB_toolbox用のEmEditor構文ファイル
    のフルバージョンです。
    このファイルはMATLABコード中の関数やオペレータ等のキーワードをハイライトする
    ための構文ファイルです。本ファイルに登録されたキーワードは、auto-completion
    プラグインと連携してキーワードを自動補完する際にも利用できます。
    なお、このフルバージョンの構文ファイルには、MATLAB本体、Simlink、および
    MATLAB Toolboxに含まれるほぼ全ての関数をカバーしているため、場合によっては
    ハイライトがかえって煩わしかったり、コード補完の候補が多すぎて使いづらいことが
    あるかもしれません。その場合は、EmEditorに構文ファイルを読み込ませる前に不要な
    部分を削除したください。あるいは、かわりに下の簡易バージョンをお使いください。
    主にMATLAB R2022aに含まれる関数、キーワード名に基づいてファイルを作成しています。

matlab_with_toolboxes_light.esy : MATLABとMATLAB_toolbox用のEmEditor構文ファイル
    の簡易バージョンです。
    このファイルはMATLABコード中の関数やオペレータ等のキーワードをハイライトする
    ための構文ファイルです。本ファイルに登録されたキーワードは、auto-completion
    プラグインと連携してキーワードを自動補完する際にも利用できます。
    もし上のフルバージョンの構文ファイルほどに全てのキーワードをカバーする必要がない
    場合は、こちらの簡易バージョンをお使いください。
    主にMATLAB R2009に含まれる関数、キーワード名に基づいてファイルを作成しています。

EmEditor_MATLAB_snippet.eesnip : MATLAB用のEmEditorスニペットファイル(EmEditor
    の仕様で、自動化マクロ等もスニペット内に含みます)です。
    MATLABプログラミングでよく利用されるマクロを呼び出したり、定型文の自動挿入が可能
    となります。
    現在、下記のマクロに対応しています
    1. mCLEAN: Javascriptマクロ
              コード内から余分なスペース(行末の空白や空行の空白など)を削除します。
    2. mCOMMENT_LINE : Javascriptマクロ
              行コメント、操作をキーボードショートカットに登録するために用意しています。
    3. mCOMMENT_REGION : Javascriptマクロ
              選択領域コメント、操作をキーボードショートカットに登録するために用意して
              います。
    4. mENDLINE : Javascriptマクロ
              行末に(ない場合)セミコロンを追加、操作をキーボードショートカットに登録す
              るために用意しています。
    5. mINDENT : Javascriptマクロ
              選択領域をインデント、操作をキーボードショートカットに登録するために用意
              しています。
    6. mINS_TSTAMP : Javascriptマクロ
              タイムスタンプの自動挿入。
              MATLABソースコード保存時に行頭から200行以内に特定の記述
              (Lastt Update : "")があるかを探索し、検出された場合にはその部位に保存
              時間を自動挿入します。 (ご注意：特定の記述中、Lasttの部分は実際にはLast)
    7. mMLINT : Javascriptマクロ
              mlint.exeを呼び出してソースコードを解析し、エラー・警告を表示します。
              マクロの最初の部分で使用するmlintをフルパスで指定している部分があります
              ので、ご自身の環境に合わせて適宜ご変更ください。
    8. mNEWLINE : Javascriptマクロ
              次の行へ移動、操作をキーボードショートカットに登録するために用意してい
              ます。
    9. mNEXTCHAR : Javascriptマクロ
              次の文字へ移動、操作をキーボードショートカットに登録するために用意して
              います。
    10. mPREVCHAR : Javascriptマクロ
              前の行へ移動、操作をキーボードショートカットに登録するために用意してい
              ます。
    11. mPREVLINE : Javascriptマクロ
              前の文字へ移動、操作をキーボードショートカットに登録するために用意して
              います。
    12. mRETURN : Javascriptマクロ
              (ない場合に)行末にセミコロンをつけて改行挿入。
    13. mSCRATCH : Javascriptマクロ
              MATLABコードテスト用のスクラッチバッファを新規作成します(MATLAB設定の
              テキストファイルの新規作成(無保存状態))。
              Gnu Emacsのelisp scratch bufferにインスパイアされて用意いたしました。
    14. mUNTABIFY : Javascriptマクロ
              タブを全てスペースに変換、操作をキーボードショートカットに登録するために
              用意しています。
    15. このスニペットファイルを用いることで、下記の定型文の自動挿入が可能となります。
              BSD, case, clear, Comment Divide, disp, disp sprintf, dlmwrite,
              else, elseif, error, exp, for, fprintf, function, get, GPL,
              griddata, if ... else ... end, if ... elseif ... end,
              if ... end, line, nargchk, Octave function, Revisions,
              set, small function, sprintf,
              switch ... case ... otherwise ... end,
              switch ... case ... end, title, try ... catch ... end,
              unix, unwind_protect ... cleanup ... end, warning, while,
              xlabel, xtick, ylabel, ytick, zlabel
              これらのコード・スニペットは、TextMateのMATLABスニペットに
              インスパイアされて用意いたしました。

macros -- ディレクトリ、EmEditor用のJavascriptマクロが含まれています。
    このディレクトリに含まれる全てのマクロは、上のスニペットファイルに既に組みこん
    でありますので、スニペットファイルをご利用になられる場合には、このディレクトリ
    内のファイルを使用する必要はありません。
    もし上のスニペットファイルをご使用になられず、マクロの機能(の全て、あるいは一部)
    だけをご利用になられたい場合には、必要な機能に対応するファイルをここから
    EmEditorのマクロディレクトリにコピーしてお使いください。
</pre>

## **ライセンス**  

<img src="https://img.shields.io/badge/LICENSE-BSD-red" /><br>

MATLABtools4EmEditor -- utilities for editing MATLAB codes with EmEditor. Copyright (c) 2022 Hiroshi Ban. All rights reserved.  

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:  

    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.
    * Redistributions in binary form must reproduce the above copyright
      notice, this list of conditions and the following disclaimer in
      the documentation and/or other materials provided with the distribution

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.  

The views and conclusions contained in the software and documentation are those of the authors and should not be interpreted as representing official policies, either expressed or implied, of the FreeBSD Project.  

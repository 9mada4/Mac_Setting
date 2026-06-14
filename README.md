# Mac_環境
- 備忘録です．

<details>
<summary>基本</summary>
Macでのインストールは基本

`brew install XXX` でどうにかなる．
</details>

---
## Word for Macの設定
1. `Normal.dotm`をダウンロード
2. Finderで command⌘ + shift + g
3. ここに移動
   ```
   cd ~/Library/Group\ Containers/UBF8T346G9.Office/User\ Content.localized/Templates/
   ```
   または
   ```
   ~/Library/Group\ Containers/UBF8T346G9.Office/User\ Content.localized/Templates.localized/
   ```
4. 既存のNormal.dotmを置き換え
5. Word再起動

⚠️デフォルトに戻す場合はNormal.dotmを削除することで，Word起動時に再生成される．

---
## CRDのキーボード設定
2025-07-16<br>
Chrome Remoto Desktop(CRD)でWindows10をMacから操作するときのキーボード設定．
1. Windowsの設定(キーの割当設定)<br>
    時刻と言語 > 言語 > 日本語 > オプション
    - レイアウト > **日本語キーボード(106/109キー)**　(PC再起動必須?)
    - キーボード > Microsoft IME > オプション > キーとタッチのカスタマイズ > キーの割り当て
      | 設定 | 推奨 |
      | --- | --- |
      | 無変換キー | **IME-オフ（または IMEオン/オフ）** |
      | 変換キー | **IME-オン** |
2. Karabineerの設定(Mac側のキー送り調整)<br>
   Karabineerで Eisu→F13，Kana→F14 に変更(CRD起動時のみの変換)
    - CRDにキーが送られる前にMac側で変換キーとして消費されるため．
    - アプリのID↓は環境ごとに違うはずなので，KarabineerのEventViewerで調べる必要あり．
      "com.google.Chrome.app.cmkncekebbebpfilplodngbpllndjkfo"

3. CRDの設定(Mac→Windowsでの変換設定)<br>
   CRDのサイドパネル(初期設定は右) > キーマッピングの設定
    - 以下のように設定すると，基本はMacと同じ操作感になる．
    - Windowsキーは右⌘(MetaRight)になっている．
      | マッピング元のキー | マッピング先のキー |
      | --- | --- |
      | F13 | NonConvert |
      | F14 | Convert |
      | MetaLeft | ControlLeft |


---

## Hammerspoon　" ウィンドウ操作 "
init.luaを以下のディレクトリにコピーすると，コマンドが使えるようになる．

`/Users/ユーザー名/.hammerspoon/init.lua`

<details>
<summary>コマンド</summary>

1. ショートカット：Ctrl + Option + Command + →　で右モニターに送る
2. ショートカット：Ctrl + Option + Command + ←　で左モニターに送る
3. ショートカット：Command + ろ でGUIメニューを起動  
- ウィンドウの配置をGUIメニューから選択

    - `　中央に配置　`

    - ```
        　1枚目ウィンドウ ■　　2/3
        ■■□　□□
        ■■□　□●
        ■■□　□●
        　2枚目ウィンドウ ●　　2/3 * 1/2
        ```
    - `　■□　□●　1枚目ウィンドウ ■　 1/2左寄せ `
    - `　●□　□■　1枚目ウィンドウ ■　 1/2右寄せ `
    - `　■■□　□□●　1枚目ウィンドウ ■　 2/3左寄せ `
 
    ---

</details>

- Reload Configをしないと反映されない
- ステージマネージャーと併用すると良い
- デスクトップは一つのモニターで3つまでがよい
- `トラックパッド > フルスクリーンアプリケーションをスワイプ　> 4本指で左右にスワイプ`をONにして上下左右にスライドすると感動する

---

## Touch IDが反応しない

解決方法: Macに触れる
仮説: 静電容量方式のセンサーが乾燥した環境の静電気などで反応しずらくなっていた
- 実際に10月末にいきなり反応しなくなり，これによって解消された．

日本語記事
https://zenn.dev/monoduki_tech/articles/6a4f40af85bf8a
Apple Comunity元記事
https://discussions.apple.com/thread/255054380?sortBy=rank

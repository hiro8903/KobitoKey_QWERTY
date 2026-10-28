# KobitoKey_QWERTY

小人キーや人キーのケース、TypeSurfer各種の3DデータはReleasesよりダウンロード出来ます。
ダサい使い方はしないこと。


Layer 0 QWERTY
<img width="1280" height="690" alt="Image" src="https://github.com/user-attachments/assets/ef0797b7-a63f-4632-912d-9b5d0115769f" />

Layer 1 NUMBER & ARROW
<img width="1280" height="690" alt="Image" src="https://github.com/user-attachments/assets/d6347b3c-a238-4278-bacd-e58195774d0e" />

Layer 2 Bluetooth & FUNCTION
<img width="1280" height="690" alt="Image" src="https://github.com/user-attachments/assets/f1f7cc93-fbd8-4a98-84ea-c8c36ad3952d" />

Layer 3 AUTO MOUSE
<img width="1280" height="690" alt="Image" src="https://github.com/user-attachments/assets/2efe5275-e460-41bc-ae45-0c0665435268" />

---

## 📖 初心者向け 設定ファイル解説ドキュメント

このセクションでは、自作キーボード「小人キー」のキーマップやトラックボール設定をスムーズにカスタマイズできるよう、各設定ファイルのコード全文と行ごとの詳細な解説をまとめています。  
（※実際の設定ファイルの動作に影響が出ないよう、解説・コメントはすべてこのドキュメントに集約しています）

### 📑 目次
- [1. config/KobitoKey.json（GUI用物理レイアウト定義）](#1-configkobitokeyjson)
<!-- 今後追加予定:
- 2. config/KobitoKey.keymap（キー割り当て・レイヤー・コンボ定義）
- 3. config/boards/shields/KobitoKey/KobitoKey_left.overlay（左手トラックボール・マトリクス定義）
- 4. config/boards/shields/KobitoKey/KobitoKey_left.conf（左手側Bluetooth・設定）
- 5. config/boards/shields/KobitoKey/KobitoKey_right.overlay / conf（右手側定義）
- 6. config/boards/shields/KobitoKey/kobitokey.dtsi（共通ハードウェア定義）
-->

---

### 1. config/KobitoKey.json

- **編集・対象ファイル**: [`config/KobitoKey.json`](./config/KobitoKey.json)
- **ファイルの種類**: JSON (レイアウト定義)
- **ファイルの役割**: 
  - Nick Coutsos の「[Keymap Editor](https://nickcoutsos.github.io/keymap-editor/)」や「ZMK Studio」などの視覚的GUIエディタで、キーボードの物理的なキー配置（画面上の見た目）を正しく描画するための設定ファイルです。
  - **※注意**: 実際の「どのキーを押したら何の文字が出るか」というキー割り当ては [`config/KobitoKey.keymap`](./config/KobitoKey.keymap) に記述します。また、トラックボールの感度等の設定は `config/boards/shields/KobitoKey/` 配下にあります。

#### コード全文と解説（コメント付き）

```jsonc
{
  // キーボードの一意な識別子（ID）
  "id": "KobitoKey",

  // ツール等の画面上に表示されるキーボードの名称
  "name": "KobitoKey",

  // レイアウトの定義グループ
  "layouts": {
    // デフォルト（標準）レイアウトの定義
    "default_layout": {
      "name": "default_layout",

      // 各キーの物理配置リスト（全40キー：左右各20キー）
      // 【各項目の意味】
      //   row : スイッチマトリクスの行番号（0〜3行目）
      //   col : スイッチマトリクスの列番号（0〜9列目。0〜4が左手、5〜9が右手）
      //   x   : 画面上での横位置（1キー幅 = 1.0。左手と右手の間はトラックボール等を考慮し隙間が空いています）
      //   y   : 画面上での縦位置（1行下がるごとに +1.0）
      "layout": [
        // ----------------------------------------------------------------------
        // 【1行目 (最上段 / row: 0)】 全10キー
        // ----------------------------------------------------------------------
        // [左手側: row 0, col 0〜4] （KobitoKey.keymap では Q, W, E, R, T に対応）
        { "row": 0, "col": 0, "x":    0, "y": 0 }, // 左手小指 (例: Q)
        { "row": 0, "col": 1, "x":    1, "y": 0 }, // 左手薬指 (例: W)
        { "row": 0, "col": 2, "x":    2, "y": 0 }, // 左手中指 (例: E)
        { "row": 0, "col": 3, "x":    3, "y": 0 }, // 左手人差指 (例: R)
        { "row": 0, "col": 4, "x":    4, "y": 0 }, // 左手人差指 内側 (例: T)

        // [右手側: row 0, col 5〜9] （KobitoKey.keymap では Y, U, I, O, P に対応）
        // ※ xが4から6.5に飛んでいるのは、左右の間にトラックボール用の隙間（2.5キー分）があるため
        { "row": 0, "col": 5, "x":  6.5, "y": 0 }, // 右手人差指 内側 (例: Y)
        { "row": 0, "col": 6, "x":  7.5, "y": 0 }, // 右手人差指 (例: U)
        { "row": 0, "col": 7, "x":  8.5, "y": 0 }, // 右手中指 (例: I)
        { "row": 0, "col": 8, "x":  9.5, "y": 0 }, // 右手薬指 (例: O)
        { "row": 0, "col": 9, "x": 10.5, "y": 0 }, // 右手小指 (例: P)

        // ----------------------------------------------------------------------
        // 【2行目 (ホームポジション段 / row: 1)】 全10キー
        // ----------------------------------------------------------------------
        // [左手側: row 1, col 0〜4] （KobitoKey.keymap では A, S, D, F, G に対応）
        { "row": 1, "col": 0, "x":    0, "y": 1 }, // 左手小指 (例: A)
        { "row": 1, "col": 1, "x":    1, "y": 1 }, // 左手薬指 (例: S)
        { "row": 1, "col": 2, "x":    2, "y": 1 }, // 左手中指 (例: D)
        { "row": 1, "col": 3, "x":    3, "y": 1 }, // 左手人差指 (例: F)
        { "row": 1, "col": 4, "x":    4, "y": 1 }, // 左手人差指 内側 (例: G)

        // [右手側: row 1, col 5〜9] （KobitoKey.keymap では H, J, K, L, ; に対応）
        { "row": 1, "col": 5, "x":  6.5, "y": 1 }, // 右手人差指 内側 (例: H)
        { "row": 1, "col": 6, "x":  7.5, "y": 1 }, // 右手人差指 (例: J)
        { "row": 1, "col": 7, "x":  8.5, "y": 1 }, // 右手中指 (例: K)
        { "row": 1, "col": 8, "x":  9.5, "y": 1 }, // 右手薬指 (例: L)
        { "row": 1, "col": 9, "x": 10.5, "y": 1 }, // 右手小指 (例: ;)

        // ----------------------------------------------------------------------
        // 【3行目 (下段 / row: 2)】 全10キー
        // ----------------------------------------------------------------------
        // [左手側: row 2, col 0〜4] （KobitoKey.keymap では Z, X, C, V, B に対応）
        { "row": 2, "col": 0, "x":    0, "y": 2 }, // 左手小指 (例: Z)
        { "row": 2, "col": 1, "x":    1, "y": 2 }, // 左手薬指 (例: X)
        { "row": 2, "col": 2, "x":    2, "y": 2 }, // 左手中指 (例: C)
        { "row": 2, "col": 3, "x":    3, "y": 2 }, // 左手人差指 (例: V)
        { "row": 2, "col": 4, "x":    4, "y": 2 }, // 左手人差指 内側 (例: B)

        // [右手側: row 2, col 5〜9] （KobitoKey.keymap では N, M, ,, ., ' に対応）
        { "row": 2, "col": 5, "x":  6.5, "y": 2 }, // 右手人差指 内側 (例: N)
        { "row": 2, "col": 6, "x":  7.5, "y": 2 }, // 右手人差指 (例: M)
        { "row": 2, "col": 7, "x":  8.5, "y": 2 }, // 右手中指 (例: ,)
        { "row": 2, "col": 8, "x":  9.5, "y": 2 }, // 右手薬指 (例: .)
        { "row": 2, "col": 9, "x": 10.5, "y": 2 }, // 右手小指 (例: ')

        // ----------------------------------------------------------------------
        // 【4行目 (最下段・親指キーなど / row: 3)】 全10キー
        // ----------------------------------------------------------------------
        // [左手側: row 3, col 0〜4] （KobitoKey.keymap では LSHFT, LALT, LCMD, SPACE(LT2), LCTRL に対応）
        // ※ 親指キー等は手の自然な開きに合わせて x の配置が調整されています (2.5, 3.5, 4.5)
        { "row": 3, "col": 0, "x":    0, "y": 3 }, // 左端キー (例: Left Shift)
        { "row": 3, "col": 1, "x":    1, "y": 3 }, // 左から2番目 (例: Left Alt)
        { "row": 3, "col": 2, "x":  2.5, "y": 3 }, // 親指キー外側 (例: Left Cmd)
        { "row": 3, "col": 3, "x":  3.5, "y": 3 }, // 親指キー中央 (例: Space / タップでSpace, 長押しでLayer2)
        { "row": 3, "col": 4, "x":  4.5, "y": 3 }, // 親指キー内側 (例: Left Ctrl)

        // [右手側: row 3, col 5〜9] （KobitoKey.keymap では BSPC, ENTER(LT1), RSHFT, RSHFT, SLASH(LALT) に対応）
        { "row": 3, "col": 5, "x":    6, "y": 3 }, // 親指キー内側 (例: Backspace)
        { "row": 3, "col": 6, "x":    7, "y": 3 }, // 親指キー中央 (例: Enter / タップでEnter, 長押しでLayer1)
        { "row": 3, "col": 7, "x":    8, "y": 3 }, // 親指キー外側 (例: Right Shift)
        { "row": 3, "col": 8, "x":  9.5, "y": 3 }, // 右から2番目 (例: Right Shift)
        { "row": 3, "col": 9, "x": 10.5, "y": 3 }  // 右端キー (例: Slash / 長押しでLeft Alt)
      ]
    }
  },

  // ロータリーエンコーダー等の回転センサー定義（KobitoKeyでは未使用のため空配列）
  "sensors": []
}
```


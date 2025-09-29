# Karabiner Key Bind Config

macOSでKarabiner-Elementsを使用して、JIS配列の外部キーボードの挙動をWindowsに近づけるための設定ファイルです。

## 概要

このプロジェクトでは、MacでJIS配列の外部キーボードを使用する際の操作感をWindowsに近づけるためのKarabiner-Elementsの設定を提供します。**Mac本体のキーボードは設定対象外**で、JIS配列外部キーボードの操作感の違いを最小限に抑えることを目的としています。

## 機能

- JIS配列外部キーボードのWindows風キーバインド設定
- アプリケーション固有のキーマッピング
- カスタムショートカットの定義
- Mac本体キーボードへの影響なし

## ファイル構成

```
karabiner-key-bind-config/
├── karabiner.json              # メイン設定ファイル
├── rules/                      # ルールファイル群
│   ├── grave_accent_toggle.json      # 半角・全角切り替え
│   └── windows_ctrl_shortcuts.json   # Windows風Ctrlショートカット
└── README.md                   # このファイル
```

## インストール方法

1. [Karabiner-Elements](https://karabiner-elements.pqrs.org/)をインストール
2. このリポジトリをクローンまたはダウンロード
3. `karabiner.json`を`~/.config/karabiner/`にコピー
4. `rules/`フォルダ内のルールファイルを`~/.config/karabiner/assets/complex_modifications/`にコピー
5. Karabiner-Elementsを再起動
6. **重要**: Karabiner-ElementsのUIで、JIS配列の外部キーボードにのみ設定を適用してください。Mac本体のキーボードには影響しません。

```bash
# 設定ファイルのコピー
cp karabiner.json ~/.config/karabiner/

# ルールファイルのコピー
mkdir -p ~/.config/karabiner/assets/complex_modifications/
cp rules/*.json ~/.config/karabiner/assets/complex_modifications/
```

### 設定の適用

Karabiner-ElementsのUIで以下の手順で設定を適用してください：

1. Karabiner-Elementsを開く
2. 「Devices」タブでJIS配列の外部キーボードを選択
3. 「Complex Modifications」タブで必要なルールを有効化
4. Mac本体のキーボードは設定対象から除外

## 設定内容

### 利用可能なルール

#### 1. grave_accent_toggle.json
- **` キー**: 半角・全角の双方向切り替え
- Windowsの ` キーと同じ挙動を再現

#### 2. windows_ctrl_shortcuts.json
- **Ctrl + C/V/X**: コピー/ペースト/カット
- **Ctrl + Z/Y**: アンドゥ/リドゥ
- Windows風のCtrlショートカットを実現

### 基本的なキーマッピング（simple_modifications）

- **無変換/変換キー**: 英数/かな切り替え
- **Ctrlキー**: Commandキーにマッピング
- **Caps Lock**: Ctrlキーにマッピング

## カスタマイズ

### 新しいルールの追加

1. `rules/`フォルダに新しいJSONファイルを作成
2. ルールファイルを`~/.config/karabiner/assets/complex_modifications/`にコピー
3. Karabiner-ElementsのUIでルールを有効化

### ルールファイルの構造

```json
{
  "title": "ルールのタイトル",
  "rules": [
    {
      "description": "ルールの説明",
      "manipulators": [
        {
          "type": "basic",
          "from": { "key_code": "キーコード" },
          "to": [ /* 変換先 */ ]
        }
      ]
    }
  ]
}
```

### 基本的な設定の変更

`karabiner.json`の`simple_modifications`セクションで基本的なキーマッピングを変更できます。

## トラブルシューティング

### 設定が反映されない場合

1. Karabiner-Elementsが正しくインストールされているか確認
2. 設定ファイルのパスが正しいか確認（`~/.config/karabiner/karabiner.json`）
3. Karabiner-Elementsを再起動
4. システム環境設定 > セキュリティとプライバシー > プライバシー > アクセシビリティでKarabiner-Elementsが許可されているか確認
5. **重要**: Karabiner-ElementsのUIで、JIS配列の外部キーボードが正しく選択されているか確認

### キーマッピングが競合する場合

他のアプリケーションやシステム設定と競合する場合は、Karabiner-ElementsのUIで設定を調整するか、`karabiner.json`の設定を編集してください。

### Mac本体のキーボードに影響が出る場合

Karabiner-Elementsの「Devices」タブで、Mac本体のキーボードを設定対象から除外してください。

## ライセンス

このプロジェクトはMITライセンスの下で公開されています。

## 貢献

バグ報告や機能要望は、GitHubのIssuesでお知らせください。プルリクエストも歓迎します。

## 更新履歴

- v1.0.0: 初回リリース
  - 基本的なWindows風キーマッピングを実装

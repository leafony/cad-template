# Leafony CAD Templates

[Leafony](https://leafony.com/)の拡張リーフ基板を設計するためのCADテンプレート集です。基板外形、Leafony busの接続部、デザインルールなどを設定した設計データを、KiCadとCR-8000 Design Force向けに収録しています。

## 収録テンプレート

| CAD | 使用するバージョン | 内容・使い方 |
| --- | --- | --- |
| KiCad | 10.0系 | 回路図、PCB、プロジェクト設定、専用ライブラリ。[設定・利用手順](KiCad/README.md) |
| CR-8000 Design Force | 2020以降（同梱readmeの記載） | 設計データとライブラリ一覧を含む[ZIPアーカイブ](DesignForce/Leafony_Template/Design_Force_Leafony_Template.zip) |

KiCad版の回路図・PCBはKiCad 10.0形式で保存されています。以前のREADMEにあった「KiCad 6.0.0以降」は、現在のファイルには適用されません。

```text
cad-template/
├── KiCad/
│   ├── README.md
│   ├── Leafony_Template/
│   │   ├── Leafony_Template.kicad_pro   # プロジェクト設定
│   │   ├── Leafony_Template.kicad_sch   # 回路図
│   │   ├── Leafony_Template.kicad_pcb   # 基板レイアウト
│   │   ├── sym-lib-table / fp-lib-table
│   │   ├── lib/                        # 専用シンボル・フットプリント
│   │   └── meta/                       # テンプレート選択画面用の情報
│   └── img/
└── DesignForce/
    └── Leafony_Template/
        └── Design_Force_Leafony_Template.zip
```

## ダウンロード

リポジトリをクローンしてください。

```sh
git clone https://github.com/leafony/cad-template.git
```

Gitを使わない場合は、[GitHubのリポジトリページ](https://github.com/leafony/cad-template)で **Code → Download ZIP** を選び、ダウンロードしたZIPを展開します。ライブラリなどの参照先も必要なため、プロジェクトファイルだけでなくフォルダ全体を取得してください。

## KiCadで使う

1. KiCad 10.0系と標準ライブラリをインストールします。
2. KiCadのユーザーテンプレートの場所に、このリポジトリの `KiCad` フォルダを指定します。
3. 新規プロジェクトのテンプレートとして **Leafony Leaf** を選び、作業用フォルダにプロジェクトを作成します。
4. 作成したプロジェクトでLeafonyのシンボルライブラリを登録し、回路と基板を編集します。

パスの設定例、ライブラリ登録、設計開始時の確認事項は、[KiCad/README.md](KiCad/README.md)を参照してください。

## Design Forceで使う

1. [Design_Force_Leafony_Template.zip](DesignForce/Leafony_Template/Design_Force_Leafony_Template.zip)を作業用フォルダに展開します。
2. `template-design/readme.txt` を確認します。
3. Design Forceで **ファイル → 開く → 設計データ** を選び、`template-design/Design Force/Leafony_Template.dsgn` を開きます。
4. 別名で保存し、設計を開始します。

ZIPには `LeafonyTemplateLibraryList.xlsx` とプレビュー画像も含まれています。対応バージョンと操作手順は、ZIP内のreadmeに基づいています。

## 設計時の確認

テンプレートを基に、使用するリーフとのピン割り当て、電源、I2Cアドレス、部品高さや積層時の干渉を確認してください。基板の寸法・層構成・製造ルールは各CADデータで確認し、製造先の条件に合わせて調整します。設計完了時には回路・基板のルールチェックと製造データの確認を行ってください。

ピン配置、I2Cアドレス、基板製造データの作成については、[Leafony公式ドキュメント「自作リーフ開発」](https://docs.leafony.com/pcb/)を参照してください。

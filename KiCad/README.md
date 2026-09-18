# Leafony KiCad Template

Leafonyの拡張リーフ基板を設計するためのKiCadプロジェクトテンプレートです。Leafony busのシンボルとフットプリント、基板外形、層構成、デザインルールを収録しています。

[リポジトリ全体の案内に戻る](../README.md)

## 対応環境

- **KiCad 10.0系**を使用してください。収録する回路図・PCB・フットプリントはKiCad 10.0で保存されています。
- KiCadの標準シンボル・フットプリントライブラリもインストールしてください。回路図の電源シンボルは標準の `power` ライブラリを参照します。

旧READMEの「KiCad 6.0.0以降」という記載は現在のデータには適用されません。KiCad 9以前は対象外です。KiCadは新しいバージョンで保存したファイルを古いバージョンで開けない場合があります。[KiCad公式マニュアル](https://docs.kicad.org/10.0/ja/kicad/kicad.html)も参照してください。

## ファイル構成

以下のパスは、このREADMEがある `KiCad` フォルダからの相対パスです。

| パス | 用途 |
| --- | --- |
| `Leafony_Template/Leafony_Template.kicad_pro` | プロジェクト設定、デザインルール、ネットクラス |
| `Leafony_Template/Leafony_Template.kicad_sch` | Leafony bus、電源、信号ラベルを配置した回路図 |
| `Leafony_Template/Leafony_Template.kicad_pcb` | 基板外形、接続部、ビア、銅箔ゾーン禁止領域を含むPCB |
| `Leafony_Template/lib/Leafony.kicad_sym` | `Leafony Bus` シンボル |
| `Leafony_Template/lib/Leafony.pretty/` | `CN_F29_B29` フットプリント |
| `Leafony_Template/sym-lib-table` | プロジェクト固有のシンボルライブラリ一覧。配布時点では未登録 |
| `Leafony_Template/fp-lib-table` | プロジェクト固有のフットプリントライブラリ一覧。`Leafony` を登録済み |
| `Leafony_Template/meta/` | テンプレート名・説明・アイコン・プレビュー画像 |

`leafony_template-cache.lib`、`lib/Leafony.dcm`、`lib/Leafony.bak` は旧形式のキャッシュ・説明・バックアップです。新規設定で登録するシンボルライブラリは `lib/Leafony.kicad_sym` です。`.kicad_prl` と `fp-info-cache` は個人設定・キャッシュであり、ライブラリ登録の対象ではありません。

## 1. KiCadとテンプレートを準備する

1. [KiCad公式ダウンロードページ](https://www.kicad.org/download/)から、利用するOS向けのKiCad 10.0系をインストールします。
2. 初回起動時は標準ライブラリを使用する設定を選びます。Linuxなどでライブラリが別パッケージの場合は、標準ライブラリもインストールしてください。
3. [リポジトリの入手手順](../README.md#ダウンロード)に従って、フォルダ全体を取得します。

以降のパスに含まれる `cad-template` は、実際のクローン先またはZIPの展開先に読み替えてください。

## 2. ユーザーテンプレートを登録する

1. KiCadのプロジェクトマネージャーを起動します。
2. **設定 → パスを設定…（Preferences → Configure Paths…）** を開きます。OSや表示言語によりメニュー表記は異なります。
3. `KICAD_USER_TEMPLATE_DIR` を、このリポジトリの **`KiCad` フォルダの絶対パス**に設定します。
4. 設定を保存します。テンプレート一覧に反映されない場合はKiCadを再起動します。

| OS | 設定値の例 |
| --- | --- |
| Windows | `C:/Users/your-name/Documents/cad-template/KiCad` |
| macOS | `/Users/your-name/Documents/cad-template/KiCad` |
| Linux | `/home/your-name/cad-template/KiCad` |

この変数には、`Leafony_Template` を含む親フォルダを指定します。必要な構造は次のとおりです。

```text
<KICAD_USER_TEMPLATE_DIR>/
└── Leafony_Template/
    ├── Leafony_Template.kicad_pro
    ├── Leafony_Template.kicad_sch
    ├── Leafony_Template.kicad_pcb
    ├── lib/
    ├── sym-lib-table
    ├── fp-lib-table
    └── meta/
        └── info.html
```

すでに別のユーザーテンプレートフォルダを利用している場合は、設定値を維持したまま、そのフォルダの下に `Leafony_Template` を丸ごとコピーしても利用できます。

テンプレートの探索場所は[KiCad公式マニュアル](https://docs.kicad.org/10.0/ja/kicad/kicad.html)の「Template locations」に記載されています。

## 3. テンプレートからプロジェクトを作成する

1. プロジェクトマネージャーで **ファイル → 新規プロジェクト…（File → New Project…）** を選びます。
2. テンプレート一覧から **Leafony Leaf** を選びます。必要に応じて一覧をユーザーテンプレートに絞り込みます。
3. **OK** を押し、作業用フォルダと新しいプロジェクト名（例：`my_leaf`）を指定します。
4. 作成された `my_leaf.kicad_pro` を開き、回路図とPCBをプロジェクトマネージャーから起動します。

テンプレートのファイルは新しいプロジェクトへコピーされ、主要なファイル名はプロジェクト名に置き換わります。`lib` フォルダとライブラリ一覧もコピーされます。保存先にはテンプレートの元フォルダとは別の場所を選んでください。

内容を見るだけなら、`Leafony_Template/Leafony_Template.kicad_pro` を直接開けます。自分のリーフを設計するときは、新しく作成したプロジェクトを編集します。

## 4. ライブラリを設定する

作成したプロジェクトで設定します。`${KIPRJMOD}` はKiCadが自動で設定する「現在のプロジェクトフォルダ」です。パス設定画面で追加・変更する必要はありません。

### シンボルライブラリ

配布時の `sym-lib-table` は空です。配置済みのシンボルは回路図内にも保存されていますが、ライブラリからの追加・参照には次の登録が必要です。

1. プロジェクトマネージャーから回路図エディターを開きます。
2. **設定 → シンボルライブラリを管理…（Preferences → Manage Symbol Libraries…）** を開きます。
3. **プロジェクト固有ライブラリ（Project Specific Libraries）** を選びます。
4. 「既存のライブラリを追加」から、作成したプロジェクト内の `lib/Leafony.kicad_sym` を選びます。
5. 登録内容を次の値に合わせ、有効にして保存します。

| 項目 | 値 |
| --- | --- |
| ニックネーム | `Leafony` |
| ライブラリパス | `${KIPRJMOD}/lib/Leafony.kicad_sym` |
| ライブラリ形式 | `KiCad` |

シンボルの選択画面で `Leafony:Leafony Bus` を検索し、表示されることを確認します。既存の `CN1` を使う場合、確認のためにもう1個配置する必要はありません。

### フットプリントライブラリ

`fp-lib-table` に登録済みのため、通常は追加設定不要です。PCBエディターの **設定 → フットプリントライブラリを管理…（Preferences → Manage Footprint Libraries…）** で、プロジェクト固有ライブラリを確認します。

| 項目 | 値 |
| --- | --- |
| ニックネーム | `Leafony` |
| ライブラリパス | `${KIPRJMOD}/lib/Leafony.pretty` |
| ライブラリ形式 | `KiCad` |

`Leafony:CN_F29_B29` が表示されれば設定できています。再登録する場合は、個別の `.kicad_mod` ファイルではなく `Leafony.pretty` フォルダを選びます。

ライブラリを含むプロジェクト全体を移動・共有すれば、上記の相対参照を維持できます。詳細は[KiCad公式「シンボルライブラリの管理」](https://docs.kicad.org/10.0/en/eeschema/eeschema.html#managing-symbol-libraries)を参照してください。

## 5. 設計を開始する

### テンプレートの初期値

以下は収録データの設定値です。製造先に指定する条件と照合してください。

| 項目 | 初期値 |
| --- | --- |
| 基板外形 | `Edge.Cuts` の最大寸法は23 × 20 mm。コネクタ側の幅20 mmに対し、左右に張り出しあり |
| 銅層 | 4層：`F.Cu` / `In1.Cu` / `In2.Cu` / `B.Cu` |
| 基板厚 | 0.8 mm |
| 接続部 | `CN1`、表裏各29接点（`F1`〜`F29`、`B1`〜`B29`） |
| 取り付け穴 | 直径2.05 mmの非めっき穴2個 |
| 最小配線幅・最小クリアランス | 0.1016 mm |
| `Default` ネットクラスの配線幅 | 0.127 mm |
| `Default` ネットクラスのビア径 / ドリル径 | 0.56 mm / 0.30 mm |

基板設定（Board Setup）で層構成、製造上の制約、ネットクラスを確認します。コネクタ領域には銅箔ゾーン禁止領域が設定されています。実際の外形・接点位置・穴位置はPCBデータを基準にしてください。

### 回路・基板を編集する

1. 使用するリーフのピン割り当てを確認し、回路図に部品と配線を追加します。Leafony busの接点番号と既存の信号名を確認しながら接続します。
2. 追加した部品にフットプリントを割り当て、回路図の電気的ルールチェック（ERC）を実行します。
3. **ツール → 回路図からPCBを更新…（Tools → Update PCB from Schematic…）** でPCBへ反映します。
4. 接続部と取り付け穴の位置、他のリーフとの部品干渉を確認し、部品配置・配線を行います。
5. 銅箔ゾーンを再充填し、デザインルールチェック（DRC）で未接続や製造ルール違反を確認します。
6. ガーバーとドリルファイルを出力し、製造先の指定と照合します。

ピン配置や製造データ作成の補足は、[Leafony公式「自作リーフ開発」](https://docs.leafony.com/pcb/)を参照してください。

## よくある問題

| 症状 | 確認すること |
| --- | --- |
| `Leafony Leaf` がテンプレート一覧に出ない | `KICAD_USER_TEMPLATE_DIR` が `Leafony_Template` の親フォルダを指し、その下に `Leafony_Template/meta/info.html` があるか確認します。設定変更後は一覧を開き直すかKiCadを再起動します。 |
| ファイル形式が新しすぎると表示される | KiCad 10.0系で開いているか確認します。 |
| `Leafony` シンボルライブラリが見つからない | 作成したプロジェクトのシンボルライブラリ一覧に `Leafony` を登録します。配布時の一覧には登録されていません。 |
| `Leafony:CN_F29_B29` が見つからない | `lib/Leafony.pretty` と `fp-lib-table` がプロジェクト内にあり、ニックネームとパスが上記設定と一致しているか確認します。 |
| `power` などの標準シンボルが見つからない | KiCadの標準ライブラリがインストールされ、グローバルライブラリ一覧で有効になっているか確認します。 |
| 別のPCへ移したらライブラリを参照できない | `lib` フォルダもコピーし、ライブラリのパスが元のPCの絶対パスではなく `${KIPRJMOD}` を使用しているか確認します。 |

## ライセンス

MIT

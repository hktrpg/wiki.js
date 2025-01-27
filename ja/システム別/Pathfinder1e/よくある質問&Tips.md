---
title: よくある質問&Tips
description: よくありそうな質問と便利なテクニックをまとめています
published: true
date: 2021-09-14T12:32:49.941Z
tags: 
editor: markdown
dateCreated: 2021-09-11T02:48:19.206Z
---

# PathfinderRPG1e よくある質問&Tips

最終更新：2021/09/14
編集時のバージョン FoundryVTT 0.8.9、Pathfinder1e 0.79.1

## 日本語化関係

### クラスや呪文などの辞典が日本語化されない
日本語化（PF1）のMOD以外に [Babele](https://gitlab.com/riccisi/foundryvtt-babele) というMODが必要です。
 [Babele](https://gitlab.com/riccisi/foundryvtt-babele) を導入しても一部の辞典のデータに英語のままの項目があるのは仕様です。

## システム関係

### アクターとトークンは何が違うのか？

FVTTのアクターリストにある状態をアクターと呼び、そのアクターをシーンにドロップして駒として出すとトークンと呼びます。PCやネームドNPCとしてアクターとトークンを同一として扱いたい場合は、アクターシートを開きウィンドウ上部にあるPrototype Tokenを押し**トークン設定**を呼び出し設定を行います。トークン設定のキャラクタータブの**アクターデータの共有**にチェックを入れることで、アクターとトークンのデータは同期されるようになります（例えばトークンのHPを減らすとアクターのHPも減っている）。ただしトークンの視覚を編集してもアクターの視覚は元のままですので注意しましょう。

次に**アクターデータの共有**のチェックを外しての運用ですが主にエネミーとしてトークンを複数出す場合に使用します。チェックを外したトークンを複数配置すると、それぞれのトークンは独立したHPを持つ駒になります。もし共有にチェックが入ったままだと、一人がダメージを受けると他の同一トークンもダメージを受けてしまいます。

### トークンの名前やHPバーを表示したい

アクターシートを開きウィンドウ上部にあるPrototype Token（トークン）を押すか、トークンを右クリックして歯車アイコンを押し**トークン設定**を呼び出します。トークン設定のキャラクタータブの**ネームプレート**に表示したい名前を、**表示方法**にネームプレートが表示される条件を設定します。HPバーはリソースタブの**表示方法**に表示される条件を、**バー1設定**は`attributes.hp`を選択します。最後に**トークンを更新**を押すと保存されます。

### トークンを移動しようとしても出来ない

**一時停止**が有効になっているか、左に並んでいるアイコンが**トークン操作→トークン選択**になっていない可能性があります。

### トークンの移動ルートを決めて移動させたい

トークンをドラッグして移動させる時に、曲がり角など方向転換したいマスで**右クリック**するとその地点が記憶されます。

### Foundry VTTでアイテム以外もアイテムというのはなぜ？
Foundry VTTではアクターに追加するデータ群をアイテムと呼びます。PathfinderRPG1eではクラス、種族、呪文、アイテム、クラス特徴、特技など全てデータ上はアイテムとなります。

### トークンのHPがダメージや回復で増減するのを簡単に処理したい

アクターシートで生成した攻撃を実行するとチャットに**ダメージの適用ボタン**が表示されています。ダメージを与えたいトークンを選択（ターゲット機能ではない）した状態でこのボタンを押すとダメージ分だけHPが減ります。またキュア・ライト・ウーンズなどを使うと**回復の適用ボタン**があるのでこれも同じように使うことが出来ます。トークンは複数選択出来るのでファイアーボールなどで複数の対象に一度にダメージ処理を行うことも出来ます。

トークンを右クリックすると表示されるHP欄は `+5` や `-3` などと入れるとHPを増減させることが出来るので覚えておくと便利かもしれません。この機能はアクターシートの所持金欄などの数字を扱う欄の一部でも使用出来ます。

### アクターシートで生成した攻撃や呪文以外のロールでダメージ適用ボタンや回復適用ボタンを表示させたい

普通のダイスロールは `/roll` や `/r` で行いますがこの部分を次のように変更すると適用ボタンが表示されるようになります。  
ダメージ：`/damage` または `/d`  
回復：`/heal` または `/h`

### トークンにダメージを適用させる時にダメージ減少の分だけ減らしたい、または脆弱性などで増やしたい

チャットのダメージの適用ボタンを**shiftキーを押しながらクリック**するとウィンドウが現れるので、**減少値**に減らしたい分の数字を入れて適用すると減らしたダメージが適用されます。ダメージを増やしたい場合は `-5` のように負数にすると増やすことが出来ます。

アクターシートの能力値タブの**ダメージ減少**に`10/冷たい鉄`のように設定しておくと、上記のウィンドウを出した際に`10/冷たい鉄`の項目が表示され、その項目をクリックすると**減少値**にその数字が送られる機能もあります。

複数のダメージ減少を設定する時は、`10/冷たい鉄;5/銀`のように`;`記号で区切ってください。

### 死亡したトークンにもターンが回ってくるのでスキップしたい

イニシアチブ表の設定で**敗北者をスキップ**にチェックを入れる。

### パーティの視覚の共有機能について

権限が**観察者（Observer）以上**のアクターの視界が共有されるようになります。

### システム設定のツールチップで手に持っているアイテムなどを非表示にしても表示される

この設定は権限が**なし、限定的（Limited）、観察者（Observer）** のトークンのデータをプレイヤーが見れるかどうかの設定になります。権限が**所有者（Owner）** のトークンやGM視点だとツールチップは全て表示されます。権限が**観察者（Observer）** のトークンはデータは非表示に出来ますがアクター名は非表示にしても表示されます。ただしポートレートのみ権限やGMに関わらず非表示になります。

**ツールチップを無効にする**にチェックを入れると権限やGMに関わらず全て非表示にできます。

## アクターシート関係（全般）

### アクターを新規作成するときのcharacterとnpcの違いは？

PCを作成する時はcharacterを選択してください。アクターをnpcで作成すると一部の自動計算機能が省略されてしまいます。例えば重装鎧に習熟していない状態でフルプレートを装備すると、characterが攻撃した場合は判定ペナルティを受けますがnpcにはそれがありません。またnpcは専用のNPCLiteシートや戦利品用のNPCLootシートに変更が出来ます。

### アクターに追加したデータの内容を変更したい
そのデータの右のアイコンの中に**アイテム編集ボタン**があるのでそこから編集できます。データの列にカーソルを合わせて右クリックでもアイテム編集が開けます。

### アクターシートにあるアイテムや能力のデータを変更したのに変わっていない

内容を変更してすぐに閉じてしまうと内容が保存されていないことがよくあります。変更後は名前などを選択してエンターキーを押すとほぼ確実に保存されます。

### デフォルトとは違う表示のキャラクターシートを見かけたんだけど？

NPCでアクターを作成するとNPCLiteシートという簡易表示のものやNPCの所持品を戦利品として分配するためのNPCLootシートに変更が出来ます。シートの種類を変更するにはアクターシートを開きウィンドウ上部ある**シート設定**というボタンを押すと設定ウィンドウが出るのでそこで変更できます。

他にも[Pathfinder 1e Alt Sheet](https://gitlab.com/zenvy/foundryvtt-pf1-alt-sheet)というMODでシートの見た目の変更が出来ます。MODを有効にするとシート設定ウィンドウに**Alternative character sheet**が追加されています。デフォルトのシートと機能に違いはほとんどありません。このMODはNPCのシートも**Alternative NPC character sheet**に変更できます。


### 種族の設定

**種族辞典**を開き取得したい種族をアクターシートにドロップすると設定出来ます。種族辞典には通常の種族特性に加え、代替種族特性や適正クラス・オプション、年齢や身長体重も記載されています。種族特性による能力値の修正やセーヴや技能に対するボーナスなどは種族データの変更タブにて設定済です。**ただし人間、ハーフエルフ、ハーフオークの選択した能力値へのボーナスは自身で設定する必要があります**。変更タブの設定方法は**バフの設定**で解説していますのでそちらを参照してください。

変更タブで設定できないような特性は、アクターシートの特徴タブの種族特徴に自身で追加してください。

疑似呪文能力は**アクターシート関係（呪文）**の**疑似呪文能力の設定**で解説していますのでそちらを参照してください。

### 能力値の設定

アクターシートの能力値タブで各能力値の**合計**の列の数字を書き換えるか、下部の**ポイント購入計算機**で設定ができます。合計の列は種族や他の能力で能力値が増えていても、クリックするとベースの能力値が表示される仕組みになっています。

### クラスの設定

**クラス辞典**を開き取得したいクラスをアクターシートにドロップします。するとクラスを追加というメニューが表示されるので通常か省略のどちらかを選びます。通常ではヒット・ダイスのロールと適正クラス・ボーナスを選ぶメニューが表示されます。省略ではヒット・ダイスと適正クラスは飛ばされるので、後に手動で編集する必要があります。

### 手動でHPや適正クラス・ボーナスを設定するにはどうするのか

変更したいクラスを編集で開き、詳細タブの**ヒット・ポイント**に任意の数字を入力する、または**適正クラス・ボーナス**で取得したい内容の数字を変えることで変更できます。

### 技能の設定

アクターシートの技能タブの各技能のランクに割り振る技能ポイントを入力します。芸能、職能、製作技能は＋ボタンで新しく追加し技能名に特定の種類を設定します

技能のチェック欄の略称は CS（クラス技能）、ACP（鎧による判定ペナルティ）、RT（習得時のみ）を表しています。

### クラス特徴で新たにクラス技能が増えたので設定したい

該当するクラスを編集で開き、詳細タブの**クラス技能**のチェックボックスをオンにするとクラス技能になります。

### 所持品や特技、クラス特徴をアクターに追加したい

基本的にどのデータも辞典からアクターシートにドロップすることで追加出来ます。クラス特徴に限り、クラス・レベルを上げることで取得できるものは**該当レベルになれば自動的に追加**されます。ただし激怒パワーなどの自分で選ぶものは自動的に追加されないので手動で追加してください。

### 武器や鎧を高品質にしたり+1強化ボーナスを設定したい

設定したい装備をアイテム編集で開き、詳細タブの**高品質**をチェックしたり**強化ボーナス**の項目に数字を入力します。武器にこの設定を行った後に**攻撃生成**を行うと、武器攻撃にも内容が反映されています。

### 巻物、ポーション、ワンドを作成したい

**呪文辞典**からアクターの**所持品タブ**にドロップすると上記のアイテムの作成ウィンドウが出ます。

### アクターに明かりや夜目、暗視を設定したい

アクターシートを開きウィンドウ上部にあるPrototype Tokenを押し**トークン設定**を出します。トークン設定の視覚タブの**視覚制限を有効化**にチェックを入れます。**夜目**ならチェックを入れ、夜目の倍率を設定します。**明かり**なら薄暗い照明と明るい照明に距離を入力します。**暗視**なら視覚[薄暗い]と視覚[明るい]に距離を入力します。

アクターシートではなくトークンを右クリックして歯車アイコンからトークン設定を呼び出し視覚の設定をすることも出来ますが、**トークンに設定した視覚はアクターシートに反映されません**ので注意してください。トークンから行った視覚設定はそのシーン内でのみ有効です。

### アイテムを他のアクターに渡したり、背負い袋などの収納アイテムに入れる方法

所持品のプレゼントアイコンの**アイテムを渡す**をクリックするとアクターや収納アイテムにアイテムを移動出来ます。ただし渡したいアクターの権限によっては一覧に表示されません。収納アイテムをアイテム編集で開き、移動したいアイテムをドロップすることで移動も出来ます。

### 背負い袋（高品質）やアントホールなどの運搬能力増加の設定

所持品タブの下の**運搬筋力ボーナス**に数字を入れると運搬能力に関してだけ筋力が高く計算されます。**運搬倍率ボーナス**に数字を入れると運搬能力がその数字だけ倍化します（1で2倍になる）。

### バフの設定

アクターシートのバフタブでは状態異常の設定やバフの設定が行なえます。状態異常をオンにすると、**自動的にペナルティが計算され判定などに適用**されます。よく使われるバフは**一般的なバフ辞典**にあるのでドロップして追加し、チェックすることでバフを有効に出来ます。シールド・オヴ・フェイスなどの一部のバフは術者レベルを設定することで効果が変動するようになっています。

自分で新しくバフを作る場合は**＋増やす**を押して新規作成してください。新しいバフをアイテム編集で開き名前と説明に内容を入力します。

#### 詳細タブの設定
- **トークンから隠す：** チェックを入れると、シーンのトークンにアイコンが表示されなくなります。  
- **持続時間：** 将来的なアップデートのための項目で、現在は機能していません。  

#### 変更タブの設定
- **フラグ：** 各項目にチェックを入れると、このバフを有効にしたときに効果が発揮されます。  
- **変更：** セーヴや能力値などを増減するための設定が行なえ、右端の＋を押すと新しい項目が追加されます。  
- **式：** **演算子**が `＋` であれば入力した数字が加算（式がマイナスの場合でも＋を使用する）され、`＝` であれば式の数字に変更されます。**演算子**が `S` の場合は、式の箇所が Edit になりスクリプトを記述することが出来ます。  
- **目標：** 式の数字をどの対象に適用するかを選びます。  
- **修正値：** ボーナスの種類を選びます。その右は同じボーナスが合った場合の優先順位を設定出来ます。  
- **文脈メモ：** 特定のアクションを取った時にチャット欄にメッセージを表示する機能です。＋を押して項目を追加し、**メモ**に表示したいメッセージを入力、**目標**にそのメッセージを表示したい対象を選択します。例えばエルフであれば**メモ**に`心術呪文と心術効果に対するセーヴィング・スローに＋2の種族ボーナス`と入力し、**目標**に`全てのセーヴィング・スロー`を選択するとセーヴをロールした際にメモに設定したメッセージが表示されるようになります。

バフの変更タブの設定項目はアイテムや特技、クラス能力などにも備わっていますので恒常的な修正はそちらで加えることも出来ます。

### エンラージ・パースンなどのサイズ変更があるバフの設定
バフだけではサイズ変更を自動化することは出来ないので、能力値タブの**サイズ**を手動で変える必要があります。サイズを変更すると攻撃ロールとアーマー・クラスへの修正値は自動的に計算されます。

エンラージ・パースンの場合では、バフで`筋力+2サイズ・ボーナス`と`敏捷力-2サイズ・ペナルティ`を設定し、能力値タブの**サイズ**を`大型`に変更します。

### 種族特性を代替種族特性に変更したい

まず通常通りアクターシートに種族をドロップして設定します。概要タブの種族を編集で開き、変更タブを見ると種族によりますがいくつかの変更や文脈メモが設定されていると思います。これらの項目のうち代替種族特性で置き換えられるものを**ゴミ箱アイコンで削除**し、代替種族特性で追加される項目を変更や文脈メモに追加します。変更タブの設定方法は**バフの設定**で解説していますのでそちらを参照してください。

もし変更タブの内容に適さない特性があれば、アクターシートの特徴タブの種族特徴に追加します。

### 使い魔や動物の相棒の作成

基本的にはPCと同じように作成するのですが、アクターシートのクラスのところに**種族HD辞典**に記載されている種族を設定します。

### レベルアップの方法

経験点が貯まるとクラスのところに**Level Upアイコン**が出現するのでそれを押してください。ヒット・ダイスのROCと適正クラス・ボーナスの選択が出来ます。決定するとチャット欄にヒット・ダイスのロール結果やLvUpによるクラス特徴の取得、特技や能力値の追加のお知らせが出ます。

Level Upアイコンを使用せずに、クラスをアイテム編集で開きレベルの数字を直接変更することでもレベルアップが可能です。この場合は詳細タブでヒットポイントと適正クラス・ボーナスを自分で設定する必要があります。

### 自分でアイテムや特徴を作ったのでアイコンを設定したい

アイコンを設定するにはGMであるか**コンフィグ設定→コア設定→権限の設定**でファイル・ブラウザの使用の権限を与えられている必要があります。アイコンを変えるにはそのアイテムなどをアイテム編集で開きアイコンの部分をクリックします。Pathfinder1eシステムでよく使われているアイコンは `systems\pf1\icons` 内に種類ごとにフォルダに分けられています。

## アクターシート関係（攻撃）

### 武器攻撃を設定したい

まずアクターに武器をドロップし装備させます。その武器のアイテム編集を開き、詳細タブの下部にある**攻撃生成**をクリックすると、**（武器名）の攻撃を生成**というメッセージがポップアップします。戦闘タブにその武器名の攻撃が作られているので**剣のアイコン（攻撃を実行）**をクリックすると攻撃ウィンドウが出ます。このウィンドウには攻撃時のオプションが表示され、攻撃ロールやダメージに一時的なボーナスを与えたり強打による修正を自動的に加えることも出来ます。
- **攻撃ロールダイス：** 2個振って高い目`2d20kh`や悪い目`2d20kl`を採用する時に利用します。
- **攻撃ロールボーナス：** 数字やダイスを入力してボーナスやペナルティを攻撃ロールに適用します。遮蔽がある時に活用してください。
- **ダメージ・ボーナス：** 数字やダイスを入力してボーナスやペナルティをダメージロールに適用します+
- **その他：** ヘイストによる追加攻撃、近接攻撃では強打、遠隔攻撃では致命的な狙い、束ね射ち、速射、近距離射撃の使用時にチェックを入れると攻撃に適用されます。
- **ダメージ能力値：** 片手から両手持ち替えて筋力が1.5倍になる時などに変更します。
- **手に持っている：** この項目を変更すると強打使用時のダメージが変更されます。筋力などダメージ能力値の加算倍率は変わりません。
- **ロールモード：** ロール結果を公開するかどうか選択できます。

設定が終わったら**一回の攻撃**をクリックすると、攻撃ロールとダメージロールが行われチャットにロール結果が表示されます。もし基本攻撃ボーナスが高く複数回攻撃出来るときや、ヘイストにチェックを入れて追加攻撃をしたい場合は**全力攻撃**にしてください。

### 肉体攻撃を設定したい
武器のように攻撃生成が行えないので自分で攻撃を設定する必要があります。例としてウルフの噛みつきの設定を上げておきます。

戦闘タブの肉体攻撃の**＋増やす**をクリックし新しい攻撃を追加したらアイテム編集で開き以下のように設定します。
- **名前：** 噛みつき
- **主要攻撃：** チェックを入れる
- **攻撃の種類：** 肉体攻撃
- **発動コスト：** 1、攻撃アクション
- **距離：** 近接
- **アクションの種類：** 近接武器攻撃
- **攻撃名：** 噛みつき
- **クリティカル可能域：** 20
- **クリティカル倍率：** 2
- **攻撃能力値：** 筋力
- **ダメージ能力値：** 筋力、×1
- **ダメージの式：** ＋ダメージの式を追加をクリックして項目追加。**ダメージの式**に`1d6`を、その右は見切れていますが**ダメージ・タイプ**なので`殴打／斬撃／刺突`とします。

これで設定完了です。

肉体攻撃で攻撃ウィンドウを呼び出すと**その他**の項目に主要攻撃が追加されています。二次的攻撃の場合はチェックを外してください。二次的攻撃でしか使わないのであれば、アイテム編集で**主要攻撃**のチェックを外すと楽です。

### 呪文で使うために近接接触攻撃や遠隔接触攻撃を設定したい
武器のように攻撃生成が行えないので自分で攻撃を設定する必要があります。

戦闘タブの武器攻撃の**＋増やす**をクリックし新しい攻撃を追加したらアイテム編集で開き以下のように設定します。
- **名前：** 近接接触攻撃 または 遠隔接触攻撃
- **攻撃の種類：** 肉体攻撃
- **発動コスト：** 1、フリーアクション
- **アクションの種類：** 近接呪文攻撃 または 遠隔呪文攻撃
- **攻撃名：** 近接接触攻撃 または 遠隔接触攻撃
- **クリティカル可能域：** 20
- **クリティカル倍率：** 2
- **攻撃能力値：** 筋力 または 敏捷力

これで設定完了です。

### 攻撃のダイスロールの修正値が合っているか確かめたい

チャットに表示されたダイスロールのダイスアイコンにカーソルを合わせるかクリックすると、基本攻撃ボーナスや筋力などの修正値がいくら足されているのか、またどんなペナルティが入っているのか詳細が表示されます。

### 基本攻撃ボーナスが6以上だったり爪が2つあるので追加攻撃を設定したい。

基本攻撃ボーナスが6以上の状態で武器から攻撃生成を新規に行うと、自動的に追加攻撃が設定された武器攻撃が生成されます。

手動で追加攻撃を増やしたい場合は攻撃をアイテム編集で開き、詳細タブの**＋追加攻撃を追加**をクリックし項目を追加します。**攻撃ボーナスの式**には基本攻撃ボーナスによる追加攻撃なら `-5[基本攻撃ボーナス]` と設定し、爪などで攻撃ボーナスが変わらないのであれば空白のままで問題ありません。**名前**は入力したものがチャットのダイスロールに表示されます。設定が完了すれば攻撃時に**全力攻撃**を選択すると追加攻撃が行なえます。

### 《武器熟練》の設定

武器攻撃をアイテム編集で開き、詳細タブの**攻撃ロールボーナス**に `1[武器熟練]` と入れます。実際に攻撃を行うとチャットに表示される攻撃のダイスロールの詳細に武器熟練で+1されているのが確認できます。複数の修正値を設定したい時は、`1[武器熟練]+1[上級武器熟練]` のように記述してください。

`[ ]`はそのボーナスが何から来ているのか分かりやすくするために表示するための機能で、入力しなくても動作に問題はありません。

### フレイミングなどの常時発動している追加ダメージを武器攻撃に設定したい

武器攻撃をアイテム編集で開き、詳細タブの**＋非クリティカルダメージボーナスの式を追加**をクリックします。追加された項目の**ダメージの式**に `1d6[フレイミング]`、**ダメージ・タイプ**に `火炎` と入力します。

### 急所攻撃などの特定の状況で増える追加ダメージを武器攻撃に設定したい

武器攻撃をアイテム編集で開き、条件付き修正タブの**＋条件を追加**をクリックします。追加された項目のチェックボックスは空のまま**名前**に急所攻撃と入れ、**＋効果を追加**をクリックします。**式**に `1d6[急所攻撃]`と入力し、以降の項目は `ダメージ、全て、無種別、非クリティカルダメージボーナスの式` を選択します。設定が終われば攻撃を行う時に出るウィンドウに**条件付き修正：急所攻撃**が増えているのでチェックを入れて攻撃を行うと、急所攻撃が適用されたダイスロールが実行されます。

レベルが上がるたびに急所攻撃の追加ダメージを変更するのが面倒であれば、**式**に`(ceil(@classes.rogue.level / 2)d6)[急所攻撃]`と入れるとローグのレベルが上がるたびに自動的にダイスが増えるようになります。`@classes.rogue.level`はクラスレベルを取得するための変数で`rogue`の部分をクラスタグと呼びます。、他のクラスのタグに変更することでニンジャのクラスレベルを参照するように出来たりします。クラスタグはクラスをアイテム編集で開き、詳細タブの**ADVANCE：タグ**のところに記載してあります。

### 《狂乱集中》の設定

武器攻撃をアイテム編集で開き、条件付き修正タブの**＋条件を追加**をクリックします。追加された項目のチェックボックスは空のまま**名前**に狂乱集中と入れ、**＋効果を追加**をクリックします。**式**に `-@powerAttackPenalty` と入力し、以降の項目は `攻撃ロール、攻撃1、無種別、通常` を選択します。設定が終われば攻撃を行う時に出るメニューに**条件付き修正：狂乱集中**が増えているので強打と一緒にチェックを入れて攻撃を行うと、強打のペナルティが軽減されたダイスロールが実行されます。

### 弓などの遠隔武器で使う矢弾を自動消費するように設定したい

攻撃生成した遠隔攻撃をアイテム編集で開き、リンクタブの項目を**矢弾**にします。所持品にある使用したい矢弾をリンクタブにドロップすると登録が行われ、攻撃するたびに矢弾を消費するようになります。

矢弾をリンクした状態で攻撃を行うと攻撃ロール結果に**矢弾の回収**が表示されるようになります。

### 特殊能力のチャージ数を他の特殊能力で自動消費するように設定したい

例としてパラディンの癒しの手を2回消費して正のエネルギー放出を使う設定は次のように行います。癒しの手をアイテム編集で開きリンクタブの項目を**チャージ**にし、正のエネルギー放出をリンクタブにドロップして登録します。次に正のエネルギー放出をアイテム編集で開き、詳細タブの**自動的にチャージを引く**の下の数字を2に変更します。

## アクターシート関係（呪文）

### 呪文の設定

アクターシートの設定タブの呪文書の使用の**Primary**（複数の呪文クラスがあれば他も）にチェックを入れます。すると呪文タブが表示されるので移動し、右上の方にある**設定ボタンに小さい設定ボタンが2つくっついているアイコン**を押すと折りたたまれたメニューが表示されます。そのメニューの**呪文発動クラス**と**呪文発動能力値**を設定し、、**スペルスロットの自動計算**、**初級呪文/祈りの使用**のチェックとその下の術者の呪文発動タイプと呪文数の成長速度（低中高）に適切なものを選びます。秘術呪文失敗確率があるクラスならば**秘術呪文失敗確率**のチェックボックスにチェックを入れます。あとは**呪文辞典**や**呪文閲覧**から使いたい呪文をドロップするとリストに追加されます。

#### 呪文の成長速度一覧
- **高：** クレリック、ドルイド、オラクル、サイキック、シャーマン、ソーサラー、ウィッチ、ウィザード
- **中：** アルケミスト、バード、ハンター、インクィジター、インヴェスティゲーター、メイガス、メスメリスト、オカルティスト、スカルド、スピリチュアリスト、サモナー
- **低：** アンティパラディン、ブラッドレイジャー、ミーディアム、パラディン、レンジャー（呪文をクラス・レベル1で取得しないクラスは呪文の設定で**クラスレベル修正**を入力する必要があります）

### 疑似呪文能力の設定

アクターシートの設定タブの呪文書の使用の右端の **Spell-Likes** にチェックを入れます。呪文タブが表示されるので移動し、Spell-Likesタブの右上の方にある**設定ボタンに小さい設定ボタンが2つくっついているアイコン**を押すと折りたたまれたメニューが表示されます。疑似呪文能力の術者レベルがヒット・ダイス依存であれば**呪文発動クラス**にヒット・ダイスと設定し、そうではなく値が決まっているのであれば**術者レベル：術者レベルボーナスの式**にその値を入力します。**呪文発動能力値**を魅力にし、**秘術呪文失敗確率**、**スペルスロットの自動計算**、**任意発動型**のチェックを外します。あとは呪文辞典や呪文閲覧から使いたい呪文をドロップするとリストに追加されます。

### 領域や秘術系統で増えるスロットの設定

呪文タブの**領域スロット数**を`1`に変更します。領域呪文に設定したい呪文のアイテム編集を開き、詳細タブのその他にある**領域/系統**にチェックを入れます。するとその呪文の準備数のところに手のアイコンが出ているので、その状態で回数を増やしてもスロットに影響しなくなります。

### 呪文スロット能力値修正（特徴由来）とは何か？

ティーフリングやイフリットなどの呪文に関してだけ能力値が高いかのように扱う時に入力する項目です。呪文数の自動計算で参照されますが、セーヴィングスローの難易度は自動計算されないようです。

### 辞典から呪文をドロップして覚えさせたが違う呪文レベルに表示されている

呪文をドロップしたときにクラスによって適切な呪文レベルに表示する機能があるのですが、いつの間にか機能しなくなっているようです。手動で変更するには該当する呪文をアイテム編集で開き、詳細タブの**呪文レベル**を変更すると反映されます。

### 呪文の準備数や使用数が覚えのない数字になっている

各呪文の準備数や使用数の上でマウスホイールを使うと数字が増減する機能があるのでそれが暴発した可能性が高いです。呪文は多くなるとスクロールする機会が多いので気を付けましょう。[Spellcaster utility for PF1](https://github.com/SvenWerlen/fvtt-spellcaster-utility-pf1)というMODのマクロを使うことで安全に準備数を設定することも出来ます。

### 呪文熟練で特定の系統だけセーヴィングスローの難易度を上げたい

現在システムが対応していませんので代替手段を2つ上げておきます。  
1. 呪文をアイテム編集で開き、詳細タブの**難易度への修正**を変更し各呪文ごとに難易度を上げる。該当する呪文の数だけアイテム編集する必要があるのが難点です。
2. 呪文熟練などの該当能力をアイテム編集で開き、変更タブの文脈メモの＋を押し項目を追加します。メモには**召喚術のDC+1**のように記述し、目標には**呪文：効果**を選びます。すると呪文を使用すると効果メモとして先程の**召喚術のDC+1**が表示されるようになります。 全ての呪文に表示されるようになるのが難点です。

### 呪文修正特技を適用した呪文の設定

まず呪文修正特技を適用したい呪文を**アイテム複製ボタン**で複製します。複製した呪文をアイテム編集で開き、分かりやすいように名前に呪文修正特技の名称を付けます。詳細タブの**呪文レベル**を修正後の呪文レベルに変更し、**呪文レベルへの修正**に上げた呪文レベル分だけマイナスで入力します。これをしておかないとセーヴ難度が呪文レベル依存で計算されるため高くなってしまいます。《呪文レベル上昇》特技の場合は、**呪文レベルへの修正**を入力する必要はありません。


## 辞典関係

### 辞典のデータが多すぎて探しにくい

右下の閲覧機能（呪文閲覧や特技・クラス特徴閲覧）を利用してください。呪文閲覧ではクラスや呪文レベルでの絞り込みが出来ます。特技・クラス特徴閲覧ではクラス特徴にクラスとタグが設定されているのでそれで絞り込みが出来ます。

### Bestiary辞典のアクターデータが正しくない

データベースからアクターデータへの変換をプログラムで処理しているため間違っていることが多いです。使用する場合は一度アクターデータに目を通した方がいいでしょう。

### 怪物辞典閲覧を開くのに時間が掛かる

データ数が多いのと一部の項目の処理にエラーが出るため時間が掛かります。アップデートで改善されるのを期待しましょう

### 一部のクラスの主要なクラス特徴が抜けている

サムライの上級決意などレベルアップで自動的に取得する特徴にも関わらず抜けているデータがあります。それらのデータはクラス辞典の各クラスの説明タブに記載していますので、そちらで確認してください。

### 一部のデータが辞典から抜けている

データ数が非常に多いため辞典から抜けているデータもあります。また特技辞典はコアルールの特技しか実装されていない状態だったりします。

日本語化されていませんがアーキタイプや様々なデータを追加するMODがありますのでそちらを利用してください。
- [Pathfinder 1e Archetypes and Abilities](https://github.com/baileymh/pf1e-archetypes)
- [Pathfinder 1e Content](https://github.com/baileymh/pf1e-content)

### 一部のクラス特徴（罠感知など）の修正値が正しく適用されない

罠感知などの複数のクラスに同じ特徴が存在し、クラス・レベルを参照して効果が変わる特徴の修正値が正しく計算されない状態になっています。例えば罠感知をアイテム編集で開き変更タブを見ると、文脈メモに `+[[floor(@classes.rogue.level/3)]] vs. traps` と書かれています。複数のクラスに存在するにも関わらずローグのレベルを参照するよう記述されているので、他のクラスでは正しく動作していません。これは変数の `@classes.rogue.level` の `rogue` の部分を自身のクラスタグに変更することで直すことが出来ます。自身のクラスタグの確認は、クラスをアイテム編集で開き詳細タブの**ADVANCE：タグ**に書かれています。バーバリアンであれば `barbarian` となっていますので `@classes.barbarian.level` にすることで罠感知が正しく適用されます。

## MOD関係

PathfinderPRG 1e用の様々なMODが作られていますのでご紹介します。

- **Pathfinder 1e Alt Sheet：**
https://gitlab.com/zenvy/foundryvtt-pf1-alt-sheet  
シートの見た目を変えるMODです。アクターシートを開いてウィンドウ上部のシート設定から Alternative character sheet に変更してください。

- **Spellcaster utility for PF1：**
https://github.com/SvenWerlen/fvtt-spellcaster-utility-pf1  
その日の呪文管理に便利なマクロです。Spellcaster Macros辞典が追加されているので、中の **Cast Spells** と **Prepare Spells** をホットバーにコピーして使用します。トークンを選択した状態で **Cast Spells** を使用すると呪文が使用が、**Prepare Spells** を使用すると呪文の準備が出来ます。呪文を使用出来るクラスが複数ある場合は、マクロ編集で開いて `primary` の部分を `secondary` などに変更することで対応出来ます。
呪文タブで準備数を設定する時にマウスのホイールスクロールでの増減が暴発する人におすすめです。

- **Koboldworks - Little Helper for PF1：**
https://gitlab.com/koboldworks/pf1/little-helper  
様々な細かい調整が行われるMODです。詳細はサイトで確認してください。

- **Koboldworks - Item Hints for Pathfinder 1e：**
https://gitlab.com/mkah-fvtt/pf1/item-hints  
所持品、特徴、呪文、バフなどの名前の後ろに特性が表示されるようになります。

- **MKAh/PF1/Buff Activator：**
https://gitlab.com/mkahvi/fvtt-micro-modules/-/tree/master/pf1-buff-activator  
呪文や能力を使用時にバフをオンにするMODです。あらかじめオンにしたいバフを作成しておき、起点となる呪文や能力の詳細タブに**Activate buff**が増えていますのでそこで設定します。

- **MKAh/PF1/Container Contents：**
https://gitlab.com/mkahvi/fvtt-micro-modules/-/tree/master/pf1-container-contents  
収納アイテムをアイテム編集で開かなくてもクリックすると内容物が見れるようになります。

- **Pathfinder 1e Archetypes and Abilities：**
https://github.com/baileymh/pf1e-archetypes  
上級クラスやアーキタイプ、それらのクラス特徴を追加する辞典MODです。

- **Pathfinder 1e Content：**
https://github.com/baileymh/pf1e-content  
非常に多くのデータを追加する辞典MODです。

- **PF1e UE Treasure Generator：**
https://github.com/websterguy/pf1e-treasure-generator  
Ultimate Equipmentの宝物の生成が行えるMODです。
アイテムタブの下部に**Generate Treasure**が追加されているのでそこから起動します。

- **SBC | PF1 Statblock Converter：**
https://github.com/Lavaeolous/PF1-StatBlock-Converter-Module  
テキストデータからアクターを作成します。

## よく使う変数

参照先：https://furyspark.gitlab.io/foundryvtt-pathfinder1-doc/advanced/formula-data/
FVTT内のトークン設定のリソースタブのバー1設定で様々な変数が確認できます。

- `@classes.クラスタグ.level`  
クラスレベルを参照、クラスタグはクラスの詳細タブの**ADVANCED：タグ**で確認可能

- `@abilities.{str,dex,con,int,wis,cha}.mod`  
能力値修正を参照、筋力修正値を参照するなら`@abilities.str.mod`となります

- `@attributes.hd.total`  
ヒット・ダイス数を参照

## よく使う関数

- `sizeRoll` 武器攻撃のダメージ
例：`sizeRoll(1, 8, @size)`
最初の数字は武器ダメージのダイスの個数、2番目の数字はダイスの種類を表します。
`@size`はアクターのサイズを自動で取得し、そのサイズによってダイスの数と種類が自動的に変化します。

- `floor` 切り捨て 
例：`1 + (floor((@classes.druid.level - 4) / 2))`
ドルイドの自然の化身の使用回数は4レベルで1回、以降は2レベルごとに1回増える。

- `ceil` 切り上げ
例：`(ceil(@classes.cleric.level / 2))d6`
クレリックのエネルギーの放出は奇数レベル毎に1d6増える。

## ダイスロール

- `2d20kh`
d20を2個ロールして高い目を採用

- `2d20kl`
d20を2個ロールして低い目を採用


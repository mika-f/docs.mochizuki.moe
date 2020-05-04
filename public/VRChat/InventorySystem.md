# VRChat Inventory System for Unity 2018

Unity 2018.3 以降、 VRChat 2020.1 以降 (Unity 2018 対応版以降) で使用できる、C# スクリプトを使わないインベントリシステムです。  
ここでは、付属の専用のエディター拡張を使用した導入方法を説明します。

## はじめに

このインベントリシステムを使うには、以下のものが必要です。

- VRChat Inventory System for Unity 2018 v0.1.0-beta.1 以降
- お好きな 3D モデル (アバター)
- 出し入れしたい 3D モデル (もしくはその他のなにか)

ここでは、 v0.1.0-beta.1、キッシュちゃん、帽子で解説をしていきます。

> 注意: 導入後に起こったいかなる事にも私は責任を持ちません。自己責任でご利用ください。

## ダウンロード

GitHub もしくは Booth から、 UnityPackage をダウンロードしてください。

- [GitHub](https://github.com/mika-f/VRChat-InventorySystem)

ダウンロード後、お使いのプロジェクトにインポートしてください。  
`Assets` 以下に、 `Mochizuki/VRChat` のようなフォルダーが出来ていれば OK です。

## Inventory Editor

Unity のメニューバーの `Mochizuki/VRChat/Inventory Editor` から、専用エディターを開いてください。

![](https://assets.mochizuki.moe/docs/VRChat/InventorySystem/1.PNG)

もし上記メニューが存在しない場合は、インポートがうまくいってないので再度インポートを行ってください。

## セットアップ

開いたら、まずはインベントリシステムの Prefab を Hierarchy へドラッグ＆ドロップします。  
Hierarchy へ設置したら、 Hierarchy の中から先ほど開いた Inventory Editor の `Inventory Prefab` の所へ、  
`InventorySystem_DefaultOFF_v3` をドロップします。  
このとき、 Project の中のものをドロップすると動かないので注意してください。

[<img src="https://assets.mochizuki.moe/docs/VRChat/InventorySystem/2.PNG" height="400px" />](https://assets.mochizuki.moe/docs/VRChat/InventorySystem/2.PNG)

次に、他の項目も設定していきます。  
`Avatar` には、 `VRC_Avatar Descriptor` が設定されている GameObject を設定します。  
キッシュちゃんの場合は (名前を変更していない場合は) `Quiche` もしくは `Quiche_m` を設定します。

次に Collider を設定します。  
ここでは、キッシュちゃんの左手に設定を行います。  
まずは、空の GameObject をアバター直下に作成してください。  
次に、 `Parent Constraint` コンポーネントを追加し、左手を Source に設定して `Zero` をクリックします。

<img src="https://assets.mochizuki.moe/docs/VRChat/InventorySystem/3.PNG" width="450px" />

すると、上にある Transform の値が変わるので、これで Parent Constraint の設定は完了です。  
次に、先ほど作成した GameObject の子として、さらに GameObject を作成します。  
作成できたら、適当な Collider コンポーネントをアタッチしてください。  
下のように、黄緑の枠線が手と同じような大きさになっていれば、それで OK です。

<img src="https://assets.mochizuki.moe/docs/VRChat/InventorySystem/4.PNG" width="550px" />

設定できたら、 `Inventory Editor` の `Collider` へ、 Collider を設定した GameObject を設定します。

この時点で、 `Inventory Prefab`、 `Avatar`、 `Collider` が以下のように設定できていれば良い調子です。

<img src="https://assets.mochizuki.moe/docs/VRChat/InventorySystem/5.PNG" width="550px" />

次に `Object` を設定します。  
これは、あらかじめ位置を調整しておいた帽子を使用します。  
(Booth などで配布されているアイテムの場合、多くの場合は設定済みであるため省略します)。

これも同じく、帽子の GameObject を `Object` に設定すれば OK です。

最後の `Parent` は、当たり判定を追加したい場所に設定します。  
今回の場合は、キッシュちゃんのカバンの位置に設定しますが、好きな場所に設定してよいです。

これは、 Collider を設定したときのように `Parent Constraint` をもつ GameObject を作成し、設定します。  
設定が終わったら、作成した GameObject を `Parent` に設定してあげれば OK です。

この時点で、全ての設定が完了し、一番下のボタンが押せるようになっていると思うので、  
設定に問題が無ければボタンをクリックしてください。

うまくいけば、先ほどまで表示されていた帽子が消えますが、これが正常動作なので問題ありません。

最後に、微調整を行います。  
今の状態のままだと、画像のようにカバンの所から何かが出てきている状態になってしまいます。

![](https://assets.mochizuki.moe/docs/VRChat/InventorySystem/6.PNG)

このままだと不格好なので、これを消します。  
まずは、最後に設定した `Parent` の直下に `InventoryTrigger` が追加されていることを確認してください。

![](https://assets.mochizuki.moe/docs/VRChat/InventorySystem/7.PNG)

追加されていない場合は、正常にできていないので、今までの項目を見直してみてください。  
追加されている場合は、その下にある `Shims` のさらに下にある `Trigger` を、  
`InventoryTrigger` の子として設定します。  
したの画像のようになっていれば OK です。

![](https://assets.mochizuki.moe/docs/VRChat/InventorySystem/8.PNG)

設置できていれば、 `Shims` は必要なくなるので削除します。  
削除したら、いままでと同様に空の `GameObject` を、 **`Shims` という名前で** 作成します。  
このとき、 `Shims` という名前以外で作成するとうまく動かなくなるので注意してください。

最後に、作成した `Shims` の子に `Triggers` を設定してあげれば、調整が完了です。

## お疲れさまでした！

あとは、 VRChat へアバターをアップロードすれば、インベントリシステムが使えます。
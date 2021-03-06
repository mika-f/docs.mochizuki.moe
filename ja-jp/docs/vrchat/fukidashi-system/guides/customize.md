---
title: Fukidashi System のカスタマイズ
---

# Fukidashi System のカスタマイズ

## テクスチャ改変

Fukidashi System にはデフォルトテクスチャとして、 `Sample.png` を添付していますが、自前のテクスチャを用意することで、表示されるメッセージの内容を好きに設定することが可能です。

テクスチャの仕様は以下の通りです。

1. テクスチャは正方形 (2 の冪乗を推奨します)
1. 横方向に 2 等分
1. 縦方向に 8 等分
1. 左上から順番に Message 1 ～ 16 と割り当てられる

上記仕様に沿っていれば完全に自前で用意することも可能ですが、可能ならば以下のファイルを使用するのを推奨します。

-   `FukidashiTemplate.clip`
    -   CLIP STUDIO PAINT が使える人向け
    -   レイヤー分けあり
-   `FukidashiTemplate.png`
    -   CLIP STUDIO PAINT が使えない人向け
    -   上のファイルの書き出し版

上記のどちらのファイルにしても、初めから用意されている枠の中に収まるように文字や記号を設定してください。  
枠からはみ出したりした場合は、途中で途切れたり、うまく表示されない可能性があります。

テクスチャの編集が終わったら、 `Message Board` GameObject のシェーダー設定を開き、 `Texture` の項目を入れ替えることで、設定の反映が完了します。

<figure>
  <img src="https://assets.mochizuki.moe/docs/fukidashi-system/customize-inspector.PNG" data-zoomable="true">
  <figcaption>Inspector の <code>MessageBoard</code> を選択し、</figcaption>
</figure>

<figure>
  <img src="https://assets.mochizuki.moe/docs/fukidashi-system/customize-texture.png" width="300px" data-zoomable="true">
  <figcaption>改変したテクスチャを設定する</figcaption>
</figure>
## シェーダー改変

デフォルトのシェーダーの場合 Unlit になっているため、影の影響を受けません。  
その仕様が気に入らない場合、以下の仕様にそって自前で作成することが可能です。

1. 0 ～ 16 を入力値として取る `TextureNo` プロパティを持つ
1. 0 では何も表示しない (`discard` もしくは白を表示する)
1. 1 ～ 16 では上記テクスチャの仕様に沿ったメッセージを表示する

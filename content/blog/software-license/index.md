---
title: "ソフトウェアライセンスについて"
date: 2021-10-17T23:07:10+09:00
draft: false
summary: "ソフトウェアライセンスについて学んだこと"
categories:
  - 学習メモ
tags:
  - 技術
  - メモ
---

# OSS ライセンスに共通する主な条件

- 再配布する際にライセンス本文をつける
- 利用は無保証、脆弱性や不具合は自己責任
- 対象のソフトウェアに関連する特許がある場合、無償で利用許諾する

# OSS ライセンスの類型

## コピーレフト型(GPL)

- 改変部分のソースコード開示: 要  
- 他のソフトウェアのソースコード開示: 要

- 派生製品のソースコードも開示させる
- 製品に組み込んだ場合、製品すべてのソースコード開示が必要となる

## 準コピーレフト型(MPL)

- 改変部分のソースコード開示: 要  
- 他のソフトウェアのソースコード開示: 不要

- 改変した場合、その改変部分を開示させる

## 非コピーレフト型(BSD License)

- 変部分のソースコード開示: 不要  
- 他のソフトウェアのソースコード開示: 不要

- ほぼ何も気にしない
- 主なライセンス: BSD License, Apache License, MIT Lisense

## MIT ライセンス

> The MIT License Copyright (c)  
> 以下に定める条件に従い、本ソフトウェアおよび関連文書のファイル（以下「ソフトウェア」）の複製を取得するすべての人に対し、ソフトウェアを無制限に扱うことを無償で許可します。これには、ソフトウェアの複製を使用、複写、変更、結合、掲載、頒布、サブライセンス、および/または販売する権利、およびソフトウェアを提供する相手に同じことを許可する権利も無制限に含まれます。  
> 上記の著作権表示および本許諾表示を、ソフトウェアのすべての複製または重要な部分に記載するものとします。  
> ソフトウェアは「現状のまま」で、明示であるか暗黙であるかを問わず、何らの保証もなく提供されます。ここでいう保証とは、商品性、特定の目的への適合性、および権利非侵害についての保証も含みますが、それに限定されるものではありません。 作者または著作権者は、契約行為、不法行為、またはそれ以外であろうと、ソフトウェアに起因または関連し、あるいはソフトウェアの使用またはその他の扱いによって生じる一切の請求、損害、その他の義務について何らの責任も負わないものとします

## 結局

- 自由に使って良い
- 著作権表示と本許諾表示を明記する

リポジトリ内のLICENSEをコピーして貼っておくと良さそうです。

# 参考資料

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/419829fc59af479998ebeff496251e65" title="ソフトウェアライセンス 2021 / Software license 2021" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;"></iframe>

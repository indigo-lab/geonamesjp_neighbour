# GeoNames.jpのURI間の隣接関係（基礎自治体以上のURI間）

[GeoNames.jp](http://geonames.jp/) の市町村、特別区、政令市の区、郡、都道府県のURI間の実空間上の隣接関係のデータセット


## What's this?
GeoNames.jpの市町村、特別区、政令市の区、郡、都道府県のURI間の実空間上の隣接関係を、[GeoNames Ontology](http://www.geonames.org/ontology/documentation.html) で定義された[gn:neighbour](http://www.geonames.org/ontology#neighbour) で結ぶデータセットです。

ジオメトリは、[国土数値情報 行政区域データ　平成26年度　（作成時点：平成26年4月1日） (国土交通省)](http://nlftp.mlit.go.jp/ksj/gml/datalist/KsjTmplt-N03.html)　を使用しています。


このデータセットのライセンスは [CC-BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/)  です。


##隣接関係の定義

[gn:neighbour](http://www.geonames.org/ontology#neighbour)の定義は「境界を共有」ですが、このデータセットでは「境界が１点のみを共有する」場合も「境界を共有」と見なしています。

また、国土数値情報 行政区域データにおいて、ジオメトリに内水面（湖沼、河川）が含まれていますが、海面は含まれません。そのため、このデータセットでは、陸上では隣接関係ではない場合でも、湖沼、河川上で境界を共有している場合は隣接関係になり、逆に、海上の橋、海底トンネルで直接往来が可能あっても、海面の場合は境界を共有しないため隣接関係になりません。

## Example

	@prefix gn:    <http://www.geonames.org/ontology#> .
	@prefix gnjp:  <http://geonames.jp/resource/> .

	gnjp:東京都世田谷区  gn:neighbour  gnjp:神奈川県 , gnjp:東京都調布市 , gnjp:東京都渋谷区 , gnjp:東京都狛江市 , gnjp:神奈川県川崎市 , gnjp:神奈川県川崎市中原区 , gnjp:神奈川県川崎市多摩区 , gnjp:東京都三鷹市 , gnjp:神奈川県川崎市高津区 , gnjp:東京都大田区 , gnjp:東京都杉並区 , gnjp:東京都目黒区 .

	gnjp:三重県南牟婁郡紀宝町  gn:neighbour  gnjp:三重県熊野市 , gnjp:三重県南牟婁郡御浜町 , gnjp:和歌山県 , gnjp:和歌山県新宮市 .
	gnjp:三重県南牟婁郡  gn:neighbour  gnjp:和歌山県 , gnjp:和歌山県新宮市 , gnjp:三重県熊野市 .



## Note
* 17,473 Triples (2015/07/22 時点)
* データセットのトリプルに加えて、データセット自体のメタデータを [VoID Vocabulary](http://www.w3.org/TR/void/) で記述しています。
* 境界未定地域が関係する隣接関係については、国土数値情報 行政区域データのジオメトリを元に隣接関係を判定しています。
* 政令市が関連する隣接関係は、政令市の区の隣接関係から構築を行っています。
* 郡、都道府県が関連する隣接関係は、市町村の隣接関係から構築を行っています。
* 他URIと隣接関係が存在しないURIは掲載していません。

* [DBpedia Japanese](http://ja.dbpedia.org/)での[dbpedia-ja:隣接自治体](http://ja.dbpedia.org/property/%E9%9A%A3%E6%8E%A5%E8%87%AA%E6%B2%BB%E4%BD%93)、もしくは[dbpedia-ja:隣接自治体・行政区 ](http://ja.dbpedia.org/property/%E9%9A%A3%E6%8E%A5%E8%87%AA%E6%B2%BB%E4%BD%93%E3%83%BB%E8%A1%8C%E6%94%BF%E5%8C%BA) (政令市の区) プロパティでの各自治体間の関係性と、本データでの各自治体間の関係性を比較を行いました。その結果、一部合致しないケースがあり、[地理院地図](http://maps.gsi.go.jp/)にて目視で確認を行ったところ、[DBpedia Japanese](http://ja.dbpedia.org/)側に以下の存在を確認しました。
	* 本データセットの仕様と合致しないケース
	* [DBpedia Japanese](http://ja.dbpedia.org/)側の記載と[地理院地図](http://maps.gsi.go.jp/)で隣接関係が異なるケース

* 2014(平成26)/4/1以降の自治体の合併は反映していません。([国土数値情報 行政区域データ　平成26年度　（作成時点：平成26年4月1日） (国土交通省)](http://nlftp.mlit.go.jp/ksj/gml/datalist/KsjTmplt-N03.html)　に由来)
* 北海道の振興局（旧支庁）は隣接関係の対象外としています。（[GeoNames.jp](http://geonames.jp/)の仕様に準拠）



##湖沼を挟んでの隣接関係
陸地では隣接関係にないが、湖沼上での境界の共有により本データセットにおいて隣接として取り扱っている関係は以下のとおりです。


	#霞ヶ浦
	gnjp:茨城県かすみがうら市	gn:neighbour  gnjp:茨城県稲敷郡阿見町 .
	gnjp:茨城県稲敷郡阿見町	gn:neighbour  gnjp:茨城県かすみがうら市 .
	gnjp:茨城県かすみがうら市	gn:neighbour  gnjp:茨城県稲敷郡美浦村 .
	gnjp:茨城県稲敷郡美浦村	gn:neighbour  gnjp:茨城県かすみがうら市 .
	gnjp:茨城県かすみがうら市	gn:neighbour  gnjp:茨城県小美玉市 .
	gnjp:茨城県小美玉市	gn:neighbour  gnjp:茨城県かすみがうら市 .
	gnjp:茨城県稲敷郡美浦村	gn:neighbour  gnjp:茨城県行方市 .
	gnjp:茨城県行方市	gn:neighbour  gnjp:茨城県稲敷郡美浦村 .
	gnjp:茨城県行方市	gn:neighbour  gnjp:茨城県稲敷市 .
	gnjp:茨城県稲敷市	gn:neighbour  gnjp:茨城県行方市 .
	
	#琵琶湖
	gnjp:滋賀県近江八幡市	gn:neighbour  gnjp:滋賀県高島市 .
	gnjp:滋賀県高島市	gn:neighbour  gnjp:滋賀県近江八幡市 .
	gnjp:滋賀県近江八幡市	gn:neighbour  gnjp:滋賀県大津市 .
	gnjp:滋賀県大津市	gn:neighbour  gnjp:滋賀県近江八幡市 .
	gnjp:滋賀県近江八幡市	gn:neighbour  gnjp:滋賀県彦根市 .
	gnjp:滋賀県彦根市	gn:neighbour  gnjp:滋賀県近江八幡市 .
	gnjp:滋賀県高島市	gn:neighbour  gnjp:滋賀県彦根市 .
	gnjp:滋賀県彦根市	gn:neighbour  gnjp:滋賀県高島市 .
	gnjp:滋賀県守山市	gn:neighbour  gnjp:滋賀県大津市 .
	gnjp:滋賀県大津市	gn:neighbour  gnjp:滋賀県守山市 .
	gnjp:滋賀県大津市	gn:neighbour  gnjp:滋賀県野洲市 .
	gnjp:滋賀県野洲市	gn:neighbour  gnjp:滋賀県大津市 .
	gnjp:滋賀県長浜市	gn:neighbour  gnjp:滋賀県彦根市 .
	gnjp:滋賀県彦根市	gn:neighbour  gnjp:滋賀県長浜市 .
	
	#中海	
	gnjp:島根県安来市	gn:neighbour  gnjp:鳥取県境港市 .
	gnjp:鳥取県境港市	gn:neighbour  gnjp:島根県安来市 .

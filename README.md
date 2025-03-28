# Lunar 3D Model and Lamp Design

NASA提供の月面標高と色の観測データを使用して3Dプリンタブルな月面モデルを作成するJupyter Notebookです。
表面にはリアルな月面のクレーターを再現し、内部の厚さを調整することで月面の色を表現したランプをデザインします。

## 概要
### 月面の3Dモデルのデザイン

`lunar-surface.ipynb` は、月面のクレーターをリアルデータから忠実に3Dプリントするための Jupyter Notebook です：

- NASA/USGSが公開している[月の高解像度標高データ](https://astrogeology.usgs.gov/search/map/moon_lro_lola_dem_118m) をダウンロード
- 月の標高データを3D球体モデルにマッピング
- 地形の強調表示による視覚的効果の向上
- メッシュの最適化と間引きによる3Dプリント用データの準備
- 中空シェルモデルの作成によるプリント材料の節約
- STLファイル出力

### 月面ランプのデザイン

`lunar-lamp.ipynb` は、月面3DモデルをランプとしてデザインするためのJupyter Notebookです：

- NASAがScientific Visualization Studioで公開している月面の色データ [CGI Moon Kit](https://svs.gsfc.nasa.gov/4720/) をダウンロード
- 表面に月のクレーターによる凹凸を追加
- 内側の厚さの変化で内部からの光を調整して月面の色を表現
- STLファイル出力

## 使用方法

1. このリポジトリをクローンまたはダウンロードします
2. 必要なライブラリをインストールします
3. Jupyter Notebookを起動して、リポジトリのノートブックを開きます
4. セルを順に実行します

## 注意点

- 月面の標高データは約8GBと大きいため、ダウンロードには時間がかかります
- データ処理には十分なメモリが必要です
- 3Dモデルの解像度や地形強調度は、パラメータ調整により変更可能です

## 技術的詳細

このノートブックでは以下の技術を使用しています：

- Rasterio：地理空間ラスターデータ処理
- PyVista：3Dメッシュ操作と可視化
- 球面座標変換：標高データを球体表面にマッピング
- メッシュ間引きアルゴリズム：3Dプリント用の最適化


## 3Dプリント設定

出力済みのSTLファイルを3Dプリントするための設定例を以下に示します:
- メッシュファイル: `model/lunar_lamp.stl`

### Bambu Studio

3Dプリントをするときに設定すると良い項目は以下の通りです：

- Wall generator: Arachne
- Top surface pattern: Archimedean Chords

Bambu Studio 設定例: `model/lunar_lamp.3mf`

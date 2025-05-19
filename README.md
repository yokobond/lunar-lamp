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

内部にLEDを入れる穴は開けていないので、Blenderなどで開けます。

- 穴の空いたBlenderファイル: `model/lunar-lamp-print.blend`

- [Blender](https://www.blender.org/) での穴あけ方法
  - 月のSTLファイルをインポート
  - 月のモデルの穴を開けたいところにcylinderを追加して、BooleanでUnionを選択
  - cylinderの内側に小さいcylinderを追加して、月とBooleanでDifferenceにする(穴になる)

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

このノートブックでは以下のライブラリを使用しています：

- [Rasterio](https://rasterio.readthedocs.io/)：地理空間ラスターデータ処理
- [PyVista](https://www.pyvista.org/)：3Dメッシュ操作と可視化


## 3Dプリント設定

出力済みのSTLファイルを3Dプリントするための設定例を以下に示します:
- 穴なしメッシュファイル: `model/lunar-lamp.stl`
- 穴ありメッシュファイル: `model/lunar-lamp-print.stl`

### Bambu Studio

3Dプリントをするときに設定すると良い項目は以下の通りです：

- Wall generator: Arachne
- Top surface pattern: Archimedean Chords

Bambu Studio 設定例: `model/lunar-lamp-print.3mf`

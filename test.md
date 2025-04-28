変換元 CRS 変換先 CRS 特徴
EPSG:27700 EPSG:4326 イギリス・OSGB36、グリッドファイル要
EPSG:6697 EPSG:4326 日本・地方系測地系、必ず proj.db 必要
🔥 実際にテストするコード例（proj-wasm）
たとえば、ブラウザや Node でこれをやる 👇

javascript
コピーする
編集する
import \* as proj from "proj-wasm";

await proj.proj_init();
proj.set_search_paths(["/opfs/proj"]); // proj.db と grids があるディレクトリ

const transformer = proj.create_crs_to_crs("EPSG:27700", "EPSG:4326");

// イギリス国内の適当な座標例（X, Y）
const result = proj.trans_coord(transformer, [651409.903, 313177.270, 0, 0]);

console.log(result);

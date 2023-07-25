### データ構成
* scores.csv : 通し番号・ID・SMILES・Docking Score・Internal energyの５つのデータを一覧にしたcsvファイル
* inputs: ドッキングの入力に使ったpdbqtファイル
* outputs: ドッキング結果のpdbqtファイル
* PDBs/complex_{通し番号}.pdb: ドッキング結果の一番スコアの良い配座の複合体PDBファイル (prolifなどの解析に使う想定)
* PDBs/ligand_{通し番号}.{pdb | sdf}: ドッキング結果のリガンドのみのファイル
##### @souyakuchan 追加
* iSiP_docking.pse: 各化合物の最良スコアポーズを PyMOL で流し見できるようにしたセッションファイル

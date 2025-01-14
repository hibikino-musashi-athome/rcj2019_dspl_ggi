# これは
Hibikino-Musashi@HomeのRoboCup@Home DSRL Go Get It in Unknown Environment用のプログラム．
# 手法
Training Phaseで, 一般物体識別器による識別結果, および, 音声情報により得た情報, マニピュレーション地点を記憶し,　Test Phaseでその記憶した情報と入力された音声コマンドを比較して, 目的オブジェクトの特定を行う.
## Training Phase
### オブジェクトの識別
You Only Look Once v2(YOLO v2)を用いて, リアルタイムにオブジェクトを80クラスに分類する. その際に, ロボットのヘッドディスプレイに学習する範囲を示すことで, 学習したいオブジェクトのみを学習できようにしている.
### 音声認識による情報の付与
YOLO v2の認識結果に追加して, 音声入力により, オブジェクトのより詳細な情報を追加することでTest Phaseにおける目的オブジェクトの特定を容易にしている. 音声認識には, Google ChromeのWeb Speech APIを用いて, 音声を文字データ化し, データベースに保持する.
## Test Phase
### 目的オブジェクトの特定
Training Phaseと同様, Web Speech APIを用いて, 音声コマンドを文字データ化する. Test Phaseではその文字データを単語ごとに品詞解析し, 名詞と形容詞のみを抽出してデータベースに保持する. Training Phaseで作成したデータベースとTest Phaseで作成したデータベースを比較し, 単語の一致度が高いものを目的オブジェクトとして判断する.
### ヘッドディスプレイを利用したオブジェクトの確認
目的オブジェクトを判断した後, ロボットは判断したオブジェクトが本当に目的のオブジェクトであるかをロボットのヘッドディスプレイを利用して視覚的に確認作業を行う.
## 詳細
本手順は, 下記PDFファイルにより詳細をまとめた.
[https://github.com/hibikino-musashi-athome/rcj2019_dspl_ggi/blob/master/rcj19_dspl_ggi.pdf](https://github.com/hibikino-musashi-athome/rcj2019_dspl_ggi/blob/master/rcj19_dspl_ggi.pdf)

# Gitの基本操作
## gitリポジトリの作成方法
1. スクラッチから作成する(**git init < project name >**)
2. 既存のローカルフォルダをgitリポジトリにする(該当フォルダ内で、**git init**)
3. 既存のリモートリポジトリから作成する
   1. リモートリポジトリから**git clone**して、ローカルリポジトリを作成
   2. 既存のリモートリポジトリを**fork**して自分のリモートリポジトリにコピー

## ローカルリポジトリでの作業
### untrack: git addのようなコマンドを実行していないファイルは、git管理の外にある状態
### staging area: commit前の状態のファイルを修正すると、staging areaには修正前の状態が残り、変更後の情報は、working directoryのtrack済みに入る
### unstage:
* stagingにaddした作業をキャンセルする
* **git restore --staged < file >**
### working directoryでの作業をキャンセル
* 修正前の状態に戻したい
* エディタのundoなどでも戻せるが、過信はできない
* **git restore < file >**
### ファイル名の変更をgitで管理する
* **git mv < filename1 > < filename2 >**
* working directoryにはいかず、その時点でstaging areaに
* 通常のmvコマンドをした場合は、filename1を削除し、新たにfilename2を作成
  * filename1: 削除されたことがgitでworking directory上での削除
  * filename2: **untrackとして**working directoryに追加される
  * ファイルの削除をstaging areaに追加するには、**git add -A** をすればよい
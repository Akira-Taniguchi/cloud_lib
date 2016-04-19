cloud_lib
======================
amazonやgoogleのクラウドサービスを利用できるAPIを作成しました  
ご利用は自己責任でご自由にどうぞ

使い方
------
１．pipコマンドを実行し、モジュールをダウンロードしてください

    pip install cloud_lib

２．クラスをインポートし、接続情報をコンストラクタで指定してください

    from cloud_lib.amazon_services import Ec2
    ec2_service = Ec2(aws_access_key_id, aws_secret_access_key, region_name)
    ec2_service.start_instance('instance_id')

    from cloud_lib.google_services import BigQuery
    bq_service = BigQuery(project_id, client_id, client_secret, refresh_token)
    bq_service.delete_table(data_set_id, table_id)

機能紹介
------
### Ec2
#### ec2に関連する機能を保持したクラスです
***
start_instance(instance_id):インスタンスを起動します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| instance_id | ◯ | 起動したいインスタンスのID | - | 
戻り値：Bool
***
stop_instance(instance_id):インスタンスを停止します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| instance_id | ◯ | 停止したいインスタンスのID | - | 
戻り値：Bool
***
    
### Sqs
#### sqsに関連する機能を保持したクラスです
***
put_message(message):Queueにメッセージを登録します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| message | ◯ | 登録したいメッセージを文字列型で指定 | - | 
戻り値：なし
***
get_messages(max_number_of_messages):Queueからメッセージを取得します。取得したメッセージはQueueから削除されます

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| max_number_of_messages | × | 一度に取得したいメッセージの数を指定します | 1 | 
戻り値：List
***

### S3
#### S3に関連する機能を保持したクラスです
***
get_keys(bucket_name, prefix=''):バケットに存在するキー情報を返却します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| bucket_name | ◯ | 情報を取得したいバケット名 | - | 
| prefix | × | 取得したいキーのprefix | (0バイト文字列) | 
戻り値：キー名称(yield)
***
download_ascii_file(bucket_name, key, local_file_path, encoding='utf-8', errors='ignore'):アスキーファイルを取得します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| bucket_name | ◯ | 情報を取得したいバケット名 | - | 
| key | ◯ | 取得したいファイルのキー | - | 
| local_file_path | ◯ | 取得したファイルのローカル配置先 | - |
| encoding | × | 取得するファイルの文字コード | utf-8 |
| errors | × | 文字コードでは再現出来ない文字があった時の動作、strict、ignore、replaceの内どれかを設定出来る | ignore |
戻り値：なし
***
download_binary_file(bucket_name, key, local_file_path):バイナリファイルを取得します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| bucket_name | ◯ | 情報を取得したいバケット名 | - | 
| key | ◯ | 取得したいファイルのキー | - | 
| local_file_path | ◯ | 取得したファイルのローカル配置先 | - |
戻り値：なし
***
get_file_obj(bucket_name, key):ファイルオブジェクトを取得します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| bucket_name | ◯ | 情報を取得したいバケット名 | - | 
| key | ◯ | 取得したいファイルのキー | - | 
戻り値：ファイルオブジェクト(StringIO)
***
upload_binary_file(bucket_name, key, local_file_path):バイナリファイルをアップロードします

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| bucket_name | ◯ | アップロードしたいバケット名 | - | 
| key | ◯ | アップロードしたいファイルのキー | - | 
| local_file_path | ◯ | アップロードしたいファイルのローカルパス | - |

戻り値：なし
***

### BigQuery
#### BigQueryに関連する機能を保持したクラスです
***
has_table(data_set_id, table_id):テーブルが存在するかどうか確認します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| data_set_id | ◯ | 確認したいテーブルのデータセットID | - | 
| table_id | ◯ | 確認したいテーブルのテーブルID | - | 
戻り値：Bool
***
delete_table(data_set_id, table_id):テーブルを削除します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| data_set_id | ◯ | 削除したいテーブルのデータセットID | - | 
| table_id | ◯ | 削除したいテーブルのテーブルID | - | 
戻り値：なし
***
create_table(source_csv_path, source_schema, data_set_id, table_id):テーブルを作成します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| source_csv_path | ◯ | データソースのCSVパス | - | 
| source_schema | ◯ | データソースのスキーマ | - | 
| data_set_id | ◯ | 作成したいテーブルのデータセットID | - | 
| table_id | ◯ | 作成したいテーブルのテーブルID | - | 
戻り値：ジョブの詳細(dictionary)
***
create_view(data_set_id, view_name, query):viewを作成します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| data_set_id | ◯ | 作成したいテーブルのデータセットID | - | 
| view_name | ◯ | viewの名称 | - |
| query | ◯ | viewを作成するクエリ | - | 
戻り値：ジョブの詳細(dictionary)
***
import_csv_from_storage(source_csv_path, source_schema, data_set_id, table_id):テーブルを作成し、データをインポートします

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| source_csv_path | ◯ | データソースのCSVパス | - | 
| source_schema | ◯ | データソースのスキーマ | - | 
| data_set_id | ◯ | 作成したいテーブルのデータセットID | - | 
| table_id | ◯ | 作成したいテーブルのテーブルID | - | 
| write_disposition | × | すでにテーブルが存在した場合の動作、「WRITE_TRUNCATE」「WRITE_APPEND」「WRITE_EMPTY」が指定できる| WRITE_EMPTY |
戻り値：ジョブの詳細(dictionary)
***
query(query, time_out=60000, allow_large_results=False):クエリを実行します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| query | ◯ | 実行するクエリ | - | 
| time_out | × | クエリの最大待機ミリ秒 | 60000 | 
| allow_large_results | × | limitを超えた結果サイズを許容するか | False |
戻り値：レコード情報(yield)
***
get_table_list(data_set_id):テーブルリストを取得します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| data_set_id | ◯ | テーブル一覧を取得したいデータセットID | - | 
戻り値：テーブル名称(yield)
***

### CloudStorage
#### google cloud storageに関連する機能を保持したクラスです
***
upload_file(local_file_path, bucket_name, storage_file_path):ファイルをアップロードします

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| local_file_path | ◯ | アップロードするファイルのローカルパス | - |
| bucket_name | ◯ | アップロード先のバケット名称 | - |
| storage_file_path | ◯ | アップロード先のファイルパス | - |
戻り値：Bool
***
download_file(local_file_path, bucket_name, storage_file_path):ファイルをダウンロードします

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| local_file_path | ◯ | ダウンロード先のローカルパス | - |
| bucket_name | ◯ | ダウンロード元のバケット名称 | - |
| storage_file_path | ◯ | ダウンロード元のファイルパス | - |
戻り値：Bool
***
get_list(bucket_name, name_prefix=None, content_type=None):存在するファイルのリストを取得します

| 名前 | 必須 | 説明 | デフォルト値 | 
|:-----------|:------------:|:-----------|:-----------| 
| bucket_name | ◯ | ダウンロード元のバケット名称 | - |
| name_prefix | × | 取得したいキーのprefix | None |
| content_type | × | 取得したいファイルのコンテントタイプ | None |
戻り値：List

  
関連情報
--------
1. [ググレカス(ブログ)](http://gugurekasu.blogspot.jp/)
2. [LinkedIn](https://jp.linkedin.com/in/akirataniguchi1)
 
ライセンス
----------
Distributed under the [MIT License][mit].
[MIT]: http://www.opensource.org/licenses/mit-license.php

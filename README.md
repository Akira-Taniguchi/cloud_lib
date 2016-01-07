cloud_lib
======================
amazonやgoogleのクラウドサービスを利用できるAPIを作成しました  
ご利用は自己責任でご自由にどうぞ

使い方
------
クラスをインポートし、接続情報をコンストラクタで指定してください

    from cloud_lib.amazon_services import Ec2
    ec2_service = Ec2(aws_access_key_id, aws_secret_access_key, region_name)
    ec2_service.start_instance('instance_id')

    from cloud_lib.google_services import BigQuery
    bq_service = BigQuery(project_id, client_id, client_secret, refresh_token)
    bq_service.delete_table(data_set_id, table_id)

機能紹介
------
   `Ec2` :ec2に関連する機能を保持したクラスです

    def start_instance(instance_id)
+   `instance_id` :起動したいインスタンスのID


    def stop_instance(instance_id)
+   `instance_id` :停止したいインスタンスのID  


   `S3` :S3に関連する機能を保持したクラスです

    def get_keys(bucket_name, prefix='')
+   `bucket_name` :キーを取得したいバケットの名称

+   `prefix` :取得したいキーのprefix


    def download_ascii_file(bucket_name, key, local_file_path, encoding='utf-8', errors='ignore')
+   `bucket_name` :取得したいファイルのバケット名称

+   `key` :取得したいファイルのキー

+   `local_file_path` :取得したファイルのローカル配置先

+   `encoding` :取得したファイルの文字コード

+   `errors` :文字コードでは再現出来ない文字があった時の動作、strict、ignore、replaceの内どれかを設定出来る


    def download_binary_file(bucket_name, key, local_file_path):
+   `bucket_name` :取得したいファイルのバケット名称

+   `key` :取得したいファイルのキー

+   `local_file_path` :取得したファイルのローカル配置先


    def get_file_obj(bucket_name, key):
+   `bucket_name` :取得したいファイルのバケット名称

+   `key` :取得したいファイルのキー


   `BigQuery` :BigQueryに関連する機能を保持したクラスです
 
     def has_table(data_set_id, table_id):
+   `data_set_id` :データセットID

+   `table_id` :存在を確認したいtable_id


     def delete_table(data_set_id, table_id):
+   `data_set_id` :データセットID

+   `table_id` :削除したいtable_id
    

     def create_table(source_csv_path, source_schema, data_set_id, table_id):
+   `source_csv_path` :データソースのCSVパス

+   `source_schema` :データソースのスキーマ

+   `data_set_id` :データセットID

+   `table_id` :table_id
    

    def import_csv_from_storage(storage_path, source_schema, data_set_id, table_id):
+   `source_csv_path` :データソースのCSVパス

+   `source_schema` :データソースのスキーマ

+   `data_set_id` :データセットID

+   `table_id` :table_id


    def query(query, time_out=60000):
+   `query` :実行したいクエリ

+   `time_out` :最大待機ミリ秒数


    def get_table_list(data_set_id):
+   `data_set_id` :データセットID


   `CloudStorage` :google cloud storageに関連する機能を保持したクラスです

    def upload_file(local_file_path, bucket_name, storage_file_path):
+   `local_file_path` :アップロードしたいファイルパス

+   `bucket_name` :アップロード先のバケット名

+   `storage_file_path` :アップロード先のファイルパス


    def download_file(local_file_path, bucket_name, storage_file_path):
+   `local_file_path` :ダウンロード先のローカルファイルパス

+   `bucket_name` :ファイルが存在するバケット名

+   `storage_file_path` :ダウンロードしたいファイルのパス


    def get_list(bucket_name, name_prefix=None, content_type=None):
+   `bucket_name` :ファイルリストを取得したいバケット名

+   `name_prefix` :取得したいキーのprefix

+   `content_type` :取得したいファイルのコンテントタイプ

  
関連情報
--------
1. [ググレカス(ブログ)](http://gugurekasu.blogspot.jp/)
2. [LinkedIn](https://jp.linkedin.com/in/akirataniguchi1)
 
ライセンス
----------
Distributed under the [MIT License][mit].
[MIT]: http://www.opensource.org/licenses/mit-license.php

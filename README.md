cloud_lib
======================
amazon��google�̃N���E�h�T�[�r�X�𗘗p�ł���API���쐬���܂���  
�����p�͎��ȐӔC�ł����R�ɂǂ���

�g����
------
�N���X���C���|�[�g���A�ڑ������R���X�g���N�^�Ŏw�肵�Ă�������

    from cloud_lib.amazon_services import Ec2
    ec2_service = Ec2(aws_access_key_id, aws_secret_access_key, region_name)
    ec2_service.start_instance('instance_id')

    from cloud_lib.google_services import BigQuery
    bq_service = BigQuery(project_id, client_id, client_secret, refresh_token)
    bq_service.delete_table(data_set_id, table_id)

�@�\�Љ�
------
   `Ec2` :ec2�Ɋ֘A����@�\��ێ������N���X�ł�

    def start_instance(instance_id)
+   `instance_id` :�N���������C���X�^���X��ID


    def stop_instance(instance_id)
+   `instance_id` :��~�������C���X�^���X��ID  


   `S3` :S3�Ɋ֘A����@�\��ێ������N���X�ł�

    def get_keys(bucket_name, prefix='')
+   `bucket_name` :�L�[���擾�������o�P�b�g�̖���

+   `prefix` :�擾�������L�[��prefix


    def download_ascii_file(bucket_name, key, local_file_path, encoding='utf-8', errors='ignore')
+   `bucket_name` :�擾�������t�@�C���̃o�P�b�g����

+   `key` :�擾�������t�@�C���̃L�[

+   `local_file_path` :�擾�����t�@�C���̃��[�J���z�u��

+   `encoding` :�擾�����t�@�C���̕����R�[�h

+   `errors` :�����R�[�h�ł͍Č��o���Ȃ����������������̓���Astrict�Aignore�Areplace�̓��ǂꂩ��ݒ�o����


    def download_binary_file(bucket_name, key, local_file_path):
+   `bucket_name` :�擾�������t�@�C���̃o�P�b�g����

+   `key` :�擾�������t�@�C���̃L�[

+   `local_file_path` :�擾�����t�@�C���̃��[�J���z�u��


    def get_file_obj(bucket_name, key):
+   `bucket_name` :�擾�������t�@�C���̃o�P�b�g����

+   `key` :�擾�������t�@�C���̃L�[


   `BigQuery` :BigQuery�Ɋ֘A����@�\��ێ������N���X�ł�
 
     def has_table(data_set_id, table_id):
+   `data_set_id` :�f�[�^�Z�b�gID

+   `table_id` :���݂��m�F������table_id


     def delete_table(data_set_id, table_id):
+   `data_set_id` :�f�[�^�Z�b�gID

+   `table_id` :�폜������table_id
    

     def create_table(source_csv_path, source_schema, data_set_id, table_id):
+   `source_csv_path` :�f�[�^�\�[�X��CSV�p�X

+   `source_schema` :�f�[�^�\�[�X�̃X�L�[�}

+   `data_set_id` :�f�[�^�Z�b�gID

+   `table_id` :table_id
    

    def import_csv_from_storage(storage_path, source_schema, data_set_id, table_id):
+   `source_csv_path` :�f�[�^�\�[�X��CSV�p�X

+   `source_schema` :�f�[�^�\�[�X�̃X�L�[�}

+   `data_set_id` :�f�[�^�Z�b�gID

+   `table_id` :table_id


    def query(query, time_out=60000):
+   `query` :���s�������N�G��

+   `time_out` :�ő�ҋ@�~���b��


    def get_table_list(data_set_id):
+   `data_set_id` :�f�[�^�Z�b�gID


   `CloudStorage` :google cloud storage�Ɋ֘A����@�\��ێ������N���X�ł�

    def upload_file(local_file_path, bucket_name, storage_file_path):
+   `local_file_path` :�A�b�v���[�h�������t�@�C���p�X

+   `bucket_name` :�A�b�v���[�h��̃o�P�b�g��

+   `storage_file_path` :�A�b�v���[�h��̃t�@�C���p�X


    def download_file(local_file_path, bucket_name, storage_file_path):
+   `local_file_path` :�_�E�����[�h��̃��[�J���t�@�C���p�X

+   `bucket_name` :�t�@�C�������݂���o�P�b�g��

+   `storage_file_path` :�_�E�����[�h�������t�@�C���̃p�X


    def get_list(bucket_name, name_prefix=None, content_type=None):
+   `bucket_name` :�t�@�C�����X�g���擾�������o�P�b�g��

+   `name_prefix` :�擾�������L�[��prefix

+   `content_type` :�擾�������t�@�C���̃R���e���g�^�C�v

  
�֘A���
--------
1. [�O�O���J�X(�u���O)](http://gugurekasu.blogspot.jp/)
2. [LinkedIn](https://jp.linkedin.com/in/akirataniguchi1)
 
���C�Z���X
----------
Distributed under the [MIT License][mit].
[MIT]: http://www.opensource.org/licenses/mit-license.php

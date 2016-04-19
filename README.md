cloud_lib
======================
amazon��google�̃N���E�h�T�[�r�X�𗘗p�ł���API���쐬���܂���  
�����p�͎��ȐӔC�ł����R�ɂǂ���

�g����
------
�P�Dpip�R�}���h�����s���A���W���[�����_�E�����[�h���Ă�������

    pip install cloud_lib

�Q�D�N���X���C���|�[�g���A�ڑ������R���X�g���N�^�Ŏw�肵�Ă�������

    from cloud_lib.amazon_services import Ec2
    ec2_service = Ec2(aws_access_key_id, aws_secret_access_key, region_name)
    ec2_service.start_instance('instance_id')

    from cloud_lib.google_services import BigQuery
    bq_service = BigQuery(project_id, client_id, client_secret, refresh_token)
    bq_service.delete_table(data_set_id, table_id)

�@�\�Љ�
------
### Ec2
#### ec2�Ɋ֘A����@�\��ێ������N���X�ł�
***
start_instance(instance_id):�C���X�^���X���N�����܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| instance_id | �� | �N���������C���X�^���X��ID | - | 
�߂�l�FBool
***
stop_instance(instance_id):�C���X�^���X���~���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| instance_id | �� | ��~�������C���X�^���X��ID | - | 
�߂�l�FBool
***
    
### Sqs
#### sqs�Ɋ֘A����@�\��ێ������N���X�ł�
***
put_message(message):Queue�Ƀ��b�Z�[�W��o�^���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| message | �� | �o�^���������b�Z�[�W�𕶎���^�Ŏw�� | - | 
�߂�l�F�Ȃ�
***
get_messages(max_number_of_messages):Queue���烁�b�Z�[�W���擾���܂��B�擾�������b�Z�[�W��Queue����폜����܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| max_number_of_messages | �~ | ��x�Ɏ擾���������b�Z�[�W�̐����w�肵�܂� | 1 | 
�߂�l�FList
***

### S3
#### S3�Ɋ֘A����@�\��ێ������N���X�ł�
***
get_keys(bucket_name, prefix=''):�o�P�b�g�ɑ��݂���L�[����ԋp���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| bucket_name | �� | �����擾�������o�P�b�g�� | - | 
| prefix | �~ | �擾�������L�[��prefix | (0�o�C�g������) | 
�߂�l�F�L�[����(yield)
***
download_ascii_file(bucket_name, key, local_file_path, encoding='utf-8', errors='ignore'):�A�X�L�[�t�@�C�����擾���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| bucket_name | �� | �����擾�������o�P�b�g�� | - | 
| key | �� | �擾�������t�@�C���̃L�[ | - | 
| local_file_path | �� | �擾�����t�@�C���̃��[�J���z�u�� | - |
| encoding | �~ | �擾����t�@�C���̕����R�[�h | utf-8 |
| errors | �~ | �����R�[�h�ł͍Č��o���Ȃ����������������̓���Astrict�Aignore�Areplace�̓��ǂꂩ��ݒ�o���� | ignore |
�߂�l�F�Ȃ�
***
download_binary_file(bucket_name, key, local_file_path):�o�C�i���t�@�C�����擾���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| bucket_name | �� | �����擾�������o�P�b�g�� | - | 
| key | �� | �擾�������t�@�C���̃L�[ | - | 
| local_file_path | �� | �擾�����t�@�C���̃��[�J���z�u�� | - |
�߂�l�F�Ȃ�
***
get_file_obj(bucket_name, key):�t�@�C���I�u�W�F�N�g���擾���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| bucket_name | �� | �����擾�������o�P�b�g�� | - | 
| key | �� | �擾�������t�@�C���̃L�[ | - | 
�߂�l�F�t�@�C���I�u�W�F�N�g(StringIO)
***
upload_binary_file(bucket_name, key, local_file_path):�o�C�i���t�@�C�����A�b�v���[�h���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| bucket_name | �� | �A�b�v���[�h�������o�P�b�g�� | - | 
| key | �� | �A�b�v���[�h�������t�@�C���̃L�[ | - | 
| local_file_path | �� | �A�b�v���[�h�������t�@�C���̃��[�J���p�X | - |

�߂�l�F�Ȃ�
***

### BigQuery
#### BigQuery�Ɋ֘A����@�\��ێ������N���X�ł�
***
has_table(data_set_id, table_id):�e�[�u�������݂��邩�ǂ����m�F���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| data_set_id | �� | �m�F�������e�[�u���̃f�[�^�Z�b�gID | - | 
| table_id | �� | �m�F�������e�[�u���̃e�[�u��ID | - | 
�߂�l�FBool
***
delete_table(data_set_id, table_id):�e�[�u�����폜���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| data_set_id | �� | �폜�������e�[�u���̃f�[�^�Z�b�gID | - | 
| table_id | �� | �폜�������e�[�u���̃e�[�u��ID | - | 
�߂�l�F�Ȃ�
***
create_table(source_csv_path, source_schema, data_set_id, table_id):�e�[�u�����쐬���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| source_csv_path | �� | �f�[�^�\�[�X��CSV�p�X | - | 
| source_schema | �� | �f�[�^�\�[�X�̃X�L�[�} | - | 
| data_set_id | �� | �쐬�������e�[�u���̃f�[�^�Z�b�gID | - | 
| table_id | �� | �쐬�������e�[�u���̃e�[�u��ID | - | 
�߂�l�F�W���u�̏ڍ�(dictionary)
***
create_view(data_set_id, view_name, query):view���쐬���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| data_set_id | �� | �쐬�������e�[�u���̃f�[�^�Z�b�gID | - | 
| view_name | �� | view�̖��� | - |
| query | �� | view���쐬����N�G�� | - | 
�߂�l�F�W���u�̏ڍ�(dictionary)
***
import_csv_from_storage(source_csv_path, source_schema, data_set_id, table_id):�e�[�u�����쐬���A�f�[�^���C���|�[�g���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| source_csv_path | �� | �f�[�^�\�[�X��CSV�p�X | - | 
| source_schema | �� | �f�[�^�\�[�X�̃X�L�[�} | - | 
| data_set_id | �� | �쐬�������e�[�u���̃f�[�^�Z�b�gID | - | 
| table_id | �� | �쐬�������e�[�u���̃e�[�u��ID | - | 
| write_disposition | �~ | ���łɃe�[�u�������݂����ꍇ�̓���A�uWRITE_TRUNCATE�v�uWRITE_APPEND�v�uWRITE_EMPTY�v���w��ł���| WRITE_EMPTY |
�߂�l�F�W���u�̏ڍ�(dictionary)
***
query(query, time_out=60000, allow_large_results=False):�N�G�������s���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| query | �� | ���s����N�G�� | - | 
| time_out | �~ | �N�G���̍ő�ҋ@�~���b | 60000 | 
| allow_large_results | �~ | limit�𒴂������ʃT�C�Y�����e���邩 | False |
�߂�l�F���R�[�h���(yield)
***
get_table_list(data_set_id):�e�[�u�����X�g���擾���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| data_set_id | �� | �e�[�u���ꗗ���擾�������f�[�^�Z�b�gID | - | 
�߂�l�F�e�[�u������(yield)
***

### CloudStorage
#### google cloud storage�Ɋ֘A����@�\��ێ������N���X�ł�
***
upload_file(local_file_path, bucket_name, storage_file_path):�t�@�C�����A�b�v���[�h���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| local_file_path | �� | �A�b�v���[�h����t�@�C���̃��[�J���p�X | - |
| bucket_name | �� | �A�b�v���[�h��̃o�P�b�g���� | - |
| storage_file_path | �� | �A�b�v���[�h��̃t�@�C���p�X | - |
�߂�l�FBool
***
download_file(local_file_path, bucket_name, storage_file_path):�t�@�C�����_�E�����[�h���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| local_file_path | �� | �_�E�����[�h��̃��[�J���p�X | - |
| bucket_name | �� | �_�E�����[�h���̃o�P�b�g���� | - |
| storage_file_path | �� | �_�E�����[�h���̃t�@�C���p�X | - |
�߂�l�FBool
***
get_list(bucket_name, name_prefix=None, content_type=None):���݂���t�@�C���̃��X�g���擾���܂�

| ���O | �K�{ | ���� | �f�t�H���g�l | 
|:-----------|:------------:|:-----------|:-----------| 
| bucket_name | �� | �_�E�����[�h���̃o�P�b�g���� | - |
| name_prefix | �~ | �擾�������L�[��prefix | None |
| content_type | �~ | �擾�������t�@�C���̃R���e���g�^�C�v | None |
�߂�l�FList

  
�֘A���
--------
1. [�O�O���J�X(�u���O)](http://gugurekasu.blogspot.jp/)
2. [LinkedIn](https://jp.linkedin.com/in/akirataniguchi1)
 
���C�Z���X
----------
Distributed under the [MIT License][mit].
[MIT]: http://www.opensource.org/licenses/mit-license.php

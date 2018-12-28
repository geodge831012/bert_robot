1.����google��BERTģ�Ϳ�Դ������ģ�ͼ����
github��ַ��https://github.com/google-research/bert

2.����BERT��Ŀ�е�run_classifier.py��д���ɣ��ع��˷����㷨�����ݶ�ȡ����

3.ģ�ͻ���BERTģ���ṩ������ѵ����

4.���벿����192.168.9.60:/home/mqq/geodge/BERT/bertĿ¼��
��������

������������
cd /home/mqq/geodge/BERT/bert
export BERT_BASE_DIR=/home/mqq/geodge/BERT/model/chinese_L-12_H-768_A-12
export GLUE_DIR=/home/mqq/geodge/BERT/corpus

ѵ��
python run_biaoge.py \
  --task_name=biaoge \
  --do_train=true \
  --do_eval=true \
  --data_dir=$GLUE_DIR/biaoge \
  --vocab_file=$BERT_BASE_DIR/vocab.txt \
  --bert_config_file=$BERT_BASE_DIR/bert_config.json \
  --init_checkpoint=$BERT_BASE_DIR/bert_model.ckpt \
  --max_seq_length=128 \
  --train_batch_size=32 \
  --learning_rate=2e-5 \
  --num_train_epochs=3.0 \
  --output_dir=/home/mqq/geodge/BERT/output/biaoge/

Ԥ��
python run_biaoge.py \
  --task_name=biaoge \
  --do_predict=true \
  --data_dir=$GLUE_DIR/biaoge \
  --vocab_file=$BERT_BASE_DIR/vocab.txt \
  --bert_config_file=$BERT_BASE_DIR/bert_config.json \
  --init_checkpoint=/home/mqq/geodge/BERT/output/biaoge/ \
  --max_seq_length=128 \
  --output_dir=/home/mqq/geodge/BERT/output/biaoge_predict
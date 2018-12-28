1.根据google的BERT模型开源出来的模型计算的
github地址：https://github.com/google-research/bert

2.依据BERT项目中的run_classifier.py改写而成，重构了分类算法的数据读取部分

3.模型基于BERT模型提供的中文训练集

4.代码部署在192.168.9.60:/home/mqq/geodge/BERT/bert目录下
运行命令

环境变量设置
cd /home/mqq/geodge/BERT/bert
export BERT_BASE_DIR=/home/mqq/geodge/BERT/model/chinese_L-12_H-768_A-12
export GLUE_DIR=/home/mqq/geodge/BERT/corpus

训练
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

预测
python run_biaoge.py \
  --task_name=biaoge \
  --do_predict=true \
  --data_dir=$GLUE_DIR/biaoge \
  --vocab_file=$BERT_BASE_DIR/vocab.txt \
  --bert_config_file=$BERT_BASE_DIR/bert_config.json \
  --init_checkpoint=/home/mqq/geodge/BERT/output/biaoge/ \
  --max_seq_length=128 \
  --output_dir=/home/mqq/geodge/BERT/output/biaoge_predict
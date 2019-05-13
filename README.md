# BERT_Chinese_MRC

基于[BERT](https://github.com/google-research/bert)官方源码做修改，适配中文QA任务[DRCD](https://github.com/DRCSolutionService/DRCD)。

Inspired by [BERT-for-Chinese-Question-Answering](https://github.com/eva-n27/BERT-for-Chinese-Question-Answering)

### 改动

- [x] 基于read_squad_example.py，修改中文的tokenization，去除无法匹配answer_start的数据
- [ ] ToDo

### 使用

* Train&Prediction

```
python run_drcd.py \
  --vocab_file=$BERT_MODEL_DIR/vocab.txt \
  --bert_config_file=$BERT_MODEL_DIR/bert_config.json \
  --init_checkpoint=$BERT_MODEL_DIR/bert_model.ckpt \
  --do_train=True \
  --train_file=$DRCD_DIR/DRCD_training.json \
  --do_predict=True \
  --predict_file=$DRCD_DIR/DRCD_test.json \
  --train_batch_size=6 \
  --learning_rate=3e-5 \
  --num_train_epochs=3.0 \
  --do_lower_case=True \
  --max_seq_length=512 \
  --doc_stride=128 \
  --output_dir=$OUTPUT_DIR/
```

* Evaluate

```
pyton eva.py $DRCD/DRCD_testing.json $OUTPUT_DIR/prediction.json
```

### 结果

* EM: 85.65702834239909
* F1: 91.78050628879733

![result](https://ws4.sinaimg.cn/large/006tNc79gy1g2zldnqvc6j30vg04wgmo.jpg)
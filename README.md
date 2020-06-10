# Comparing standard and effective attention

#### Install from source 
```bash
cd EffectiveAttention 
pip install .
```

#### Train and eval with standard attention

```bash
export GLUE_DIR=/path/to/glue
export TASK_NAME=MRPC

python run_glue.py \
  --model_name_or_path bert-base-cased \
  --task_name $TASK_NAME \
  --do_train \
  --do_eval \
  --data_dir $GLUE_DIR/$TASK_NAME \
  --max_seq_length 128 \
  --per_device_train_batch_size 32 \
  --learning_rate 2e-5 \
  --num_train_epochs 3.0 \
  --output_dir ./models/$TASK_NAME/standard/ \
  --attention_type standard
```


#### Train and eval with standard attention

```bash
export GLUE_DIR=/path/to/glue
export TASK_NAME=MRPC

python run_glue.py \
  --model_name_or_path bert-base-cased \
  --task_name $TASK_NAME \
  --do_train \
  --do_eval \
  --data_dir $GLUE_DIR/$TASK_NAME \
  --max_seq_length 128 \
  --per_device_train_batch_size 32 \
  --learning_rate 2e-5 \
  --num_train_epochs 3.0 \
  --output_dir ./models/$TASK_NAME/effective/ \
  --attention_type effective
```

#### Use the model trained with standard attention, but eval with effective attention

```bash
export GLUE_DIR=/path/to/glue
export TASK_NAME=MRPC

python run_glue.py \
  --model_name_or_path ./models/$TASK_NAME/standard/ \
  --task_name $TASK_NAME \
  --do_eval \
  --data_dir $GLUE_DIR/$TASK_NAME \
  --max_seq_length 128 \
  --per_device_train_batch_size 32 \
  --learning_rate 2e-5 \
  --num_train_epochs 3.0 \
  --output_dir ./models/$TASK_NAME/standard_effective/ \
  --attention_type effective
```
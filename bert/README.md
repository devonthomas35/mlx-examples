# mlxbert

An implementation of BERT [(Devlin, et al., 2019)](https://aclanthology.org/N19-1423/) within mlx.

## Downloading and Converting Weights

The `convert.py` script relies on `transformers` to download the weights, and exports them as a single `.npz` file.

```
python convert.py \
    --bert-model bert-base-uncased
    --mlx-model weights/bert-base-uncased.npz
```

## Run the Model

In order to run the model, and have it forward inference on a batch of examples:

```sh
python model.py \
  --bert-model bert-base-uncased \
  --mlx-model weights/bert-base-uncased.npz
```

Which will show the following outputs:
```
MLX BERT:
[[[-0.17057164  0.08602728 -0.12471077 ... -0.09469379 -0.00275938
    0.28314582]
  [ 0.15222196 -0.48997563 -0.26665813 ... -0.19935863 -0.17162783
   -0.51360303]
  [ 0.9460105   0.1358298  -0.2945672  ...  0.00868467 -0.90271163
   -0.2785422 ]]]
```

They can be compared against the 🤗 implementation with:

```sh
python hf_model.py \
  --bert-model bert-base-uncased
```

Which will show:
```
 HF BERT:
[[[-0.17057131  0.08602707 -0.12471108 ... -0.09469365 -0.00275959
    0.28314728]
  [ 0.15222463 -0.48997375 -0.26665992 ... -0.19936043 -0.17162988
   -0.5136028 ]
  [ 0.946011    0.13582966 -0.29456618 ...  0.00868565 -0.90271175
   -0.27854213]]]
```

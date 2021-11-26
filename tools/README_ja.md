# Visual Genome Datasetsによる学習方法

## データの準備
Visual Genomeのデータセット(MS COCOフォーマット版)のvisual_genome.tgzを `tools/datasets/visual_genome/annotations` におき、`tar zvxf visual_genome.tgz` を実行して展開する。
```
$ tar xvzf visual_genome.tgz
$ cp *.json /path/to/detectron2/tools/datasets/visual_genome/annotations/
```

また、 Visual Genomeの画像データセットをダウンロードし、 `tools/datasets/visual_genome/train_images` および `tools/datasets/visual_genome/val_images` 以下にコピーする。

```
$ wget https://cs.stanford.edu/people/rak248/VG_100K_2/images.zip
$ wget https://cs.stanford.edu/people/rak248/VG_100K_2/images2.zip
$ unzip images.zip
$ unzip images2.zip
$ cp VG_100K/*.jpg /path/to/detectron2/tools/datasets/visual_genome/train_images
$ cp VG_100K_2/*.jpg /path/to/detectron2/tools/datasets/visual_genome/train_images
$ cp VG_100K/*.jpg /path/to/detectron2/tools/datasets/visual_genome/val_images
$ cp VG_100K_2/*.jpg /path/to/detectron2/tools/datasets/visual_genome/val_images
```

## 学習の実行
`tools/train_net.py` を用いて学習を行う。

### FasterRCNN ResNet 50を用いて学習する場合
`config/faster_rcnn_R_50_FPN_1x.yaml` を用いて学習を行う。
詳細なオプションは `./train_net.py -h` を参照のこと。


```
$ cd tools/
$ ./train_net.py --num-gpus 8 \
  --config-file ../configs/Visual-Genome/faster_rcnn_R_50_FPN_1x.yaml
```

### FasterRCNN ResNext 101を用いて学習する場合
`config/faster_rcnn_X_101_32x8d_FPN_3x.yaml` を用いて学習を行う。

```
$ cd tools/
$ ./train_net.py --num-gpus 8 \
  --config-file ../configs/Visual-Genome/faster_rcnn_R_50_FPN_1x.yaml
```

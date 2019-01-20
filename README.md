### 自编码器: 句向量
* 跑起来Lisp化,用模型感知到写模型
* 中心线腰部发力,腰部之于桥马合一,整体之于局部
* 深度学习是盲人摸象,易于陷入局部化认知

```lisp

;; import
(import
 [tensorflow :as tf]
 keras
 [keras [backend :as K]]
 [keras.models [Model load_model]]
 [numpy :as np])

;; 加载自动编码器: 句向量模型
(setv autoencoder (load_model "./data/sent-thoughts-autoencoder.h5")) ;;=> 23M

;; 编码器层:
(setv encoder
      (Model autoencoder.input ;;=> <tf.Tensor 'decoder_lstm_1/add_16:0' shape=(?, ?, 100) dtype=float32>
             (autoencoder.get_layer "encoder_lstm") ;;=> <keras.layers.wrappers.Bidirectional object at 0x7f43c7ff5dd8>
             ))

```

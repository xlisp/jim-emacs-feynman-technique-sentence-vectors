### 自编码器: 句向量
* 中心线打出去,简单直接粗暴！没有那么多完美！过早的完美是万恶之源！
* 卡马克和RMS的Lisp黑客精神,没有那么多时间焦虑的,有那么多时间焦虑,不如多撸几百行代码: λ演算演算着就通了
* 马斯克: 人往往高估了钱的左右,而低估了自己能力多强大,人远远比想象的更强大
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

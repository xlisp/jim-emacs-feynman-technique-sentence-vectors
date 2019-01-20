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

;; 网络->结构, 损失函数和优化函数是怎样的?

;; 如何训练自动编码器?

;; 中文句向量和英文句向量的区别有哪些?

;; 如何用好搜狗的词向量模型和字符向量模型?

;; 自编码器分编码器和解码器,训练好了自编码器就放弃到解码器是为什么?

;; 自编码器的设计思想和CNN的卷积和池化有什么关系?

;; 自编码器能够生成矜持表示和词向量句向量的关系是什么?
;;;; LSTM设计出来就是为了适用于句子顺序的

;; 获得输入词的词向量word_embedder.get_word_vector & 输入字符的字符向量char_embedder.get_word_vector如何填充后作为输入张量?

;; 输入张量到自编码器的编码层predict输出句向量,需要经过哪些几何变换?

```

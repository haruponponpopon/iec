# iec
## stable_diffusion.ipynb
- [参考文献](https://huggingface.co/CompVis/stable-diffusion-v1-4)
- textを入力として、画像を生成する。基本的なモデル。
- メモリ使用量半分のモデル(以下全て同様)
- 生成画像はstable_diffusionに保存される
## waifu_diffusion.ipynb
- [参考文献](https://huggingface.co/hakurei/waifu-diffusion)
- アニメ画像生成に特化したモデル
- textを入力として、画像を生成する。
- 生成画像はwaifu_diffusionに保存される
## IEC_crossover
- textを入力として画像を生成する標準的なモデルと、promptベースの対話的進化計算を組み合わせたもの
- 対話型進化計算は一点交差と突然変異
- seed値は各画像につき固定
- 生成画像はiecに保存される
## IEC_mutation
- textを入力として画像を生成する標準的なモデルと、promptベースの対話的進化計算を組み合わせたもの
- 対話型進化計算は突然変異のみ
- IEC_crossoverの下位互換なので出る幕なし
## advance/iec+image_synthesis.ipynb
- textと画像を入力として画像を生成するimage2imageモデルと、promptベースの対話的進化計算を組み合わせたもの
- 対話型進化計算はIEC_crossoverと同じアルゴリズム
- 生成画像はiecに保存される
## advance/image_synthesis
- textと画像を入力として画像を生成するimage2imageモデル
## advance/original_pipeline.ipynb
- [参考文献](https://torch.classcat.com/2022/10/11/huggingface-diffusers-0-4-notebook-stable-diffusion/)
- [参考文献](https://huggingface.co/blog/stable_diffusion)
- textを入力として画像を生成する、基本的なモデル。
- 画像生成のうち、textを数値に変換した行列をいじれるようにしたもの
## advance/pipeline_image2image.ipynb
- [参考文献](https://towardsdatascience.com/stable-diffusion-using-hugging-face-variations-of-stable-diffusion-56fd2ab7a265)
- textと画像を入力として画像を生成するimage2imageモデル
- 画像生成のうち、textを数値に変換した行列をいじれるようにしたもの
## advance/image2image_iec.ipynb
- textと画像を入力として画像を生成するimage2imageモデルと、画像の数字ベースの対話的進化計算を組み合わせたもの
- まだ同じ遺伝子なのに他の画像が表示されるバグが残ってる
## trouble shooting
### float16 と float32 が競合してエラー
```
with autocast("cuda"):
```
を入れる  
- [参考文献](https://td2sk.hatenablog.com/entry/2022/08/24/001630)

# iec
![UI](https://user-images.githubusercontent.com/72332745/236678556-01767ad5-69a5-4929-841b-098b4c3113d3.png)
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
# ga(予備実験)
## ga_txt_and_image.ipynb
- textを入力として、画像を生成する
- textも画像もどちらのベクトルも進化させる
- 同じパスにiecディレクトリを用意する必要あり。ここに生成画像が保存される
- fitness.txtに適合度の世代ごとの変化が保存される
- エリート戦略、一様交叉、残りは突然変異
## image2image_ga.ipynb
- 画像、textを入力として、画像を生成するpipelineを使用
- 画像ベクトルを進化させる
## txt2image_ga.ipynb
- textを入力として、画像を生成するもので、画像ベクトルを進化させる
pre_experiment_gaディレクトリにある
## graph_plot.ipynb
- 適合度ファイル(fitness.txt)をもとにグラフを生成する
## trouble shooting
### float16 と float32 が競合してエラー
```
with autocast("cuda"):
```
を入れる  
- [参考文献](https://td2sk.hatenablog.com/entry/2022/08/24/001630)
### local variable 'epoch' referenced before assignment
globalを頭につける
### name 'epoch' is used prior to global declaration
同じ関数内でできるだけ早めに宣言する  
手前にこの単語が出てきているとこのエラーになる
### TclError: image "pyimage5" doesn't exist
一回絶対に動くコードで実行して動いたらエラーが解消される

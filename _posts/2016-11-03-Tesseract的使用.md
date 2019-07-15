---
layout: post
title: "Tesseract的使用"
date: 2016-11-03 13:20:08 
description: "Tesseract的使用"
tag: 爬虫
---

> 想干就干，要干就干的漂亮，即使没有人为你鼓掌，至少还能够勇敢的自我欣赏。

# Tesseract 使用

tesseract 是一套流行的OCT算法。专门做图片内容识别。我们只需要下载相应的训练数据就能使用tesseract进行图片内容读取。

安装参考：https://jingyan.baidu.com/article/219f4bf788addfde442d38fe.html

### 在python中使用

安装pytesseract： pip install pytesseract

```python
import pytesseract
from PIL import Image

image = Image.open('QQ.png')

result = pytesseract.image_to_string(image, lang='chi_sim')
print(result)
```

对图片进行处理：

```python
from PIL import Image

import pytesseract

image = Image.open('./douban.jpg')

# 灰度化
image = image.convert('L')
# 杂点清除掉。只保留黑的和白的。返回像素对象
data = image.load()
w, h = image.size #ndarry pandas
for i in range(w):
    for j in range(h):
        if data[i, j] > 120:
            data[i, j] = 255 # 纯白
        else:
            data[i, j] = 0 # 纯黑
image.save('clean_captcha.png')
image.show()

result = pytesseract.image_to_string(image, lang='eng')
print(result)


image.show()
```

<br>

转载请注明：[点墨的博客](http://tipFiger.github.io) » [点击阅读原文](http://tipFiger.github.io/2016/11/Tesseract的使用/)


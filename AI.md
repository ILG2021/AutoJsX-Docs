# OCR文档
>稳定性: 
>
> 实验性的函数、模块或特性，
> 在未来的更新中可能会更改或移除。应该谨慎使用这些函数或模块，或者仅用作临时或试验用途。
# Tessract OCR
**6.2.9 新增**
前往 github 下载完整例子：[TessractOCR](https://github.com/wilinz/autoxjs-tessocr)
# Google ML kIT OCR
**6.3.4 新增**
## gmlkit.ocr(img,Language)
- `img` {Image} 图片
- `Language` {String} 识别语言，可选值为：
   - `la` 拉丁
   - `zh` 中文
   - `sa` 梵文
   - `ja` 日语
   - `ko` 韩语
   - [更多语言](https://developers.google.cn/ml-kit/vision/text-recognition/v2/languages)
- `retrun` {Object} Json
```JS
//识别中文
let result = gmlkit.ocr(img, "zh");
log(result.text)
```

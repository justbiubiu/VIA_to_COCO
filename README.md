# VIA_to_COCO



由于我发现VIA直接导出的COCO格式的json格式标注文件，其实是不对的，仔细分析过json文件之后，发现和COCO2017的json文件有一些出入，导致标注文件并不能被COCO格式的模型输入识别。所以我直接导出json文件，然后使用代码的方式生成COCO标注文件。

ps:我也不知道官方直接导出为什么会不对！！！很奇怪。

粗看几乎都一样，仔细分析，有些地方就不一样了，比如segmatation,官方的COCO格式是这样的：segmatation[[100，200，300，400]],但是VIA直接导出的是这样的：segmatation[100，200，300，400]。

应该还有其他地方不同，所以才不能识别。

本项目有两个功能：

1、把VIA标注软件导出的json格式文件转换成COCO标注格式的程序

这个程序修改自这里： https://github.com/codingwolfman/VIA2COCO 

非常感谢，因为原作者的代码里面有点bug，所以直接使用是不行的。不过他并未对其进行维护。

所以我修改了一下，亲测可以把VIA导出的json格式的文件转成COCO格式。

测试平台：mmdetection。我在上面进行训练我的模型。他有标准的接口来读取COCO格式的标注文件。如果格式不正确会报错。亲测可以成功进行训练并得到满意的结果。进行了两个任务：分类和实例分割，bbox和segmentation检测是没有问题的。

2、检验并显示coco格式的bbox和mask的程序。

转换完成之后，可以用这个程序跑一遍，检测一下是否正确在图片上显示并保存bbox和mask。一般如果能正常跑完。说明你的数据集标注是正确的。如果有错的话，在上一步转换阶段就会报错。
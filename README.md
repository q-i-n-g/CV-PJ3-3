# CV-PJ3-3
使用nerfstudio框架，详见

https://github.com/nerfstudio-project/nerfstudio/

clone该仓库，并按照要求进行环境配置和依赖包下载，同时参考https://github.com/colmap/colmap 和 https://ffmpeg.org/download.html下载COLMAP和FFmpeg。

## 数据准备
到Google Drive上下载预先拍摄好的环绕物品视频，或自己拍摄视频，创建data文件夹并放入其中。运行：
```
ns-process-data video --data [path-to-the-video.mp4] --output-dir [path-save-processed-data]
```
也可以直接从Google Drive上下载预先使用COLMAP处理好的数据文件。

## 训练
```
ns-train nerfacto --vis viewer+tensorboard  --data [path-to-processed-data]
```
训练好的结果创建output文件并存入其中。

## 测试
可以从Google Drive下载已经训练好的模型直接测试，注意，需要修改config.yml文件中的地址，改为本地path-to-processed-data。或者测试上述训练的模型。运行：
```
ns-eval --load-config [path-to-output-model-config.yml]
```
将会生成output.json文件，得到在测试集的定量评估结果。

## 交互窗口与渲染视频生成
```
ns-viewer --load-config [path-to-output-model-config.yml]
```
之后会进入交互窗口，默认端口为7007，在交互窗口中添加render后导出环绕物品的渲染视频。

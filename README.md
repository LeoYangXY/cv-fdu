CIFAR-10图像分类项目说明文档

1. 项目简介
本项目开发了一个基于全连接神经网络的CIFAR-10图像分类系统，实现了从数据预处理到模型训练、优化的完整流程。系统采用GPU加速计算，使用cupy库（所有的接口于numpy类似，只是能在GPU上处理数据） 直接在GPU上进行数据处理和模型运算。

2. 主要功能
- 数据预处理：自动完成数据加载、标准化和增强（包括水平翻转和随机裁剪）
- 模型构建：支持自定义两层隐藏层的网络结构，提供多种激活函数选择
- 训练优化：采用SGD优化器，支持学习率动态衰减和L2正则化
- 参数调优：内置超参数自动搜索功能
- 可视化分析：提供训练过程曲线和参数分布直方图

3. 文件目录
项目包含以下主要文件：
- cifar-10-batches-py/：存放原始数据集
- parameters_stage1/：保存基础模型参数
- parameters_stage2/：保存进行超参数搜索之后的模型参数
- loss.ipynb：损失函数实现代码
- model.ipynb：网络模型定义代码
- train.ipynb：主训练程序
- trainer.ipynb：优化器实现代码

4. 训练及测试方式
   step1：把该项目的所有文件下载至一个文件夹
   step2：在train.ipynb中X_train, y_train, X_val, y_val, X_test, y_test = load_cifar10_with_augmentation()的括号内加入参数，参数即为cifar-10-batches-py的绝对地址
   step3：运行train.ipynb的代码，会先开始不带有超参数搜索部分：自动训练模型，之后由于代码中的model.load_model(stage=1)这句，我们会自动调用我们最好的不带超参数搜索的模型在测试集上进行测试；然后代码会自动运行到超参数搜索部分：自动训练模型，之后由于代码中的model.load_model(stage=2)这句，我们会自动调用我们最好的不带超参数搜索的模型在测试集上进行测试



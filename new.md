+ Mat 类
    + 是存储和操作 OpenCV 中图像的主要数据结构。
    + 用于密集的 n 维单通道或多通道数组。实际上它可以存储实数或复数值向量和矩阵、彩色图像或灰度图像、直方图、点云等。
    + 有许多种不同的方式可用来创建一个 Mat 对象，最流行的方法是构造函数，其数组的大小和类型被指定为：
        > `Mat(nrows,ncols,type,fillValue)`
    
    
    数组元素的初始值可以由 Scalar 类设置为一个典型的四元素向量（对于存储在数组中的图像的每个 RGB 和透明度分量）。下面展示 Mat 的一个使用示例：

    ```c++
        Mat img_A(4,4,CV_8U,Scalar(255));
        //白色图像；
        //具有 8 位无符号整数的 4x4 单个通道数组
        //（最多 255 个值，对灰度图像有效，例如，255=白色）
    ```
+ at方法：用于获取图像矩阵某点的值或改变某点的值。
        + 单通道图像：`mat.at<uchar>(row,col)`
        + 三通道图像：

        对于三通道来说，每一个像素的位置内含了三个uchar数据，所以对三通道获取像素值要使用Vec3b。Vec3b实质上是一个uchar的数组，最多能装三个数据。
    ```c++
        Vec3b i = image.at<Vec3b>(i,j);
        //返回一个Vec3b类型的数组
    ```

+ `Mat imread( const String& filename, int flags )`
    + 第一个参数是图片路径，不支持"\\"形式的路径
    + 第二个参数是flag

         flags = -1：imread按解码得到的方式读入图像

         flags = 0：imread按单通道的方式读入图像，即灰白图像

        flags = 1：imread按三通道方式读入图像，即彩色图像
+ `void cvtColor(InputArray src, OutputArray dst, int code, int dstCn=0 );`
    + 函数的作用是将一个图像从一个颜色空间转换到另一个颜色空间
    + InputArray src: 输入图像即要进行颜色空间变换的原图像，可以是Mat类 

    + OutputArray dst: 输出图像即进行颜色空间变换后存储图像，也可以Mat类 
    + int code: 转换的代码或标识，即在此确定将什么制式的图片转换成什么制式的图片.
    + int dstCn = 0: 目标图像通道数，如果取值为0，则由src和code决定
+ `void imshow(const string& winname, InputArray mat);`
    + 第一个参数，const string&类型的winname，填需要显示的窗口标识名称。
    + 第二个参数，InputArray 类型的mat，填需要显示的图像。
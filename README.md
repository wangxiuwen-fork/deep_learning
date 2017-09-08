# deeplearning
在卷积神经网络中，关于经过卷积层或者池化层后还剩多少像素的问题：这里不考虑边缘填充的问题，只讲方法帮助理解以便笔试中快速计算。【图片尺寸-卷积核尺寸(或者池化尺寸)】/步长+1=卷积或者池化后的尺寸....最后加1是因为比如1,2有两个数，2-1+1=2。。。
例如:图片尺寸100*100，卷积核尺寸5*5，[按照卷积核窗口的最后一个像素为标准移动，一直移动到图片的最后一个像素]
步长为1时，经过卷积层后的像素大小计算过程为，由于卷积核为5*5,那么图片的前5*5个像素是第1个点，然后向右移动一步则第2个到第6个像素的5*5个像素变成第2个点，以此类推，则从第5个像素移动到第100个像素共有100-5+1=96个，即卷积层后图片变为了96*96，这是步长为1的情况。
步长为2时：是第5,7,9,11,...,99。总共移动了(99-5)/2+1=48次，即图片由100*100变为了48*48了。这里没考虑第100个像素，因为步长为2，最后只剩一列了，组合不了5*5，只有4*5.填充什么的我不考虑。
步长为3时，按照上面的方法就行了。5,8,11,...,98。。。核窗口的最后一个像素总共移动了(98-5)/3+1=32次，卷积或者池化后的尺寸为32*32
对于书中讲的池化层，比如2*2的池化窗口并没有重叠的，那是因为池化的步长为2.如果池化窗口为3*3,步长为3，那也是没有重叠的.
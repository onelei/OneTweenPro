# OneTweenPro：OneTween Pro版

OneTweenPro不仅包含了OneTween的所有功能，同时包含了DOTween的所有功能。目前来说基本上能满足市面上所有Tween的功能，下面将详细列出。

![160x160](./Doc/160x160.png)

[OneTweenPro]( https://assetstore.unity.com/packages/slug/180185
) 是一个更方便高效的无GC的Unity下的Tween动画插件。不仅仅所见即所得，同时包含了市面主流Tween的功能。

![420x280](./Doc/420x280.png)

## 特点

OneTweenPro 不仅包含OneTween的所见即所得等所有功能，同时还有如下的独特之处： 

- 支持DOMove、DOMoveX、DOMoveY、DOMoveZ、DOLocalMove、DOLocalMoveX、DOLocalMoveY、DOLocalMoveZ。
- 支持DOMove传入多个目标点，设置单个移动结束的回调和整体移动结束的回调。 
- 支持DOAlpha。
- 支持DORotation、DORotationX、DORotationY、DORotationZ、DOLocalRotation、DOLocalRotationX、DOLocalRotationY、DOLocalRotationZ。
- 支持DOLocalScale、DOLocalScaleX、DOLocalScaleY、DOLocalScaleZ。
- 整个Tween动画播放过程0GC
- 包含完整的代码和示例场景。

## 使用

1.如果需要使用OneTween的相关所见即所得的功能需要将脚本挂在某个Transform下面。

2.如果需要使用DOMove等DO相关功能，transform组件下扩展出来了，可以直接使用。

下面通过几个简单的示例演示一下如何使用。

### DOMove

如果仅仅想设置移动到某个点直接Transform下面调用DOMove或者DOLocalMove即可

```c#
transform.DOLocalMove(new Vector3(2000, 2000, 2000), 1, () =>
{
    Debug.Log("DOLocalMove Complete.");
}
```

```c#
transform.DOMove(new Vector3(4000, 4000, 4000), 1, () =>
{
    Debug.Log("DOMove Complete.");
}
```

第一个参数是目标点坐标。

第二个参数是所需要的时间（单位:秒）。

第三个参数是移动结束之后的回调。

当然如果仅仅想设置单个XYZ的坐标，也有对应的函数

```c#
transform.DOLocalMoveX(1000, 1, () =>
{
     Debug.Log("DOLocalMoveX Complete.");
}
                       
transform.DOLocalMoveY(1000, 1, () =>
{
     Debug.Log("DOLocalMoveY Complete.");
}
                                              
transform.DOLocalMoveZ(1000, 1, () =>
{
     Debug.Log("DOLocalMoveZ Complete.");
}
                       
                       
transform.DOMoveX(1000, 1, () =>
{
     Debug.Log("DOMoveX Complete.");
}
                       
transform.DOMoveY(1000, 1, () =>
{
     Debug.Log("DOMoveY Complete.");
}
                                              
transform.DOLocalMoveZ(1000, 1, () =>
{
     Debug.Log("DOLocalMoveZ Complete.");
}
```

当然也可以传入多个目标点

```c#
    void TestDOMoveTargets()
    {
        transform.DOMove(new List<Vector3>()
        {
            new Vector3(0, 0, 0),
            new Vector3(10, 10, 10),
            new Vector3(20, 20, 20),
            new Vector3(30, 30, 30),
        },
        10f,
        () =>
        {
            Debug.Log("One target finish.");
            Debug.Log(transform.position);
        },
        () =>
        {
            Debug.Log("All targets finish.");
            Debug.Log(transform.position);
        });
    }
```
### Append

如果想要顺序播放几个不同的Tween动画使用Sequence

```c#
        void TestAppend()
        {
            var sequence = new OneTweenSequence();

            sequence.Append(
                transform.DOLocalMoveX(1000, 1, () =>
                {
                    Debug.Log("DOLocalMoveX Complete.");
                })
            );

            sequence.Append(
                 transform.DOLocalMoveY(1000, 1, () =>
                {
                    Debug.Log("DOLocalMoveY Complete.");
                })
            );

            sequence.Append(
                transform.DOLocalMoveZ(1000, 1, () =>
                {
                    Debug.Log("DOLocalMoveZ Complete.");
                })
            );

            sequence.Append(
                transform.DOLocalMove(new Vector3(2000, 2000, 2000), 1, () =>
                {
                    Debug.Log("DOLocalMove Complete.");
                })
            );

            sequence.Append(
                transform.DOMove(new Vector3(4000, 4000, 4000), 1, () =>
                {
                    Debug.Log("DOMove Complete.");
                })
            );
        }
```



### 动画组件

OneTweenPosition：控制Position的动画组件。

![OneTweenPosition](./Doc/OneTweenPosition.png)

OneTweenRotation：控制Rotation的动画组件。

![OneTweenRotation](./Doc/OneTweenRotation.png)

OneTweenScale：控制Scale的动画组件。

![OneTweenScale](./Doc/OneTweenScale.png)

OneTweenAlpha：控制Alpha的动画组件。

![OneTweenScale](./Doc/OneTweenAlpha.png)

OneTweenGroup：可以设置动画的Group组，做到按不同的组进行播放。

![OneTweenGroup](./Doc/OneTweenGroup.png)

OneTween还支持代码设置播放结束的回调函数。

## 安装

在 “Assets/OneTweenPro” 文件夹里面包含了所有的 OneTweenPro代码. 你可以把 OneTweenPro 文件夹放在 Assets 文件夹下面的任意位置。

## 文档

[PDF](./Doc/README.pdf)

## Release 版本

### 1.0.0

Init release 

## 联系

更多信息可以进入网站:   https://assetstore.unity.com/packages/slug/180185

Email: 936496193@qq.com
# 将latex编写的毕业论文转换成word格式

你还在为知网查重的论文格式发愁吗？也许下面的方法会帮到你&#x1F609;

## 所需材料

1. 利用模板[ucasthesis]模板撰写的pdf文件；
2. Adobe Acrobat Pro DC。点[这里][adobe]可以下载试用版；
3. 四款adobe字体：

    - AdobeSongStd-Light;
    - AdobeFangSongStd-Regular;
    - AdobeKaitiStd-Regular;
    - AdobeHeitiStd-Regular.
    
    如果电脑中没有安装上述字体，之后编译阶段会提示报错，可以点击[这里][ziti]下载安装。

## 步骤

1. 打开ucasthesis模板Style文件夹中的artratex.sty文件，定位到222行，你将看到如下代码
    ```tex
    \ifartx@windows%
        \setCJKmainfont[AutoFakeBold,ItalicFont=KaiTi]{SimSun}%
        \setCJKsansfont[AutoFakeBold]{SimHei}%
        \setCJKmonofont{FangSong}%
    \else\ifartx@mac%
        \setCJKmainfont[ItalicFont=Kaiti SC,BoldItalicFont=Kaiti SC Bold]{Songti SC Light}%
        \setCJKsansfont{Heiti SC}%
        \setCJKmonofont{STFangsong}%
    \else\ifartx@adobe%
        \setCJKmainfont[AutoFakeBold,ItalicFont=AdobeKaitiStd-Regular]{AdobeSongStd-Light}%
        \setCJKsansfont[AutoFakeBold]{AdobeHeitiStd-Regular}%
        \setCJKmonofont{AdobeFangsongStd-Regular}%
    \fi
    ```
2. 将 *@adobe* 后的字体配置替换掉你所用操作系统后的字体配置，例如，如果你使用的windows系统，那么就把 *@adobe* 后的字体配置复制到 *@windows*后面，然后把 *@Windows* 后的字体配置注释掉，结果应如下面的代码所示：
    ```tex
    \ifartx@windows%
        %\setCJKmainfont[AutoFakeBold,ItalicFont=KaiTi]{SimSun}%
        %\setCJKsansfont[AutoFakeBold]{SimHei}%
        %\setCJKmonofont{FangSong}%
        \setCJKmainfont[AutoFakeBold,ItalicFont=AdobeKaitiStd-Regular]{AdobeSongStd-Light}%
        \setCJKsansfont[AutoFakeBold]{AdobeHeitiStd-Regular}%
        \setCJKmonofont{AdobeFangsongStd-Regular}%
    \else\ifartx@mac%
        \setCJKmainfont[ItalicFont=Kaiti SC,BoldItalicFont=Kaiti SC Bold]{Songti SC Light}%
        \setCJKsansfont{Heiti SC}%
        \setCJKmonofont{STFangsong}%
    \else\ifartx@adobe%
        \setCJKmainfont[AutoFakeBold,ItalicFont=AdobeKaitiStd-Regular]{AdobeSongStd-Light}%
        \setCJKsansfont[AutoFakeBold]{AdobeHeitiStd-Regular}%
        \setCJKmonofont{AdobeFangsongStd-Regular}%
    \fi
    ```
3. 使用xelatex引擎编译生成pdf文件。如果你安装过上文提到的四款字体，那么应该会正常编译通过，否则就按照编译器的错误提示安装相应字体；
4. 使用Adobe Acrobat Pro DC将生成的pdf文件转化为word。

如果你严格按照上述过程做，那么你将得到一个说的过去的word文件，相信应对查重应该是没问题了&#x1F389;

## 后记

下面列举了此方法可转化与不可转化的内容。

### 可以转化的内容
 1. 封面、摘要、原创声明、参考文献、致谢的内容与格式；
 2. 正文内容以及章节段落格式；
 3. 不包含分数如$\frac{a}{b}$以及积分、求和符号$\int$、$\sum$的公式，格式与编号均可以保留；
 4. 图片与表格的内容与格式；
 5. 页眉的内容与格式。

### 不能完美转化的内容
1. 目录；
2. 公式中的：
    - 分数$\frac{a}{b}$；
    - 积分符号$\int$；
    - 求和符号$\sum$；
    - 矩阵
        $$\begin{pmatrix}a&b\\c&d\end{pmatrix}$$
3. 页脚、脚注会被识别为正文。


## 私获&#x1F440;
由于查重要求去除封面原创声明等，我个人写了一个符合查重要求的主文件，下载该文件夹下的[thesisplain.tex][plain]文件并复制到ucasthesis文件夹下，打开该文件，用相同方法编译产生pdf，再按照前面的方法转为word即可。此方法可省去手动删除封面原创声明的麻烦。



>如遇问题，可以通过
>- QQ：1715260664
>- 微信：13051572393
>- 邮箱：shaoyuelinphysics@gmail.com
>
>联系我，但我也不保证可以解决&#x1F602;








[ucasthesis]:https://github.com/mohuangrui/ucasthesis
[adobe]:https://acrobat.adobe.com/cn/zh-Hans/free-trial-download.html
[ziti]:https://pan.baidu.com/s/1IRkPcYkpZwOlP0hFEejuAw
[plain]:./thesisplain.tex
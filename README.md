# 更好的中文文案排版
 
统一中文文案、排版的相关用法，降低团队成员之间的沟通成本，增强网站气质。

## 安装
使用 composer 安装：
```bash
composer install jxlwqq/chinese-typesetting
```

## 使用

### 添加空格

```php
use Jxlwqq\ChineseTypesetting\ChineseTypesetting;

$chineseTypesetting = new ChineseTypesetting();

$text = '今天，我在Apple Store上购买了一台13英寸MacBook Pro笔记本电脑，花费了14188元。';
$chineseTypesetting->insertSpace($text);
// 今天，我在 Apple Store 上购买了一台 13 英寸 MacBook Pro 笔记本电脑，花费了 14188 元。。

$text = '这一方法通过将不同目的基因的末端与一个小的β-galactosidase融合。';
$chineseTypesetting->insertSpace($text);
// 这一方法通过将不同目的基因的末端与一个小的 β-galactosidase 融合。
```

在中文与英文字母/用于数学、科学和工程的希腊字母/数字之间添加空格。 参考依据：[中文文案排版指北：空格
](https://github.com/mzlogin/chinese-copywriting-guidelines#空格)。

目前，比较主流的是约定是在中文与英文之间添加空格，我在此基础上，增加了对用于数学、科学和工程的希腊字母的支持，更加方便使用。

### 全角转半角
```php
use Jxlwqq\ChineseTypesetting\ChineseTypesetting;

$chineseTypesetting = new ChineseTypesetting();

$text = '这个名为 ＡＢＣ 的蛋糕只卖 １０００ 元。';
$chineseTypesetting->full2Half($text);
// 这个名为 ABC 的蛋糕只卖 1000 元。
```
有限度的全角转半角（英文、数字、百分号、空格等使用半角字符）。参考依据：[中文文案排版指北：全角和半角](https://github.com/mzlogin/chinese-copywriting-guidelines#全角和半角)。

### 清除 HTML 标签的样式
```php
use Jxlwqq\ChineseTypesetting\ChineseTypesetting;

$chineseTypesetting = new ChineseTypesetting();

// 清除 Class 属性
$text = '<p class="class-name"></p>';
$chineseTypesetting->removeClass($text);

// 清除 ID 属性
$text = '<p id="id-name"></p>';
$chineseTypesetting->removeId($text);

// 清除 Style 属性
$text = '<p style="color: #FFFFFF;"></p>';
$chineseTypesetting->removeStyle($text);
```
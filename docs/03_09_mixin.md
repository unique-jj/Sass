# Sass Reference


## Mixins -1��

* Defining a Mixin: @mixin
* Including a Mixin: @include
* Arguments
	- Keyword Arguments
	- Variable Arguments
* Passing Content Blocks to a Mixin
* Variable Scope and Content Blocks

---

�ͽ����� Sass ��� ��ü���� ���� ���� ���Ǵ� ��� �� �ϳ��̸�, ���뼺�� DRY ���۳�Ʈ�� �ٽ��Դϴ�.   
Mixin�� ��Ÿ�Ͻ�Ʈ ���� �����ϰ� ���� style�� ������ �� �ֽ��ϴ�. 
�ͽ����� CSS ��Ģ�� Sass �������� ���Ǵ� ���� ��� ���� ������ �� �ֽ��ϴ�. 
�Լ�ó�� �Ű������� ���� ���� �ְ�, vendor prefixes�� ������ ������ �� �ֽ��ϴ�.
�Ʒ���  border-radius �� ���� �����Դϴ�.

```SCSS 

// _style.scss
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }

```
mixin�� ����Ϸ��� ���� @mixin ���þ �����ϰ� �̸��� �����մϴ�.   
���ÿ��� border-radius ��� �̸��� �����߽��ϴ�.    
�ڹٽ�ũ��Ʈ �Լ� ���𹮰� ����� �����ε�, �̸� ���� �Ұ�ȣ �ȿ��� `$radius`��� ������ �����߽��ϴ�.    

���� ���� `.box`��� Ŭ������ border-radius �Ӽ��� ����ϱ� ����, ������ `border-radiu` mixin�� ȣ���մϴ�. ȣ�� �� ���� `@include` �ڿ� ������ mixin �̸��� �����ϰ�, �Ұ�ȣ �ȿ��� ���� �����մϴ�.
�Ʒ��� Css�� ��ȯ�� ������Դϴ�.

```css

/* style.css */
 
.box {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}

```

####Including a Mixin: @include

���� ������ ��� @include�� {} �ȿ� �����ؼ� �Ӽ��� ��ü�ϴ� mixin�� Ȯ���ϼ̽��ϴ�.
�Ӽ��Ӹ� �ƴ϶� �����ڸ� ������ ���� ��ü�� mixin���� ������ ���� �ֽ��ϴ�. 


```SCSS 

// _style.scss
@mixin silly-links {
  a {
    color: blue;
    background-color: red;
  }
}

@include silly-links;

```
```css

/* style.css */
 
a {
  color: blue;
  background-color: red; }

```

�� mixin �ȿ� �ٸ� mixin�� ������ �� �� �ֽ��ϴ�. 
```SCSS 

// _style.scss
@mixin compound {
  @include highlighted-background;
  @include header-text;
}

@mixin highlighted-background { background-color: #fc0; }
@mixin header-text { font-size: 20px; }

```
####���� ����(Arguments)

@mixin�ͽ� ���� ���� �� ��, ���ڴ� ��� ������ ���� ��ȣ �ȿ���, ��ǥ�� �����Ͽ� ���� �̸����� ��ϵ˴ϴ�.

```SCSS 

/// _style.scss
@mixin sexy-border($color, $width) {
  border: {
    color: $color;
    width: $width;
    style: dashed;
  }
}

p { @include sexy-border(blue, 1in); }

```

```css

/* style.css */
 
p {
  border-color: blue;
  border-width: 1in;
  border-style: dashed; }

```

@mixin�� default value�� �����Ͽ� ��뵵 �����մϴ�. ���� ���� ���ǵǴ� value�� ���� ��� default value ����, ���� ���ǵ� ���� ������쿣 ���ǵ� ���� ����˴ϴ�.

```SCSS 

// _style.scss
@mixin sexy-border($color, $width: 1in) {
  border: {
    color: $color;
    width: $width;
    style: dashed;
  }
}
p { @include sexy-border(blue); }
h1 { @include sexy-border(blue, 2in); }

```
```css

/* style.css */
 
p {
  border-color: blue;
  border-width: 1in;
  border-style: dashed; }

h1 {
  border-color: blue;
  border-width: 2in;
  border-style: dashed; }
```

#####Keyword Arguments(Ű���� ����)
mixin�� argument�� �����Ҷ� ������ �ƴ϶� �ش� Ű���嵵 �Բ� ���� �� �� �ֽ��ϴ�. ���� ���� �Ʒ�ó�� ������ �����մϴ�. 
```SCSS 

// _style.scss
 
p { @include sexy-border($color: blue); }
h1 { @include sexy-border($color: blue, $width: 2in); }
```

#####Variable Arguments(���� ����)

argument�� ���� ���������� ���� ��� argument �ڿ� `...` �� �������μ� �������� ���� ������ �� �ֽ��ϴ�. 

```SCSS 

// _style.scss
 
@mixin box-shadow($shadows...) {
  -moz-box-shadow: $shadows;
  -webkit-box-shadow: $shadows;
  box-shadow: $shadows;
}

.shadows {
  @include box-shadow(0px 4px 5px #666, 2px 6px 10px #999);
}
```
```css

/* style.css */
 
.shadows {
  -moz-box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
  -webkit-box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
  box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
}
```
������ ȣ���϶��� argument �� ����� �� �ֽ��ϴ�. ���� list �� map�� Ȯ�� �� �� �ֽ��ϴ�.

```SCSS 

// _style.scss
 
@mixin box-shadow($shadows...) {
  -moz-box-shadow: $shadows;
  -webkit-box-shadow: $shadows;
  box-shadow: $shadows;
}

.shadows {
  @include box-shadow(0px 4px 5px #666, 2px 6px 10px #999);
}
```

```css

/* style.css */
 
.shadows {
  -moz-box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
  -webkit-box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
  box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
}

```
###Mixin���� Content Blocks�� ���

@ content �����ڸ� ����� ��Ÿ�� ��� ��ü�� mixin���� �ѱ� �� �ֽ��ϴ�. 
Sass�� �������� �ϸ鼭 �� ����� mixin�� ȣ���ϴ� ���� �ȿ� �ٽ� �ֽ��ϴ�. 

```SCSS 

// _style.scss
 
@mixin apply-to-ie6-only {
  * html {
    @content;
  }
}
@include apply-to-ie6-only {
  #logo {
    background-image: url(/logo.gif);
  }
}

```
�� ���� @content���� ` #logo {background-image: url(/logo.gif);}` �� ����� �ֽ��ϴ�.

```css

/* style.css */
 
* html #logo {
  background-image: url(/logo.gif);
}

```
���� ������ `.sass` ���� �Ʒ��� ���� ǥ���˴ϴ�.

```sass

// _style.sass
 
=apply-to-ie6-only
  * html
    @content

+apply-to-ie6-only
  #logo
    background-image: url(/logo.gif)

```

#### ���� ����(Variable Scope) �� Content Blocks

�ͽ� �ο� ���� �� @content��  @content�� ���� �ͽ� ���� ���� ������ ���� �� �������� ����˴ϴ�. �̰��� �ͽ� ���� ���� �������� ���޹��� ���� @content���� ����� �� ���ٴ� ���� �ǹ��մϴ�.

```SCSS 
@content�� mix
// _style.scss
 
$color: white;
@mixin colors($color: blue) {
  background-color: $color;
  @content;
  border-color: $color;
}
.colors {
  @include colors { color: $color; }
}
```

```css

/* style.css */
 
.colors {
  background-color: blue;
  color: white;
  border-color: blue;
}

```

>mixin�� �⺻���� ���� ���ڸ� ������ �� ��쿡 mixin�� ȣ���ϴ� ������ ���ڰ��� ������ ���� ������ ������ ���Ƿ� ���Ǹ� ��￩�� �Ѵ�.


������ mixin���� �����Ҽ� �ִٰ� �ؼ� ���ϰ� �����ϴ� ���� �����ʽ��ϴ�.  �����Ҷ��� 20�� �̳��� ������ �����ϱ� �����մϴ�. ������ vendor prefixes�� ��쿡�� _Autoprefixer_�� ����ϸ� �׻� �ֽ� ������ �ݿ����ְ�, Sass�� �ڵ带 �ٿ� �ټ� ������, �������� vendor prefixes�� �����ϴ°��� �������� �ʽ��ϴ�. 

* [mixin ���̵���� ���� ](http://sass-guidelin.es/ko/#mixins)
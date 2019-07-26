# Sass Basic
	
* *�̹����� [sass-guidelin](http://sass-guidelin.es/ko/)�� ������ �����ϰ� �ֽ��ϴ�.*


 ###Preprocessing (��ó��)

Sass(Syntactically Awesome Stylesheets)�� CSS ������ �ִ� ��Ÿ���(meta-language)�� ���� �����ϰ� �ݽ��� ���� CSS ������ ����մϴ�.
����Ʈ���� ���� ��Ģ�� DRY(Don��t Repeat Yourself)�� �����ؼ� �� ������ ȿ�������� �ڵ带 �ۼ��ϰ� ���� �������� �ϵ��� ���ݴϴ�.-�� ���̵� ���ο��� ���ϱ� DRY ���ٵ� KISS ��Ģ (Keep It Simple Stupid)�� �켱 �� �� �ֽ��ϴ�.- ���� Sass�� CSS ��ó����(pre-processor)�Դϴ�. ��Ÿ�Ͻ�Ʈ�� ���������� �ؼ��� CSS���� �߰��� ��ġ�ϴ� �ϳ��� �������� Sass �������� �ۼ��� �ڵ带 �Ϲ������� ����ϴ� CSS �ڵ�� �������� �ݴϴ�.

Sass ������ CSS �ڵ�� ������ �ϴ� ���� �⺻���� ����� `�͹̳�`�� ����ϴ� ���ε�, Sass ��ġ �Ŀ� �͹̳ο��� `sass input.scss output.css`�� �����ϸ� ���� �����̳� ��ü ���丮�� ��ȯ�� �� �ֽ��ϴ� . ��,`--watch`��ɾ �߰��ϸ� ������ ���丮�� �ǽð����� ������ �� �ֽ��ϴ�.    
�Ʒ��� Sass�� ��ü ���丮�� �����ϴ� �����Դϴ�.    

```SCSS

sass --watch app/sass:public/stylesheets

```

<br>
 ###Variables (����)

Sass�� stylesheet ���ݿ� ���� ���� �� ������ �����ϴ� ������� `����`�� ����մϴ�.
�� �������� ����, �۲� ���� �� � Css�� ������ �� ������, ������ ����� ���� `$` ��ȣ�� �̿��մϴ�.

```SCSS

// _style.scss
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}

```
```css

/*style.css*/
body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}

```
��, ������ ���� ���̴� ������ �����ϸ� �ȵ˴ϴ�. CSS���� ���� �̸��� ���� ��ȿ������ ���� ������, �浹�� ���輺�� ���� �����ϴ�. 

<br>
[�������� ���̵���� ����](http://sass-guidelin.es/ko/#section-63) 


<br>
 ### Nesting (��ø)

Sass�� �̿��ϸ� HTML�� div �ȿ� div�� �ִ´ٴ��� �ϴ� ��ø �� ��������ó�� CSS�����ڸ� ��ø�� �� �ֽ��ϴ�.    
��, ����ģ ��ø�� �����ؾ��մϴ�. ����ģ ��ø�� CSS�� �����Ͻ� ������ �߻��� �� ������, ������ �������� ����߸� �� �ֽ��ϴ�.    
�Ʒ��� �����ϰ� ��ø�� *navigation style* ���Դϴ�.

```SCSS

// _style.scss
nav {
	ul {
		margin: 0;
		padding: 0;
		list-style: none;
	}

	li { display: inline-block; }

	a {
		display: block;
		padding: 6px 12px;
		text-decoration: none;
	}
}

```
nav�ȿ� ul, li, a selector�� �ִ� ���� �� �� �ֽ��ϴ�.    
�̷� ��쿡 ��ø ����� ����ϸ�  CSS�� �����ϰ� �� �б� ���� ���� ���ֽ��ϴ�.

```css
/*styel.css*/
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

nav li {
  display: inline-block;
}

nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}

```

<br>
[��ø���� ���̵���� ����](http://sass-guidelin.es/ko/#nesting)


<br>
 ### Partials

Sass�� �ۼ� �� CSS�� ���� ���������� �����ϴ� partial Sass������ ����� �ٸ� Sass���Ͽ� ���� ��ų �� �ֽ��ϴ�. 

```SCSS

// _reset.scss

html,
body,
ul,
ol {
  margin: 0;
  padding: 0;
}
```
```SCSS

// _base.scss

@import 'reset';

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}

```
Sass ���ϸ� �տ� `_`�� ���̸� CSS�� ��ȯ���� �ʽ��ϴ�. ������ �̿��� ���̵���ο����� `main.scss`�� ������ ��� Sass���ϸ� �տ��� `_`�� ����� ���� �����ϰ� �ֽ��ϴ�.   

<br>
[���� ���̵���� ���� ](http://sass-guidelin.es/ko/#section-54)


<br>
 ### Import (�ҷ�����)

CSS���� @import�� �ٸ� ������ �����ų �� �ֽ��ϴ�. 
SASS������ @import�� ����� �� �ִµ�, CSS�� @import�ʹ� �����̳� �۵� ����� �ٸ��ϴ�.

`.sass` , `.scss` ��� Ȯ���ڸ� �����ϰ� ȣ�Ⱑ���մϴ�. ���� Ȯ���ڸ� �ٿ��� �˴ϴ�.
Ȯ���� ���� ���� �̸������� �������⸦ �ϸ� �� ���� ������ �ִ��� �˻��Ͽ� �����ɴϴ�.
���� ���

```SCSS

@import "inc";

```
�� ���� ������ �ִ��� �˻��մϴ�.

* inc.scss
* inc.sass
* _inc.scss
* _inc.sass

�� �� �� �ϳ��� �����ϸ� �� ������ ��������, ���� ������ �����ϸ� ��ȯ �� ������ ���ϴ�.    
SASS ������ �����Դٸ�, ������ ���Ͽ� �ִ� ������ Mixin�� ����� �� �ֽ��ϴ�.

```SCSS 

// _rounded.scss

@mixin rounded($side, $radius: 10px) {
  border-#{$side}-radius: $radius;
  -moz-border-radius-#{$side}: $radius;
  -webkit-border-#{$side}-radius: $radius;
}

``` 
```SCSS 

/// _style.scss
@import "rounded";
 
nav li { @include rounded(top); }
footer { @include rounded(top, 5px); }
sidebar { @include rounded(left, 8px); }

```
```css

/* style.css */
 
nav li {
  border-top-radius: 10px;
  -moz-border-radius-top: 10px;
  -webkit-border-top-radius: 10px; }
 
footer {
  border-top-radius: 5px;
  -moz-border-radius-top: 5px;
  -webkit-border-top-radius: 5px; }
 
sidebar {
  border-left-radius: 8px;
  -moz-border-radius-left: 8px;
  -webkit-border-left-radius: 8px; }
```

 ### Mixins

�ͽ����� Sass ��� ��ü���� ���� ���� ���Ǵ� ��� �� �ϳ��̸�, ���뼺�� DRY ���۳�Ʈ�� �ٽ��Դϴ�.   
Mixin�� ��Ÿ�Ͻ�Ʈ ���� �����ϰ� ���� style�� ������ �� �ֽ��ϴ�. 
�ͽ����� CSS ��Ģ�� Sass �������� ���Ǵ� ���� ��� ���� ������ �� �ֽ��ϴ�. 
�Լ�ó�� �Ű������� ���� ���� �ְ�, vendor prefixes�� ������ ������ �� �ֽ��ϴ�.
�Ʒ���  border-radius �� ���� �����Դϴ�.

```SCSS 

/// _style.scss
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
������ mixin���� �����Ҽ� �ִٰ� �ؼ� ���ϰ� �����ϴ� ���� �����ʽ��ϴ�.  �����Ҷ��� 20�� �̳��� ������ �����ϱ� �����մϴ�. ������ vendor prefixes�� ��쿡�� _Autoprefixer_�� ����ϸ� �׻� �ֽ� ������ �ݿ����ְ�, Sass�� �ڵ带 �ٿ� �ټ� ������, �������� vendor prefixes�� �����ϴ°��� �������� �ʽ��ϴ�. 

[mixin ���̵���� ���� ](http://sass-guidelin.es/ko/#mixins

### Extend/Inheritance (Ȯ��/���)
`@extend`�� ����ϸ� �̸� ���ǵ� �ٸ� Css ������ ��� ���� �� �ֽ��ϴ�. �Ʒ��� .success, .error, .warning ���� �޼��� �Ӽ��� `@extend`�� ����Ͽ� ������ ������ �����Դϴ�. 

```SCSS 

/// _style.scss
.message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  @extend .message;
  border-color: green;
}

.error {
  @extend .message;
  border-color: red;
}

.warning {
  @extend .message;
  border-color: yellow;
}

```
�� ���þ�� �ߺ��ؼ� �����ؾ��ϴ� Ŭ���� ���� ���� �����ϰ� ������ �� �ֽ��ϴ�. 

```css

/* style.css */
 
.message, .success, .error, .warning {
  border: 1px solid #cccccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}

.warning {
  border-color: yellow;
}

```
�� ����� �˾ƴ� �ε�, �ǵ��� ����� �����ϱ� �����մϴ�. 
��ӿ� ���, �� �� ��Ӿȿ� ����� �ع����ٰų� �ϴ� ��쿣 �ڵ尡 �Ƿ� �� �������� �Ӵ���, ���� �����ϰ��� �ߴ� �Ӽ��� ã�ư��� �� ������� ���� �ֽ��ϴ�. 

�� `@extend`�� `@media` block �ȿ����� ����� �۵����� �ʽ��ϴ�. 
[extend ���̵���� ���� ](http://sass-guidelin.es/ko/#extend)


<br>
### Operators (����)
Sass������ `+, -, *, /, %`���� ������ ��Ģ����� (>, <, ==, >-, <=, !=)���� �񱳿���,  �������� ���� �����մϴ�.
�Ʒ��� width���� �˾Ƴ��� ���� ������ ���� �����Դϴ�.

```SCSS 

/// _style.scss
.container { width: 100%; }


article[role="main"] {
  float: left;
  width: 600px / 960px * 100%;
}

aside[role="complimentary"] {
  float: right;
  width: 300px / 960px * 100%;
}

```
������ ����ϸ� ��� ���� ��ġ���� ������ �ʿ� ���� ������ ���������� �̾Ƴ� �� �ֽ��ϴ�.
���ù������� `container`Ŭ������ `width`�Ӽ��� �����Ѵٸ� `article,aside`�� ���� �ڵ����� �ݿ��Ǿ� ����˴ϴ�.
���������� �ξ� �������� �� �ֽ��ϴ�.

```css

/* style.css */
 
.container {
  width: 100%;
}

article[role="main"] {
  float: left;
  width: 62.5%;
}

aside[role="complimentary"] {
  float: right;
  width: 31.25%;
}

```







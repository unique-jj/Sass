# Sass Reference

##7. @-Rules and Directives
- @import
- @media
- @extend
- @at-root
- @debug & @warn &@error

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
<br>
#### Partials 

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

* [���� ���̵���� ���� ](http://sass-guidelin.es/ko/#section-54)


<br>
###@media

@media�� Css���� ���ǵǾ��ִ� �̵�� ���� �Դϴ�. Sass���� @media�� ������ Ŭ���� ������̵� �ش��ϴ� Ŭ���� �ȿ� �ٷ� ������ �� �ֽ��ϴ�. �̷μ� ���� �����ڸ� �ݺ��ϰų� ��Ÿ���� �ۼ��� �ߴ��� �ʿ���� media ���� ��Ÿ���� �ٷ� �߰��� �� �ֽ��ϴ�. 

```SCSS 

/// _style.scss
.sidebar {
  width: 300px;
  @media screen and (orientation: landscape) {
    width: 500px;
  }
}

```

```css

/* style.css */
 
.sidebar {
  width: 300px; }
  @media screen and (orientation: landscape) {
    .sidebar {
      width: 500px; } }

```
@media�� ������ ���� ��ø �� ���� �ֽ��ϴ�.

```SCSS 

/// _style.scss
@media screen {
  .sidebar {
     height:300px
    @media (orientation: landscape) {
      width: 500px;
    }
  }
}

```

```css

/* style.css */

@media screen {
  .sidebar {
    height: 300px;
  }
}
@media screen and (orientation: landscape) {
  .sidebar {
    width: 500px;
  }
}

```
����������, @media ������ ��� �̸��� Ư�� ��ſ�  SassScript��(����, �Լ� �� ������ ����)�� ���� �� �� �ֽ��ϴ�. 

```SCSS 

/// _style.scss
$media: screen;
$feature: -webkit-min-device-pixel-ratio;
$value: 1.5;

@media #{$media} and ($feature: $value) {
  .sidebar {
    width: 500px;
  }
}

```

```css

/* style.css */

@media screen and (-webkit-min-device-pixel-ratio: 1.5) {
  .sidebar {
    width: 500px; } }

```

<br>
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

* [extend ���̵���� ���� ](http://sass-guidelin.es/ko/#extend)


####Multiple Extends
�ϳ��� �����ڴ� �ϳ��̻����� �����ڸ� Ȯ���� �� �ֽ��ϴ�.
��, ��� Ȯ��� �����ڿ��� ��Ÿ�ϸ� ����Ѵٴ� �ǹ��Դϴ�.

```SCSS 

// _style.scss
.error {
    border: 1px #f00;
    background-color: #fdd;
}

.attention {
    font-size: 3em;
    background-color: #ff0;
}

.seriousError {
  @extend .error;
  @extend .attention;
  border-width: 3px;
}

```

```css

/* style.css */
.demo-01 {
    border: 1px #f00;
    background-color: #fdd;
}

.demo-02 {
    @extend .demo-01;
    border-width: 3px;
}

.demo-03 {
    @extend .demo-02;
    position: fixed;
    top: 10%;
    bottom: 10%;
    left: 10%;
    right: 10%;
}
```

�׸��� @extend .error; @extend .attention; �� �����ڵ��� �׸��� �޸��� �����Ͽ� ������ ���� �� �� �ֽ��ϴ�.    
@extend .error, attention;

####���� Extends
�Ѱ��� �����ڴ� ���ʷ� ����°�� Ȯ��� �ٸ� �����ڸ� Ȯ���ϴ� ���� �����մϴ�.

```SCSS
/* style.css */
.demo-01 {
    border: 1px #f00;
    background-color: #fdd;
}

.demo-02 {
    @extend .demo-01;
    border-width: 3px;
}

.demo-03 {
    @extend .demo-02;
    position: fixed;
    top: 10%;
    bottom: 10%;
    left: 10%;
    right: 10%;
}
```

```css
/* style.css */
.error, .seriousError, .criticalError {
  border: 1px #f00;
  background-color: #fdd; }

.seriousError, .criticalError {
  border-width: 3px; }

.criticalError {
  position: fixed;
  top: 10%;
  bottom: 10%;
  left: 10%;
  right: 10%; }
```

####������ ����

.foo .bar �Ǵ� .foo + .bar ���� ������ �迭�� ���� Ȯ�� �� �� �����ϴ�.     
 ��ø �� �����ڴ� ��ü�� `,`�� @extend ����ϱ� ���ؼ��� �����մϴ�.

```SCSS
/* style.css */
#fake-links .link {
  @extend a;
}

a {
  color: blue;
  &:hover {
    text-decoration: underline;
  }
}
```

```css
/* style.css */
a, #fake-links .link {
  color: blue; }
  a:hover, #fake-links .link:hover {
    text-decoration: underline; }
```

#####������ ���� ����

������ ���� ������ �ٸ� ������ ��Ÿ��, �ٸ� �����ڸ� Ȯ���մϴ�. �� ���, �� ������?? ���� �� �ʿ䰡�ֽ��ϴ�.

```SCSS
/* style.css */
#admin .tabbar a {
  font-weight: bold;
}
#demo .overview .fakelink {
  @extend a;
}
```

���յǴ� �����ڿ��� ���� �����ڰ� ���� ��� �ΰ��� ���ο� �����ڰ� �����˴ϴ�. 

```css
/* style.css */
#admin .tabbar a,
#admin .tabbar #demo .overview .fakelink,
#demo .overview #admin .tabbar .fakelink {
  font-weight: bold; }
```
�� �����ڰ� �Ϻ� �����ڸ� ������ ���, ���� �����ڴ� ���յ�����, ������ �ٸ� ����� ���� �߻��ϹǷ� �Ʒ��� ���� ������ �����˴ϴ�. 
```SCSS
/* style.css */
#admin .tabbar a {
  font-weight: bold;
}
#admin .overview .fakelink {
  @extend a;
}
```

```css
/* style.css */
#admin .tabbar a,
#admin .tabbar .overview .fakelink,
#admin .overview .tabbar .fakelink {
  font-weight: bold;
```


####@extend-Only Selectors (%foo)


```SCSS
/* style.css */
// �̰��� �� ��ü�δ� ��µ��� �ʽ��ϴ�. 
#context a%extreme {
  color: blue;
  font-weight: bold;
  font-size: 2em;
}
```

```SCSS
/* style.css */
.notice {
  @extend %extreme;
}
```

```css
/* style.css */
#context a.notice {
  color: blue;
  font-weight: bold;
  font-size: 2em; }
```

#### !optional Flag
!optional �� @extend ��� ��,����� �����ڰ� �������� ���� ��� '�ɼ�' ó���Ͽ� ������ �߻���Ű�� �ʵ��� �� �� �ֽ��ϴ�.

```SCSS
/* style.css */
//   ���� ������ .btn-link ��� �Ѵٸ�
.btn-link {
  background-color: #fff;
  font-weight: bold;
  padding: 10px;
  color: #000;
}

.btn-link-01 {
  @extend .btn-link-01 !optional; 
  // .btn-link-01 Ŭ������ ������� ��� �Ͽ����� .btn-link-01 �����ڰ� ��� ������ �߻����� �ʴ´�.
  background-color: red;
  .decs & {
    background-color: darken(red, 20%);
  }
}

```

<br>
###@at-root

@at-root ���þ�� �ϳ� �̻��� ��Ģ�� �θ� ������ �Ʒ� ��ø���� �ʰ� document root�� ��µ˴ϴ�.

```SCSS 

/// _style.scss
.parent {
  background:#ddd;
  
  @at-root {
    .child1 {
      font-size: 12px;
    }
    .child2 {
      padding: 10px;
    }
  }
  .step-child {
    color: #c4c4c4;
  }
}

```

```css

/* style.css */
.parent {
  background: #ddd;
}
.child1 {
  font-size: 12px;
}

.child2 {
  padding: 10px;
}
.parent .step-child {
  color: #c4c4c4;
}

```

#### @at-root (without: ...) �� @at-root(with: ...) 

�⺻������ @at-root�� �ܼ��� �θ����ڸ� ����������  @media�� ���� ��ø�� ���þ��� ������ �ű�� �͵� �����մϴ�.

```
// _style.scss
@media print {
  .page {
    width: 8in;
    @at-root (without: media) {
      color: red;
    }
    @at-root (without: page) {
      .number{
        color: red;
      }
    }
  }
}

```

```css

/* style.css */
@media print {
  .page {
    width: 8in;
  }
}
.page {
  color: red;
}
@media print {
  .page .number {
    color: red;
  }
}

```


<br>
###@debug & warn & @error

@debug, @warn ���þ�� ǥ�� ���� ��� ��Ʈ���� SassScript ���� ���� ����մϴ�.

 @warn �� @debug���̿� �� ���� �߿��� �������� �ֽ��ϴ�.

  1. `--quie` �Ǵ� `:quiet` �ɼ����� @warn�� ������ �� �ֽ��ϴ�.
  2. @warn��쿡�� stylesheet���� ����� ������ �� ��ġ�� ������ �޽����� ����������� @debug�� cmd �� �͹̳ο��� ��µ˴ϴ�.  

```SCSS
// _style.scss
@debug 10em + 12em;

```

```css

/* style.css */
Line 1 DEBUG: 22em

```
```
// _style.scss
@debug 10em + 12em;

```

```cmd
Line 1 DEBUG: 22em

```


```SCSS
@mixin adjust-location($x, $y) {
  @if unitless($x) {
    @warn " #{$x} �� px�� �ִٰ� ���� ";
    $x: 1px * $x;
  }
  @if unitless($y) {
    @warn " #{$y} �� px�� �ִٰ� ���� ";
    $y: 1px * $y;
  }
  position: relative; left: $x; top: $y;
}
```
@error ���þ�� ġ������ ������ ���� SassScript���� ���� ����մϴ�. �װ��� mixin�� �Լ��� ���ڸ� �����ϱ⿡ �����մϴ�. 

```SCSS
@mixin adjust-location($x, $y) {
  @if unitless($x) {
    @error "$x may not be unitless, was #{$x}.";
  }
  @if unitless($y) {
    @error "$y may not be unitless, was #{$y}.";
  }
  position: relative; left: $x; top: $y;
}
```
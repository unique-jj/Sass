# Sass Reference

##6. SassScript
* Interactive Shell
* Variables: $
* Data Types
* Operations
* Parentheses
* Functions
* Interpolation: #{}
* & in SassScript
* Variable Defaults: !default

---


###Interactive Shell 

  SassScript�� �׽�Ʈ�� ���� ���� ��, terminal(�͹̳�)�̳� cmd ȯ�濡�� -i option�� ��� �� SassScript ǥ������ ���� �ڵ带 �ۼ��Ͽ� ����� Prompt�� ����غ��� �ֽ��ϴ�.

```SCSS

$ sass -i
>> "Hello, Sassy World!"
"Hello, Sassy World!"
>> 1px + 1px + 1px
3px
>> #777 + #777
#eeeeee
>> #777 + #888
white

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
��, ������ ���� ���̴� ������ �����ϸ� �ȵ˴ϴ�. CSS���� ���� �̸��� ���� ��ȿ������ ���� ������, �浹�� ���輺�� Ů�ϴ�. 

* [�������� ���̵���� ����](http://sass-guidelin.es/ko/#section-63)




<br>
### Data Types 

SassScript�� �ϰ������� �⺻ ������ ������ �����մϴ� :

* __���� (numbers)__ - e.g. 1.2, 13, 10px(������ �����Ͽ� ����Ÿ���Դϴ�.)    
* __���ڿ� : ""(�����ǥ), ''(Ȭ����ǥ), ����ǥ�� ���� �͵� ��� ���ڿ��� �ν� (string) __ - e.g. "foo", 'bar', baz)    
* __���� (colors)__ - e.g. blue, #04a3f9, rgba(255, 0, 0, 0.5)    
* __booleans__ - e.g. true, false    
* __nulls__ - e.g. null    
* __list :�ٽ�ũ��Ʈ�� �迭�� �����ϸ� �����̳� ��ǥ(,)�� ���е� ����� ���մϴ� __ - e.g. 1.5em 1em 0 2em, `Helvetica, Arial, sans-serif`    
* __map: Ű: �� ���� ������ �׷����� �ڹٽ�ũ��Ʈ�� ��ü�� �����ϸ� map �� ���õ� �Լ��� ���� ���� �� �ֽ��ϴ�._ - e.g. (key1: value1, key2: value2)    

SassScript�� `Unicode`�� `!important` �� �� ���� CSS �Ӽ� ���� ��� ������ �����մϴ�. �׷���, �̷��� ������ ���� Ư���� ó���� �����ϴ�.
�׵��� ���� �ο���� ���� ���ڿ�ó�� ����ϰ� �ֽ��ϴ�.

#### Strings
CSS 2���� ���ڿ��� ���� : `"Lucida Grande"` �Ǵ� `'http://sass-lang.com'` �� ���� �ο� ��ȣ�� ������ ��, `sans-serif` �Ǵ� `bold` ���� �ο� ��ȣ������ ��. SassScript�� �Ϲ������� SassScript���� ���Ǵ� ���ڿ�, CSS�� ������ �� ���Ǵ� ���ڿ��� �������� �ν��մϴ�.

�׷��� �ϳ��� ���ܴ� �ֽ��ϴ�.: [#{}������](#)�� ����� ��, ����ǥ�� �ѷ�����(�ο��ȣ�� ����) ���ڿ��� ����ǥ�� �ѷ��ο� ���� �ʽ��ϴ�. �̰��� mixin �ȿ��� ������ �̸��� ����� �� �װ��� ���� ����� �� �ֵ��� ���ݴϴ�.

```SCSS

// _style.scss
@mixin firefox-message($selector) {
  body.firefox #{$selector}:before {
    content: "Hi, Firefox users!";
  }
}

@include firefox-message(".header");

```
```css

/*style.css*/
body.firefox .header:before {
  content: "Hi, Firefox users!"; }
}

```


#### Lists

List�� Sass ���� `margin: 10px 15px 0 0 or font-face: Helvetica, Arial, sans-serif`�� ���� CSS�� ���� ���� ��Ÿ���� ����Դϴ�.     
List�� �� ��ü�δ� ������ ���� ������ [SassScript list functions](http://sass-lang.com/documentation/Sass/Script/Functions.html#list-functions) ������ �����ϰ� ���˴ϴ�. `nth function` ������ list ���� item�� �׼��� �Ҽ��ְ�, join function������ �������� list�� ������ �� �ְ�,  append function������ list�� item�� �߰��� �� �ֽ��ϴ�. ����  @each directive ������ ��Ÿ�� �ȿ� list�� ������ ������ �߰��� �� �ֽ��ϴ�.

������ ������ �����ϴ°� �ܿ��� �ٸ� ����Ʈ ��ϵ� ���� �� �� �ֽ��ϴ�. ���� ���, 1px 2px, 5px 6px �� 1px 2px�� �̷���� ����Ʈ, 5px 6px �� �̷���� ����Ʈ �ΰ��� �����ϴ� ū ����Ʈ �Դϴ�. ���� ������ list ���� ���۰� ���� ��Ȯ�� �ϰ� �ʹٸ� ��ȣ ()�� ����ϸ� �˴ϴ�. 
���� ���, (1px 2px) (5px 6px)�� ���� (1px 2px)�� �̷���� ����Ʈ, (5px 6px) �� �̷���� ����Ʈ �ΰ��� �����ϴ� ū ����Ʈ �Դϴ�. �ΰ��� ���̴� ���� ����Ʈ�� ������ `����`���� �����ϴ°� `,`�� �����ϴ°� �� ���Դϴ�.

list�� �Ϲ� Css�� ������ �� ��� Css�� list�� �������� �ʱ� ������ Sass�� `()`�� �߰����� �ʽ��ϴ�. ��,(1px 2px) (5px 6px) ��  1px 2px 5px 6px �� �����ϰ� ������ �˴ϴ�. �׷��� ��Sass���� �ΰ����� �������� �ʽ��ϴ�. : ù��°�� �ΰ��� list�� ������ �ϳ��� ����Ʈ�̰� �ι�° �װ��� ���ڸ� �����ϴ� list �Դϴ�. 

��, list�� �� �׸��� ���� �� �ֽ��ϴ�. �̶��� �� ���� ()�� ǥ���մϴ�.    
�׷��� �� ���� Css������ ������ �� �� ���� ������ ���� `font-family: ()`���� ���� ����Ѵٸ� Sass�� ������ ������ �߻��մϴ�. 
���� list ���� `1px 2px () 3px or 1px 2px null 3px` �� ���� �� list �� null ���� �����Ѵٸ� Css�� ������ �ϱ� ���� �����ؾ��մϴ�. 

��ǥ�� ���� �� ��� �ڿ� ��ǥ������ �� �ֽ��ϴ�. 
#### Maps

���� Ű�� ���� ã�� ������ Ű�� �� ������ ���踦 ��Ÿ���ϴ�.   
�������� �̸������� �׷��� values�� ���� ������ �����մϴ�. (key���� �׷����� ���� ������ �� �ֵ��� �ش� �׷쿡 ������ ����)    
���� �׻� ��ȣ�� ����� �ϸ� ��ǥ�� �����ؾ� �մϴ�.    
Map�� ��κ� SassScript ����� ����Ͽ� ������ �� �ֽ��ϴ�.    
@each ���þ ����Ͽ� �� ������ ������ Ű/�� �ֿ� ��Ÿ���� �����ϴµ� ���˴ϴ�.   

```SCSS

$map: (key1: value1, key2: value2, key3: value3);
```

<br>
### Operators (����) 

#### Number Operations(���ڿ���)

Sass������ `+, -, *, /, %`���� ������ ��Ģ����� (>, <, ==, >-, <=, !=)���� �񱳿���,  �������� ���� �����մϴ�.


##### ������ and / 
```SCSS

// _style.scss
p {
    font: 10px/8px;             // �Ϲ�����  css �δ� ������ ������ �� �� ����
    $width: 1000px;
    width: $width/2;            // ������ ����Ͽ� ������ ������ ����
    width: round(1.5)/2;        // �罺�Լ��� ����Ͽ� ������ ������ ����
    height: (500px/2);          // ��ȣ�� ����Ͽ� ������ ������ ����
    margin-left: 5px + 8px/2px; // �÷��� �����ڿ� �Բ� ������ ������ ����
    font: (italic bold 10px/8px); // ����Ʈ�� ��ȣ���� ������ �� ����. 
}

```
```css

/*style.css*/
p {
  font: 10px/8px;
  width: 500px;
  height: 250px;
  margin-left: 9px; }

```
\#{}�� ������� ���� ���� :

```SCSS

// _style.scss
p {
  $font-size: 12px;
  $line-height: 30px;
  font: #{$font-size}/#{$line-height};
}

```
```css

/*style.css*/
p {
  font: 12px/30px; }

```
#####  Color Operations

sass������ ���򿬻굵 �����մϴ�.


\#112233 + #332211 �̷������� ��밡���ϸ� 
\# 11 22 33 ���� 11�� Red, 22�� Green 33�� Blue ���� ��Ÿ���� RGB���ڷ� ������ �Ǿ��ֽ��ϴ�.
���� ���ڴ� 16������ ǥ�õǰ� ���� ����� red�� red���� green�� green���� blue�� blue���� ������ �ǰ� �˴ϴ�.

```SCSS
ex) #128012 + #212223  = #33a235

}


\#552230 - #225010 = #330020
- green���� 22-50�� �Ǿ� ���̳ʽ��� ���ԵǸ� �׳� 00���� ǥ�õ˴ϴ�.

\#224400 * #aa02ff = #ff8800
- red���� 22*ff�� ff�� �ʰ��Ͽ����� �׳� ff�� ǥ�õ˴ϴ�. ���� 00*ff�� 0�� ������ �ϸ� ������ 0�� �����⶧���� 00�� �����Ե˴ϴ�.

\#101010 / #102021 = #010100
- ���⼭ Ȯ���Ҽ� �ִ°� 10/20 = 0.5 ������ 01�� ��ȯ�ϳ� ���̻󰡸� 00�� ��ȯ�ϴ°ŷ� ���� �Ҽ����� �ݿø� �Ѵٴ� ���� Ȯ���� �� �ֽ��ϴ�.


#####  String Operations

sass�� ���ڿ������� ���굵 �����մϴ�.

���ڿ������� ������ `'+'`���길�� �����̵Ǹ� -,*,/ �� �����մϴ�.

```SCSS
ex) 'ab'+'cd' = 'abcd' 

}

#####  Boolean Operations

��/���� �����ڴ� ���� ���� �����ϴ°Ͱ� �����մϴ�

```SCSS
ex) true and true = true

}

true and false = false

true or true = true

true or false = false

#####  List Operations
sass������ list������ �Ұ����մϴ�

(a,b) + (c,d) �� �Ͽ��� (a,b,c,d) �� ������ �ʽ��ϴ�.

list������ ����Ϸ��� �罺�� �����Լ��� ����Ͻñ� �ٶ��ϴ�.

[SassScript list functions](http://sass-lang.com/documentation/Sass/Script/Functions.html#list-functions)

<br><br>
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
���ù������� `container`Ŭ������ `width`���� �����Ѵٸ� `article,aside`�� ���� �ڵ����� �ݿ��Ǿ� ����˴ϴ�.
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


### Parentheses

```css
p {
  width: 1em + (2em * 3);
}
```
sass������ ���� ���п����� ���� ���������� ��ȣ������ �켱������ �̷�����ϴ�.

```css
p { width: 7em; }
```

### Functions

sass��ü���� �����ϴ� �����Լ����Դϴ�. 

[sass Functions](http://sass-lang.com/documentation/Sass/Script/Functions.html)
��ũ�� ���� ���ż� api�� Ȯ���Ͻ� �� �ֽ��ϴ�.


### Interpolation : #{} ������
SASS �� ������ "" ���ο��� ó���� �� �ִ� �������� �����ϰ� �ֽ��ϴ�.
�ٽ� ���ؼ�, #{} ������ ����Ͽ� ������ �� �Ӽ� �̸��� ������ ����� ���� �ֽ��ϴ�.


```SCSS

//style.scss
$name: foo;
$attr: border;
p.#{$name} {
  #{$attr}-color: blue;
}

```

```css

/* style.css */
 
p.foo {
  border-color: blue; }

```
\#{} �� SassScript�� �Ӽ������� ����ϴ� �͵� �����մϴ�. <�ؼ��Ұ�>

```SCSS

//style.scss
p {
  $font-size: 12px;
  $line-height: 30px;
  font: #{$font-size}/#{$line-height};
}

```
```css

/* style.css */
 
p {
  font: 12px/30px; }

```
### & in SassScript


### Variable Defaults�� global : !default, !global

!default �÷��״� value���� ���� ���� ������ �̹� �Ҵ�� ���� ���Ҵ����� ������ ���� ���� ���� �ʴ� null�� ��쿡�� !defalut �÷����� value������ �Ҵ�˴ϴ�. 

```SCSS

// _style.scss
$content: "First content";
$content: "Second content?" !default;
$new_content: "First time reference" !default;

#main {
  content: $content;
  new-content: $new_content;
}

$content: null;
$content: "Non-null content" !default;

#main {
  content: $content;
}

#demo {
  $width : 5em !global; // ��������ó�� ����մϴ�.
  width: $width;
}
#sidebar {
  width: $width;
}

```
```css

/*style.css*/
#main {
  content: "First content";
  new-content: "First time reference";
}

#main {
  content: "Non-null content";
}

#demo {
  width: 5em;
}

#sidebar {
  width: 5em;
}

```

`!global` flag �� ����ϸ� �߰�ȣ �ȿ� ������ ���������� ���������� ������ �� �ֽ��ϴ�. 

```SCSS

// _style.scss
#main {
  $width: 5em !global;
  width: $width;
}

#sidebar {
  width: $width;
}

```
```css

/*style.css*/
#main {
  width: 5em;
}

#sidebar {
  width: 5em;
}

```

* [global flag ���̵���� ����](http://sass-guidelin.es/ko/#global-)]

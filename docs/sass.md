# Sass


### Comments
Sass �ּ��� �ΰ�����.

```sass
// �ؼ������ʴ� �ּ�
/* �ؼ��Ǵ� �ּ� */
```

���ּ��ϰ��� �����ؾ��Ѵ�.

```sass
/* 
������
�ּ�����
�̰��� �ȵ˴ϴ�.
*/


/*
 * ������
 * �ּ�����
 * �տ� *�� �ٿ��� �մϴ�.
 */
```

������ �ּ����� ����� �� �ִ�.

```sass
// before
$version: '1.2.3'
/* #{$version} */

// after
/* 1.2.3 */
```




<br>

### Nested Rules
Sass ��ø��Ģ�� �θ����� ���ο� �ڽļ����ڸ� �鿩���⸸�ϸ� �ȴ�.

```sass
.parent
	.child
		color: blue
```





<br>

#### Referencing Parent Selectors
Sass �θ� ���� ������(&) : �θ����ڿ� ��ø ���·� �ڽ� �����ڸ� ����� �� ���ۼ���(&) ��ȣ�� �տ� ���̸� �θ� �����ڸ� �����Ѵ�.

```sass
a
	&:hover
		color: blue
```





<br>

#### Nested Properties
Sass ��ø �Ӽ�: ��ø��Ģ�� ���� �Ӽ��� �����ϰ� ��ø�Ͽ� ����Ҽ� �ִ�.

```sass
.parent
	margin:
		left: auto
		right: auto
```






<br>

#### Selector Inheritance
Sass ������ ���(@extend) : �����ڿ� ������ �Ӽ��� �״�� �����޴´�.

```sass
.button
	font-weight: bold
	color: blue

.button-1
	@extend .button
	background-color: #fff

.button-2
	@extend .button
	background-color: #ddd
```




<br>

#### Placeholder Selector
Sass ��ü ������(%): `%` ��ȣ�� ������ css �� �ؼ����� �ʴ´�. ��ü�����ڸ� �����ڸ� ����ϸ� ��ü�������� �Ӽ��� �״�� �����޴´�.

```sass
%button
	font-weight: bold
	color: blue

.button-1
	@extend %button
	background-color: #fff

.button-2
	@extend %button
	background-color: #ddd
```

- ���

```css
.button-1, .button-2 {
    font-weight: bold;
    color: blue;
}

.button-1 {
    background-color: #fff;
}

.button-2 {
    background-color: #ddd;
}
```



<br><br>

### Import
Sass ȣ���ϱ� : `.sass` , `.scss` ��� Ȯ���� ������ ������ä�� ȣ�Ⱑ���ϴ�. 
css �� ��ȯ���� �������� ���ϸ� �տ� `_`�� ���δ�

```sass
// base �� _base.scss �̴�.
@import "base";
```


Ruby ȯ���� Sass ������ Output ��Ÿ���� ������ �� �ִ�.

Sass ��½�Ÿ�� | CSS ��°��
----------------|---------------
compact			| �ڵ带 �����ڸ��� �� �ٷ� ���
nested 			| �ڵ带 �����ڸ��� �����ٷ� ����ϵ�, ���𱸹��� ���� ������ �Ӽ��ڿ� ��ġ�Ѵ�.
expanded 		| �ڵ带 �����ڸ��� �����ٷ� ���
compressed 		| �ڵ带 ��� �����Ͽ� ���






<br><br>

### Sass Script


#### Variables
Sass���� ������ �̸��տ� `$` �� ����Ѵ�.

```sass
$blue: blue
```




<br>

#### Operation
Sass���� ����ó���� ��Ģ����(+, -, *, /), �񱳿���(>, <, ==, >-, <=, !=), �������� ���� �����Ѵ�.

������(/)�� �Ҷ� ������ ���� ���� ��ȣ�� ����� �ȴ�.

```sass
(100% / 4)
// ��� 25%
```




<br>

#### Mixin
�ͽ����� `sass`, `scss` ���� ������ �ణ �ٸ����� ���� ȣȯ�� �Ǽ� ȣ���ؼ� ����Ҽ� �ִ�.

`sass`���� �ͽ��� ����Ҷ� �̸��տ� `=` �� ���δ�. ȣ���Ҷ� `+`�� ���δ�.
`scss`���� �ͽ��� ����Ҷ� �̸��տ� `@mixin` Ű���带 ����Ѵ�. ȣ���Ҷ� `@include` Ű���带 ����Ѵ�.

- sass ����

```sass
=reset-box
	margin: 0
	padding: 0

.box
	+reset-box
```

- scss ����

```scss
@mixin reset-box {
	margin: 0;
	padding: 0;
}

.box {
	@include reset-box;
}
```


- Arguments
�������ڸ� ����Ͽ� �ͽ����� Ȯ���Ҽ� �ִ�. ������ �����ϰų� �Ҷ� ������ ������ ������ ��Ȯ�ϰ� ����ؾ� �Ѵ�.

�⺻���� �̸� �����س����� ���� �������� �������� �⺻���� ����ϰ�, �����ϸ� �װ��� ����Ѵ�. 
������� �ʴ� �Ӽ������� `null` �� �Է��س����� ���� �������� ������ ���������ϴ�.

```sass
=position($type: relative, $t: null, $r: null)
	position: $type
	top: $t
	right: $r

// ȣ��
.box
	+position(absolute)

// ���ϴ� �Ӽ����� �����Ҽ��� �ִ�.
.box-2
	+position($t: 3px)
```

- ���

```css
.box {
	position: absolute;
}

.box-2 {
	position: relative;
	top: 3px;
}
```





- ������ ��������

```sass
=transition($args...)
	-webkit-transition: $args
	transition: $args

// ȣ��
.box
	+transition(width 0.2s, height 0.4s, ease-aut)
```


- ���

```css
.box {
	-webkit-transition: width 0.2s, height 0.4s ease-aut;
	transition: width 0.2s, height 0.4s ease-aut;
}
```


<br><br>




### Conditions




#### @if...@else

�ڹٽ�ũ��Ʈ�� `if` ���� ����ϸ� `@if...@else if...@else` �� �����ϴ�.

������ : ������ ���ڿ��� �����Ҷ� `#{}` �� ����Ѵ�.


```sass
$theme: dark

@if $theme == light
	$bg-color: #f34e7b
@else
	$bg-color: #61051f

// ���
body.#{$theme}-theme
	background: $bg-color
```

- ���

```css
body.dark-theme {
	background: #61051f;
}
```





<br>



#### if()
if()�Լ��� �ڹٽ�ũ��Ʈ�� 3�� �����ڿ� ����ϴ�.

```sass
if(����, ���϶�, �����϶�)
```


```sass
.foo 
	padding: if(true, 10px, 20px)
```

- ���

```css
.foo {
    padding: 10px;
}
```





<br>


### Loops
Sass �ݺ����� �ڹٽ�ũ��Ʈ�� �ݺ����� �����ϴ�

- @while

```sass
%col
	float: left
	margin-left: 20px;

$i: 1 // �ݺ���

@while $i <= 3
	.col-#{$i}
		@extend %col
		width: (60px * $i) + (20 * ($i - 1))
	// $i �ݺ��� �� 1 ����
	$i: $i + 1
```

���

```css
.col-1, .col-2, .col-3 {
    float: left;
    margin-left: 20px;
}

.col-1 {
    width: 60px;
}

.col-2 {
    width: 140px;
}

.col-3 {
    width: 220px;
}
```



- @for

@for ���� $i ���� 1���� (from) 3 ������ (through) 1�� �����ϸ鼭 �ݺ��մϴ�.
`through` ��� `to` Ű���带 ����ϸ� 3������ �� 2���� �ݺ��մϴ�.

```sass
%col
	float: left
	margin-left: 20px

@for $i from 1 through 3
	.col-#{$i}
		@extend %col
		width: (60 * $i) + (20 * ($i - 1))
```

- ���

```css
.col-1, .col-2, .col-3 {
    float: left;
    margin-left: 20px;
}

.col-1 {
    width: 60;
}

.col-2 {
    width: 140;
}

.col-3 {
    width: 220;
}
```








- @each

`@each...in` ���� ����Ʈ�� �ʿ� �����ϴ�.
`in` �տ��� ����Ʈ�� �� ���θ� ��ȯ, Ž���ϴ� ���� ������(item) �� ����, �ڿ��� ����Ʈ�� ���� �ü� �ֽ��ϴ�.

�� ������(item) ������ŭ �ݺ��մϴ�.

```sass
@each $item in icon1, icon2, icon3, icon4
	.icon-#{$item}
		background-image: url("images/#{$item}.png")
```

- ���

```css
.icon-icon1 {
	background-image: url("images/icon1.png");
}
.icon-icon2 {
	background-image: url("images/icon2.png");
}
.icon-icon3 {
	background-image: url("images/icon3.png");
}
.icon-icon4 {
	background-image: url("images/icon4.png");
}
```



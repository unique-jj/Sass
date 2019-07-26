# Sass Reference

## CSS Ȯ��

* Nested Rules
* Referencing Parent Selectors: &
* Nested Properties
* Placeholder Selectors: %foo 


### Nested Rules (��ø)
```css
/*styel.css*/
#main {
  width: 97%; }

#main p{
    font-size: 2em; }
```
���� CSS�� �ɽ����̵������� ���� ����ó�� �θ� Ŭ������ �����ϴ� ������ ����� �����ϰ� �ֽ��ϴ�. 
�׷��� Sass�� �̿��ϸ� HTML�� div �ȿ� div�� �ִ´ٴ��� �ϴ� ��ø �� ��������ó�� CSS�����ڸ� ��ø�� �� �ֽ��ϴ�.   
�̰��� �θ� �����ڸ� �ߺ� �ۼ��ϴ� ���� �����մϴ�. 

```SCSS
/*styel.scss*/
#main {
  width: 97%;

  p, div {
      font-size: 2em;
      
      a { font-weight: bold; 
      }
  }

  pre { font-size: 3em; }
}

```

```css
/*styel.css*/
#main {
  width: 97%; }
  #main p, #main div {
    font-size: 2em; }
    #main p a, #main div a {
      font-weight: bold; }
  #main pre {
    font-size: 3em; }

```

��, ����ģ ��ø�� CSS�� �����Ͻ� ������ �߻��� �� ������, ������ �������� ����߸� �� �����Ƿ� �������� �ʽ��ϴ�.    
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
### Referencing Parent Selectors: & (�θ�����:&)

��ø��Ģ���� �θ����ڸ� ��ø�ؼ� ����ϴ� ����� ����������, ��ø��Ģ�� �θ� Ŭ���� �ȿ� ���� �ڽ� Ŭ�������� ����� �� �ִ� ��Ģ�Դϴ�. 
�������� ���� ��쿡�� �θ� �����ڸ� �����ؾ� �մϴ�. `�θ�����:hover` , `�θ�����.�߰�������` ó�� �θ� Ŭ���� ���ο��� �����ϰ� �ݺ��� ��쿡�� ��ø��Ģ���� ��ü�� �� �� �����ϴ�.
�̷���� ��ø�ؼ� �θ����ڸ� �ۼ��ϴ� ��� `&`�� �θ����ڸ� ȣ���� �� �ֽ��ϴ�. 

```SCSS

// _style.scss
a {
  font-weight: bold;
  text-decoration: none; 
  &:hover {
    text-decoration: underline; 
  }
}
body{
  &.firefox a {
      font-weight: normal; 
  }
}
```
```css

// _style.css
a {
  font-weight: bold;
  text-decoration: none; }
  a:hover {
    text-decoration: underline; }
  body.firefox a {
    font-weight: normal; }
```
��ó�� ������ ��Ÿ���� ���� ���� ����� ���� �ƴ�, �ϳ��� �׷��� �� �� �ִٴ� ������ ������ �ֽ��ϴ�. 
�׷���, ���̻�ε� ���� ��� �������� ��ü �̸��� ��Ȯ�� �������� �ʱ� ������ �������� �ʽ��ϴ�.

```SCSS
// _style.scss
#main {
  color: black;

  &-sidebar { border: 1px solid; }
}

```
```css

// _style.css
#main {
  color: black; }
  #main-sidebar {
    border: 1px solid; }
```

�߰��� [�ͽ���]()�� [���ǹ�]()�� �̿��Ͽ� �θ� �����ڰ� �����ϴ����� ���θ� ������ ���� �ֽ��ϴ�.

```SCSS
// _style.scss
@mixin does-parent-exist {
    @if & {
      &:hover {
        color: red;
      }
    }
    @else {
      a {
        color: red;
      }
    }
}

// �θ����ڰ� �ִٸ�...
.demo {
  @include does-parent-exist;
}

// �θ����ڰ� ���ٸ�...
@include does-parent-exist;

```


<br>
### Nested Properties (��ø �Ӽ�)
Css�� �Ӽ��� font-family, font-size, font-weight ��� ���� `font`�� ���۵Ǵ� �Ӽ��� ��ø�Ͽ� ����� �� �ֽ��ϴ�.

```SCSS
// _style.scss
.funky {
  font: {
    family: fantasy;
    size: 30em;
    weight: bold;
  }
}

```
```css

// _style.css
.funky {
  font-family: fantasy;
  font-size: 30em;
  font-weight: bold; }
```
���ٷ� ����Ǵ� �Ӽ����� ���������� ��ø�Ӽ��� ������ �� �ֽ��ϴ�.

```SCSS
// _style.scss
.funky {
  font: 20px/24px fantasy {
    weight: bold;
  }
}

```
```css

// _style.css
.funky {
  font: 20px/24px fantasy;
    font-weight: bold;
}
```
* [��ø���� ���̵���� ����](http://sass-guidelin.es/ko/#nesting)

###Placeholder Selectors: %foo (��ü ������)

Sass������ Ư���� �����ڷ� `placeholder selector`�� �����մϴ�. 
�� �����ڴ� Ŭ����(.)�� ���̵�(#)�� ��ü�Ͽ� `%`�� ����ؼ� ������ �� ������, 
Css�� �����Ͻÿ� ��ü�����ڸ��� ����� �ڵ��  ������ ���� �ʽ��ϴ�.

```SCSS
// _style.scss

// �� ��ü�����δ� Css�� ������ ���� �ʽ��ϴ�.
#context a%extreme {
  color: blue;
  font-weight: bold;
  font-size: 2em;
}

```
�� �ڵ�δ� %extreme�� ������ Ŭ������ ���̵� ��ü�� ���Դϴ�.
���� ���Ǳ� ���ؼ� `@extend %�̸�`�� ����� ȣ�����־���մϴ�.

```SCSS
// _style.scss

.notice {
  @extend %extreme;
}

```
```css

// _style.css
#context a.notice {
  color: blue;
  font-weight: bold;
  font-size: 2em; }

```

mixin������ ������ ����Ͽ� �Ʒ��� ���� ������ε� ǥ���� �� �ֽ��ϴ�.

```SCSS
// _style.scss
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
```css

// _style.css
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

####CSS ������ ���� ���� ������ ����ϱ�
```SCSS
// _style.scss
div {
  color:black;

  // ���� ������
  .foo {
    color: black; // �ڼ�(descendant) ������
  }
  > .foo {
    color: black; // �ڽ�(child) combinator
  }
  + .foo {
    color: #000; // ��������(adjacent sibling) ������
  }
  ~ .foo {
    color: yellow; // �Ϲ�����(general sibling) ������
  }
  & .foo {
    color: #fff; // Sass �θ�(Parent) ���� ������
  }
  .foo & {
    color: red; // Sass �θ�(Parent) ���� ������
  }
  &.bar {
    color: green;
  }
}

```
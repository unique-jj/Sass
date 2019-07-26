# Sass Reference
* Control Directives & Expressions
	
	
##8. Control Directives & Expressions

- @if
- @while
- @for
- @each
	- Multiple Assignment




### if
sass���� if��(���ǹ�)�� ����� �� �ֽ��ϴ�.

������ ������ �����ϴ�.

```css
@if true/false {
  ...
} @else if true/false {
  ...
} @else {
  ...
?}
```

true/false�� ��ȣ�� �ѷ����� �ʰ�, else�� if�� ���ٴ� ���� �����մϴ�.


���� jb-type�� ���� ���� ������ ���� �ٸ��� ����� �����Դϴ�.

jb-type�� ���� jb-red�̸� ����������, jb-blue�̸� �Ķ�������, jb-red�� jb-blue�� �ƴϸ� ���������� ����ϴ�.

```css
//sass

$jb-type: jb-blue;
p {
  @if $jb-type == jb-red {
    color: red;
  } @else if $jb-type == jb-blue {
    color: blue;
  } @else {
    color: black;
  }
}
```
������ ���� jb-blue, jb-red, Ȥ�� �׿ܾƹ��ų� ���� �ٲ㰡�鼭 �׽�Ʈ�غ��ø� ����� ��� �������� �����Ͻ� �� �ֽ��ϴ�.



```css
//css

p { color: blue; }

```


sass������ �ݺ����� 3������ �ֽ��ϴ�. ù������ wile���� �ٷ絵�� �ϰڽ��ϴ�.
### while
```css
$i: 1;
$gutter: 20px;

@while $i <= 12 {
  .grid-#{$i} {
    width: (60px * $i) + $gutter * ($i - 1);
  }
  $i: $i + 1;
}
```

@while ���� ������ true �϶����� ��ȣ���� ����� ��� �ݺ��ϴ� ��ɾ� �Դϴ�.

$i: $i + 1;
�ѹ� �ݺ��� �� ���� $i ������ ���� 1�� ������Ű�� �ᱹ���� ó������ 1�̾��� ���� 12�� �����ϸ� @while���� �ߴܵ˴ϴ�.

.grid-#{����}�� �ش� Ŭ������ ���������� ������

(60px * $i) + $gutter * ($i - 1); �������� �����������ݴϴ�.


```css
//��� 
.grid-1 { width: 60px; }

.grid-2 { width: 140px; }

.grid-3 { width: 220px; }

.grid-4 { width: 300px; }

.grid-5 { width: 380px; }

.grid-6 { width: 460px; }

.grid-7 { width: 540px; }

.grid-8 { width: 620px; }

.grid-9 { width: 700px; }

.grid-10 { width: 780px; }

.grid-11 { width: 860px; }

.grid-12 { width: 940px; }


```

### for 

while���� ������ �ణ �ٸ��� ����� �ݺ����Դϴ�.

from �� to,through �� �̿��� �ڹٽ�ũ��Ʈ�� for���� ����� ȿ���� �� �� �ֽ��ϴ�.
```css
$total: 12;

@for $i from 1 to $total {
  .grid-#{$i} {
    width: 70px * $i;
  }
}
```
$for �ڿ� {}�ȿ��� ���� ������ ������ from ���� to, through ���� ���ϴµ��� �ݺ��˴ϴ�.

�� �� to�� <(�̸�)�� ���� through �� <=(����)�� �����ϴ�.

```css
.grid-1 { width: 70px; }

.grid-2 { width: 140px; }

.grid-3 { width: 210px; }

.grid-4 { width: 280px; }

.grid-5 { width: 350px; }

.grid-6 { width: 420px; }

.grid-7 { width: 490px; }

.grid-8 { width: 560px; }

.grid-9 { width: 630px; }

.grid-10 { width: 700px; }

.grid-11 { width: 770px; }
```

```css

$total: 12;

@for $i from 1 through $total {
  .grid-#{$i} {
    width: 70px * $i;
  }
}
```

```css
.grid-1 { width: 70px; }

.grid-2 { width: 140px; }

.grid-3 { width: 210px; }

.grid-4 { width: 280px; }

.grid-5 { width: 350px; }

.grid-6 { width: 420px; }

.grid-7 { width: 490px; }

.grid-8 { width: 560px; }

.grid-9 { width: 630px; }

.grid-10 { width: 700px; }

.grid-11 { width: 770px; }

.grid-12 { width: 840px; }
```


### each

each���� �迭�̳� ��Ÿ���� �������� ������ �ϳ��� ������ ������ ��ɾ��̸� �ڹٽ�ũ��Ʈ�� for in���� ����ϰ� �����մϴ�.

```css
@each $obj in phone, tablet, cup, mouse {

  .item-#{$obj} {
    background-image: url("img/#{$obj}.jpg");
  }
}
```
@each �ڿ� $obj ������ �����ϰ� in �ڿ� �迭 phone, tablet, cup, mouse �� �����ϰ� �Ǹ� 

���������� ������ ���Ե˴ϴ�.

```css
.item-phone { background-image: url("img/phone.jpg"); }

.item-tablet { background-image: url("img/tablet.jpg"); }

.item-cup { background-image: url("img/cup.jpg"); }

.item-mouse { background-image: url("img/mouse.jpg"); }
```

�̹����� �迭�̾ƴ� �����¸� �ٷﺸ���� �ϰڽ��ϴ�.

```css
@each $item in (h1: 2em, h2: 1.5em, h3: 1.2em) {

  #{nth($item, 1)} {
    font-size: nth($item, 2);
  }
}
```

�Ʊ�� �ٸ��� (h1: 2em, h2: 1.5em, h3: 1.2em) �����°� �ڿ� ��ġ�ϰ� �ֽ��ϴ�.

nth�����Լ��� �̿��� #{nth($item, 1)}���⼭�� ù��°�� ��, h1,h2,h3 �� ����
nth($item, 2) ���⼭�� 2��°�� 2em, 1.5em, 1.2em ���� ���°� Ȯ���� �� �ֽ��ϴ�.

nth�Լ��� (�迭or��,index��) �������� ���� �迭�̳� ���� Ư���ε��� ���� ������ �� �ִ� �����Լ��Դϴ�.
#�������̳ʸ� ���� Sass 
- ����. �� �ô�Ȩ.  2014�� 7�� ����.

###������� ���ø����̼� ����ϱ�

* [��ī��Ʈ(Scout)](http://bkaprt.com/sass/6/) - Mac / Window ���� ����ũž ���ø����̼�.    
  ������ ���ȯ���� �����ϰ�, ����� Ŭ������ Sass ������Ʈ�� �����մϴ�.

* [�ڵ�Ŷ(CodeKit)](http://bkaprt.com/sass/7/)- Mac ����    
  �ܼ��� GUI���� Sass, LESS, Stylus, Haml, Ŀ�ǽ�ũ��Ʈ, �ڹٽ�ũ��Ʈ�� �׹��� ������ ���������ݴϴ�.   
  �ڵ�Ŷ�� ���ϰ� �̹����� �����ϰ� �����Ҷ� �ڵ����� ������ ���ΰ�ħ ���ִ� �ΰ���ɵ� �ֽ��ϴ�.     
* [���̺긮�ε�(LiveReload)](http://bkaprt.com/sass/8/)- Mac / Window   
  Sass ������ �� ��� ������ ��������� ����͸�, �������� ���ΰ�ħ���ݴϴ�.

* [���Ľ�.��(Compass.app)](http://bkaprt.com/sass/9/)- Mac / Window / Linux
  ���� �޴��� ���ø����̼����� Sass������ �����ϰ� ���������ݴϴ�.


### CSS ������ �����ΰ���?
Sass�� �� �� CSS ��ó������� ǥ������ ������ ���� ��ɵ��� �׽�Ʈ �� �� �ֽ��ϴ�. ��, Sass�� ���� ������ �������� �ʴ� ��ɵ��� �����ϸ鼭 �۾��� ������ �� �ֽ��ϴ�. 

Sass�� LESS���� ������ �� Ȱ��ǰ� �ֱ� ������ �������� CSS������� ������ �������ڴ� ������ �������� �ְ�, ���� W3C�۾� �ʾ����� 'CSS ������ⷹ��1'�� �����������̸� (http://bkaprt.com/sass/11/) �ֽ� ��Ŷ ��������� ����Ʋ�� ����(Nightly Builds)���� ������ ���� ������ ����Ǳ� �����߽��ϴ�. 

### �̵������

#### �ػ� �б����� ������ �����ϱ� 

```SCSS

// �ػ� �б����� ������ ����. 
$width-small : 500px;
$width-medium: 800px;
$width-large: 1200px;

```
��� ���� :

```SCSS

// _style.scss

section.main {
	font-size:16px;
	line-height: 1.4;

	@media screen and(max-width: $width-large){
		float: left;
		width: 65% 
	}
	@media screen and(max-width: $width-medium{
		float: none;
		width: auot;
	}
	@media screen and(max-width: $width-small){
		font-size: 12px;
		width: 1.4; 
	}
}

```
������

```CSS

// _style.css

section.main {
	font-size:16px;
	line-height: 1.4;
}
@media screen and(max-width:1200px){
	float: left;
	width: 65% 
}
@media screen and(max-width: 800px){
	float: none;
	width: auot;
}
@media screen and(max-width: 500px){
	font-size: 12px;
	width: 1.4; 
}

```

���߿� �ػ� �б����� ������ ��� �������� �� �ѹ��� ��ġ�� Sass�� �˾Ƽ� �� ���� ���� ������ ������Ʈ ���� ���Դϴ�.    
���굵 �����ؼ� �ػ� �б����� ���� ���ϰų� �E �� �ֽ��ϴ�. 

```SCSS

// _style.scss


@media screen and(max-width: $width-small + 1){
	font-size: 12px;
	width: 1.4; 
}
@media screen and(max-width: $width-small - 1){
	font-size: 12px;
	width: 1.4; 
}
```
������

```CSS

// _style.css

@media screen and(max-width: 501px){
	font-size: 12px;
	width: 1.4; 
}
@media screen and(max-width: 499px){
	font-size: 12px;
	width: 1.4; 
}
```
�� �� �����ؼ� �̵������ ��ü�� ������ ������ ���� �ֽ��ϴ�. 

```SCSS

// _style.scss

$mobile-first: "screen and (min-widht: 300px)";

@media #{$movile-first}{
	#content {
		font-size:14px;
		line-height:1.5;
	}
}
```
```CSS

// _style.css

@media screen and (min-widht: 300px){
	#content {
		font-size:14px;
		line-height:1.5;
	}
}
```

#### @content��ϰ� �ͽ��� ���ս�Ű��. 

`@content` �����ڸ� ����ؼ� ��Ÿ�� ��� ��ü�� �ͽ������� �ѱ� �� �ֽ��ϴ�.   
Sass�� ������ �ϸ鼭 �� ����� �ͽ����� ȣ���ϴ� ���� �ȿ� �ٽ� ���� �� �Դϴ�.   

�Ʒ��� �����Դϴ�. ���δٸ� 3���� �ػ� �б����� ���� ������ �ͽ����� ����� �� �ػ� �б����� ���Խ�ų ��Ÿ���� `@content`�� ��� �����մϴ�. 

```SCSS

$width-small : 400px;
$width-medium: 760px;
$width-large: 1200px;

@mixin responsive($width){
	@if $width == wide-screens{
		@media only screen and ( max-width: $width-large){
			@content;
		}
	}
	@else if $width == medium-screens{
		@media only screen and ( max-width: $width-medium){
			@content;
		}
	}
	@else if $width == small-screens{
		@media only screen and ( max-width: $width-small){
			@content;
		}
	}

}

```

�ͽ����� ������ �� �Ѱ��� $width ������ ���� Ȯ���ϱ� ���� @if�� @else ���� ����մϴ�. 
���� ��� �츮�� �ͽ��ο� medium-screen ������ �Ѱ��ָ� Sass�� $width-medium ������ ������ ���� `760px`�� `max-width`�� �־� �̵�������� �������� ���Դϴ�. `@content`�� �� ���ư� �̵�������� ������ �ͽ��ο� ��Ÿ�� ����� �Ѱ��� �� �ֽ��ϴ�. 

```SCSS

#content{
	float:left;
	width: 70%;
}
@media only screen and ( max-width: 1200px){
	#content{
		width:80%;
	}
}
@include responsive(wide-screens){
	#content{
		width:50%;
		font-size:14px;
	}
}
@include responsive(wide-screens){
	#content{
		float:none;
		width:100%;
        font-size:12px;
    }
}
```
������ 

```Css

#content{
	float:left;
	width: 70%;
}
	@include responsive(wide-screens){
		width:80%;
	}
	@include responsive(wide-screens){
		width:50%;
		font-size:14px;
	}
	@include responsive(wide-screens){
		float:none;
		width:100%;
        font-size:12px;
	}
}
```



###retinize �ͽ��� 

```SCSS
	
@mixin retinize($file, $type, $width, $height){ //4���� ���ڼ��� 
	background-image:url('../img/' + $file + '.' +$type);
    //������ ���ξ� �Ӽ�
	@media (-webkit-min-device-pixel-ratio: 1.5),
	       (min--moz-device-pixel-ratio: 1.5),
	       (-o-min-device-pixel-ratio: 3/2),
	       (min-device-pixel-ratio: 1.5),
	       (min-resolution: 1.5dppx){

		&{
			background-image: url('../img/' + $file + '-2x.' +$type);
			-webkit-background-size: $width $height;
			   -moz-background-size: $width $height;
			        background-size: $width $height;
		}
	}
}

```

```SCSS
	
// retinize �ͽ��� ��뿹�� 

	li.dribbble a{
		@include retinize('icon-dribbble', 'png', 24px, 24px);
	}

```

���� retinize �ͽ��ξȿ� �ͽ����� �־� �ڵ带 �Ѵܰ� �� �ٿ����ô�. 

```SCSS
	
@mixin retinize($file, $type, $width, $height){ 
	background-image:url('../img/' + $file + '.' +$type);
    
    //�ȼ��� �е��κ��� ���� ������ ������ ���� 
	@media  #{$is-hidpi} { 

		&{
			background-image: url('../img/' + $file + '-2x.' +$type);
			//background-size�� �ͽ������� ����
			@include background-size($width,$height)
		}
	}
}

```
```SCSS
$hidpi: "(-webkit-min-device-pixel-ratio: 1.5),
         (min--moz-device-pixel-ratio: 1.5),
         (-o-min-device-pixel-ratio: 3/2),
         (min-device-pixel-ratio: 1.5),
         (min-resolution: 1.5dppx)"

$mixin background-size($width, $height) {
	-webkit-background-size: $width $height;
	   -moz-background-size: $width $height;
	        background-size: $width $height;
}
```


##������ 
####������Ʈ�� ��α� 
* [Sass ������](http://bkaprt.com/sass/15/)
  Sass�� ���� ��� ������ �ִ� ���� ����. 

* [The Sass Way](http://bkaprt.com/sass/16/)
  'Sass�� ���Ľ��� �̿��� Css �ۼ����� ���� �ֽ� �ҽİ� ������ �ٷ�ϴ�' ' 

* [Css Tricks](http://bkaprt.com/sass/17/)
  Css�� ���� �ۙE���ϴ� �е鿡�� Sass�� �󸶳� ���������� ���� ������ ������ ������ �� �ֽ��ϴ�. 
  ũ���� ���̾��� [��Ÿ�� ���̵�](http://bkaprt.com/sass/18/) �Դϴ�. 

* [Sass �����ϱ�](http://bkaprt.com/sass/19/)
  ���ʺ��� ��ޱ��� ��� �� �ִ� �ڵ� ����(coad school)�� �����ڽ��Դϴ�.

* [Sass �����ϱ�](http://bkaprt.com/sass/20/)
  ���̺� �𸶸�(David Demaree)�� �� ����Ʈ ����Ʈ(A List Apart)�� ����� �Ǹ��� �Թ��ڿ� ���Դϴ�. 

* [Sass�� �̷� �鿩�� ����](http://bkaprt.com/sass/21/)
  ���̺�� ����(David Walsh)�� Sass�� ���� �������� ���� �߰����� ��ɵ餷�� �����ݴϴ�. 


####�ͽ��� ���̺귯�� 

* [���Ľ�.�����ӿ�ũ(Compass.framwork)](http://bkaprt.com/sass/22/)
  ���Ľ��� ũ���� ����Ÿ��(chris eppstenin)�� ���� Sass Ȯ�������ӿ�ũ.  
  ���Ľ��� �̸� �ۼ��� ������ Css ���ϵ��� �����մϴ�. �� ���ϵ��� �� �Ӽ��� ��ȭ�ϸ鼭 ������Ʈ �ǰ� �̿� ���߾� ���߻� ���ξ ���� �����մϴ�.   
  ���Ľ��� ��������Ʈ �̹����� ��ü�� ���� �۾��ϵ��� ���ݴϴ�. 

* [���� ���̺귯��(Bourbon)](http://bkaprt.com/sass/23/)
  '�����ϰ� ������ Sass�� �ͽ��� ���̺귯��'��� ȫ���ϴ� ������ ������ ������� ȸ���� ��Ʈ�� (thoughtbot)�� ���� ��û�� �ͽ��� �ڷḦ �����մϴ�. 
 
* [Handy Sass Mixins](http://bkaprt.com/sass/24/)
  ����ũ �극������(Jake Bresnehan)�� ���� Sass �ͽ��� �÷��� �Դϴ�.

####Sass�� ������ �����ο� ���� �߰��ڷ�.

[Sass�� ������ �������ΰ� �̵�� ������ ���� �� 1](http://bkaprt.com/sass/25/)
[Sass�� ������ �������ΰ� �̵�� ������ ���� �� 2](http://bkaprt.com/sass/26/)

* [Breakpoint](http://bkaprt.com/sass/27/)
  Sass �÷��������� �̵�� ������ �� �� ������ �ۼ��ϰ� ���ݴϴ�.

* [Susy](http://bkaprt.com/sass/28/)
  ���Ľ��� Sass�� �����ڷ� ������ �׸��� �ý����� ����µ� ������ �ݴϴ�.

* [Sassaparilla](http://bkaprt.com/sass/29/)
  �� �����ϱ� ������ �����ӿ�ũ�� ���Ľ��� Sass�� �̿��� ������ �� ������ ������Ʈ�� �����մϴ�.

####Sass��

* [���̾���׸� ���� ���̾�罺](http://bkaprt.com/sass/30/)
  ����� �뵵�� ������ ���̾����� �ֵ��. ���� Sass ���ϸ�� Sass�� �����ϵ� ��Ÿ�Ͻ�Ʈ�� �ٹ�ȣ�� ǥ�����ݴϴ�.

* [Sass�� ũ�� �����ڵ����� �����ϱ�](http://bkaprt.com/sass/31/)
  Sass�� �����ϴ� ���� ũ���� ���� Ȱ���� �� �ִ� ����� ���� �˷��ִ� Ʃ�丮��. 
# Sass Setting

## Sass��.
Sass �� `Sass` �� `SCSS` �ΰ��� �ֽ��ϴ�.
�Ϲ������� �Ѵ� �罺(Sass) ��� �θ��ϴ�.

�̵��� �ణ�� �������� �ֽ��ϴ�.
���� ū�������� �������� �����ݷ� `;` �� �߰�ȣ `{}` �� �ְ� ������ �����Դϴ�.

��:

```SCSS
// SCSS
body {
	color: #333;
	background: #fff;
}
.header {
	color: #333;
	background: #fff;
}
```

```Sass
// Sass
body
	color: #333
	background: #fff
.header
	color: #333
	background: #fff
```

### sass�� Ư¡ : 
a) Sass�� �װ��� css�� ������ ������ ��� �߰��Ѵ�. 

b) ��Ÿ�� ���� ������ �װ��� ������ �ǹ��ϴ��� �˾ƾ��Ѵ�. 

c) �����̳ʵ��� �����ϱ� ���� ��� CSS ȣȯ���� �����ϰ� �ְ�, �� ���۵��� ��� �ϰ����� �����Ѵ�.

d) Sass�� css�� ��ó���� ���ν� �����Ϸ� ������ �Ѵ�.


### ��ó����, ��ó���⿡ ���Ͽ�
�ܾ���� ū �ǹ̴� ��ó����� ���� ó���ϴ°��̰� ��ó����� �Ŀ� ó���ϴ� ���� �˴ϴ�.

���⼭�� ������ css�� �ۼ����� ���ϸ� 

��ó���� : css�� �ۼ��Ǳ� ���� ���Ǵ� ����.

��ó���� : css�� �ۼ����� ���Ǵ� ����.

��� �� �� �ֽ��ϴ�.

���� sass���� ���� ��ó������ �Ҽ��ִµ� ������ ���� �ٸ� ���� �ۼ��� �Ŀ� �� �ڵ带 css�ڵ�� �������Ͽ��� css��� ������� ��°��̱� �����Դϴ�.

�̹ۿ� ��ó����δ� postCss�� cssnext���� �ֽ��ϴ�.




<br>
<br>
<br>

## Sass ȯ�漳��

[Ruby](https://www.ruby-lang.org/ko/), [Node.js](https://nodejs.org/)




## Sass ��ġ

### Sass for Windows


[���ٿ�ε�](http://rubyinstaller.org/downloads/)

��� ������� ���ư��� Sass �̸� windows ȯ�濡�� ruby�� ��ġ������մϴ�.

![�̹���](../images/ruby_install.png)

��ġ �߰��� ������ ȯ�溯�� �ڵ������ üũ���ּ���.

���� ���������Ʈâ����

gem install sass 

��� �Է����ָ� �ڵ����� ��ġ�� �˴ϴ�.


![�̹���](../images/cmd1.png)

![�̹���](../images/cmd2.png)

��ġ�Ϸ�!



### Sass for Mac

�ƿ����� ��� �⺻ ����Ǿ��ֱ� ������ ���� ��� ��ġ�Ͻ� �ʿ䰡 �����ϴ�.

�͹̳��� ������

gem install sass 

��� �Է����ָ� �ڵ����� ��ġ�� �˴ϴ�.

```
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.0.0 directory.
```

��½��� ������ ���ٸ� 

sudo gem install sass ��� �Է��� �ְ� �Ʒα����Ҷ� �Է��ϴ� ��й�ȣ�� �Է��ϸ� ��ġ�� �� �˴ϴ�.

[sudo��ɾ����](https://ko.wikipedia.org/wiki/Sudo)




## Sass ��ɾ�


```sh
$ sass -h # ���� ����
$ sass style.scss(�ۼ�������):style.css(�����ϵ�����) # �ش� ��ɾ �Է��ϸ� ���� ������ ���� ���Ϸ� �������� ������
$ sass --watch style.scss:style.css # ���� ������ ����Ǹ� �����Ͽ� �ڵ����� ���� ���ϸ����� ������ ����
$ sass --style ��Ÿ������ style.scss:style.css # �����ϵǴ� css�� ���������� ��������
$ sass -w -t compact style.scss:style.css # -w �� --watch �� ����̰� -t�� --style �� �����
```

#### style�� ����

��ø(nested) : sass�� �⺻��Ÿ�Ϸ� html����ó�� �θ��ҿ� ���� ������Ҵ� �鿩���� �Ǵ� ����.

```css
ul {
  font-family: Georgia;
  color: #333333; }
  ul li {
    display: inline-block; }
```


Ȯ��(expanded) : �Ϲ����� css ��Ÿ�Ϸ� �����ڿ� ���� �Ӽ��� �鿩���� �Ǵ� ����. ���� ������ �ϴ��� ������ �տ�, �� ul li �տ� ������ �����ϴ�.


```css
ul {
  font-family: Georgia;
  color: #333333;
}
ul li {
  display: inline-block;
}
```


���(compact) : �츮���� �������� ���� ���� ���Ǵ� ��Ÿ�Ϸ� ���پ� ��µǴ� ��Ÿ��. ������ ���� �� �־ �ٹٲ��� ���� �ʽ��ϴ�.


```css
ul { font-family: Georgia; color: #333333; }
ul li { display: inline-block; }
```


����(compress) : �ҽ� ���� ������ ��Ÿ��


```css
ul{font-family:Georgia;color:#333333}ul li{display:inline-block}
```	




## Windows ȯ�濡�� �ѱ�(CP949) ���� �߻� ��, ��� ���ڵ� UTF-8�� ����

```sh
$ sass -E utf-8 sass/style.scss css/style.css # ���ڵ� �ɼ� ���� -E utf-8
```




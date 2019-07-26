# Sass Reference

## Function Directives

sass������ �����Լ����� ����ڰ� ���� �Լ��� ������ �� �ֽ��ϴ�.

```css
$grid-width: 40px;
$gutter-width: 10px;

@function grid-width($n) {
  @return $n * $grid-width + ($n - 1) * $gutter-width;
}

#sidebar { width: grid-width(5); }
```

@function grid-width($n) {
  @return $n * $grid-width + ($n - 1) * $gutter-width;
}

�̺κ��� function�� �����ϴ� �κ��̸� �ڹٽ�ũ��Ʈ�� ����ϰ� �����Ѵٰ� �����Ͻø� �˴ϴ�.

@mixin�� ��������� ����ū �������̶�� @return�� �ִٴ��� ������ �ֽ��ϴ�.

width: grid-width(5); �̷��� ȣ���Ͽ� 5���� function�� ���ؼ� ���Ǽ� �����̵Ǿ����ϴ�.

```css
#sidebar { width: 240px; }
```

@mixin���� ���̸� Ȯ���ϱ����� @mixin�� �̿��� ������ ����� ������ �ϰڽ��ϴ�

```css

$grid-width: 40px;
$gutter-width: 10px;

@function grid-width($n) {
  @return $n * $grid-width + ($n - 1) * $gutter-width;
}

#sidebar { width: grid-width(5); }


@mixin grid-width($n){
	width: $n * $grid-width + ($n - 1) * $gutter-width;
}

#sidebar { @include grid-width(5) }
```

```css
#sidebar { width: 240px; }

#sidebar { width: 240px; }

```
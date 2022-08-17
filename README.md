# goit-markup-hw-07 препроцесор sass

---

```scss
@import "./utils/miins";
@import "./utils/variables;
```

---

## \_placeholders підключення плейсхолдеру @extend

```scss
%link {
  text-decoration: none;
}

.heder__link {
  @extend %link;
  background-color: green;
}

.footer__link {
  @extend %link;
  background-color: red;
}
```

```css
/* отримааємо в css */

.footer__link,
.heder__link {
  text-decoration: none;
}

.heder__link {
  background-color: green;
}

.footer__link {
  background-color: red;
}
```

---

## @mixin

```scss
@mixin name-mixin($type, $color) {
  border-top: 1px $type $color;
  border-bottom: 1px $type $color;
}

p {
  @include name-mixin($type, $color);
}

// змінні за замовчуванням
@mixin name-mixin($type: dashed, $color: #cccccc) {
  border-top: 1px $type $color;
}

p {
  @include name-mixin();
}

//--------
@mixin name($type: flex) {
  display: $type;
  flex-direction: column;
  align-items: center;
}

p {
  @include name(inline-flex);
}
```

## @each, `#{`_$name_`}`, `#{} ` - интерполяция метод

---

```scss
// метод інтерполяції
$icons: "facebook", "github", "linkedin", "twitter";

@each $iconName in $icons {
  .icon-#{$iconName} {
    background-image: url("../images/#{$iconName}.svg");
  }
}
```

```scss
//приклад використання міксіна

$icons: "facebook", "github", "linkedin", "twitter";

@mixin name-mixin($nameList) {
  @each $iconName in $nameList {
    .icon-#{$iconName} {
      background-image: url("../images/#{$iconName}.svg");
    }
  }
}

@include name-mixin($icons);
```

отримаємо в сss

```css
.icon-facebook {
  background-image: url("../images/facebook.svg");
}

.icon-github {
  background-image: url("../images/github.svg");
}

.icon-linkedin {
  background-image: url("../images/linkedin.svg");
}

.icon-twitter {
  background-image: url("../images/twitter.svg");
```

---

## Оператор конкатенації (&) використания

```scss
.btn {
  background-color: aqua;

  .box:hover &,
  .box:focus & {
    background-color: red;
  }
}
```

```css
/* отримаємо в сss */
.btn {
  background-color: aqua;
}
.box:hover .btn,
.box:focus .btn {
  background-color: red;
}
```

# БЕМ

колір задається через модифікатор зовнішня геометрія блока зажається через мікси

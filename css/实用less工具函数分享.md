## hidden text 隐藏文字

```less
.hide-text() {
  font: '0/0' a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
```

## Text Overflow

```less
.text-overflow(@width) {
  width: @width;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

// 同理
.max-text-overflow(@width) {
  max-width: @width;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

## Opacity 透明度

```less
.opacity (@opacity) when (isnumber(@opacity)) and (not (@opacity < 0)) and (not (@opacity > 1)) {
  opacity: @opacity;
}

```

## Image Responsive 图片响应式

```less
.img-responsive(@display: block) {
  display: @display;
  max-width: 100%;
  height: auto;
}
```

## Sizing Shortcuts 布局简写

```less
.size(@width, @height) {
  width: @width;
  height: @height;
}
```

# Draw (快速绘制矩形、圆、三角形)

```less
.square(@size: 0, @unit) {
  width: unit(@size, @unit);
  height: unit(@size, @unit);
}

.circle(@size: 0, @unit) {
  width: unit(@size, @unit);
  height: unit(@size, @unit);
  border-radius: 50%;
}

.triangle(@direction, @size, @color) {
  .triangle(@direction, @size * 2, @size, @color);
}
.triangle(@direction, @width, @height, @color) when (@direction = up) {
  .triangle-base();
  border-left: (@width / 2) solid transparent;
  border-right: (@width / 2) solid transparent;
  border-bottom: @height solid @color;
}
.triangle(@direction, @width, @height, @color) when (@direction = down) {
  .triangle-base();
  border-left: (@width / 2) solid transparent;
  border-right: (@width / 2) solid transparent;
  border-top: @height solid @color;
}
.triangle(@direction, @width, @height, @color) when (@direction = left) {
  .triangle-base();
  border-top: (@width / 2) solid transparent;
  border-bottom: (@width / 2) solid transparent;
  border-right: @height solid @color;
}
.triangle(@direction, @width, @height, @color) when (@direction = right) {
  .triangle-base();
  border-top: (@width / 2) solid transparent;
  border-bottom: (@width / 2) solid transparent;
  border-left: @height solid @color;
}
```

## Layout 布局相关

```less
// 居中
.center-block() {
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.v-center() {
  top: 50%;
  .translateY(-50%);
}

.h-center() {
  left: 50%;
  .translateX(-50%);
}

.font-medium() {
  font-family: PingFangSC-Medium, sans-serif;
}

```

## 箭头

```less
.bottom-arrow(@size, @color: rgb(102, 102, 102)) {
  display: inline-block;
  content: '';
  width: 0;
  border: @size solid transparent;
  border-top-color: @color;
}

```

## Utils 工具

```less
.translateX(@x: 0) {
  transform+_: translateX(@x);
}
.translateY(@y: 0) {
  transform+_: translateY(@y);
}
.triangle-base() {
  content: '';
  display: block;
  width: 0;
  height: 0;
}
.clear() {
  &:before,
  &:after {
    content: ' ';
    display: table;
    line-height: 0;
  }
  &:after {
    clear: both;
  }
}

.text-ellipsis(@line: 1) {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
  -webkit-line-clamp: @line;
}

```
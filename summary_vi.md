### Hoạt ảnh bouncing khi tải trang

`Creates a bouncing loader animation.`

Tạo hoạt ảnh nảy lên khi tải trang.
#### HTML

```html
<div class="bouncing-loader">
  <div></div>
  <div></div>
  <div></div>
</div>
```

#### CSS

```css
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.bouncing-loader {
  display: flex;
  justify-content: center;
}
.bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__bouncing-loader">
  	<div></div>
    <div></div>
    <div></div>
  </div>
</div>

<style>
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.snippet-demo__bouncing-loader {
  display: flex;
  justify-content: center;
}
.snippet-demo__bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.snippet-demo__bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.snippet-demo__bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
</style>

#### Giải thích

Ghi chú: `1rem` tương đương `16px`.

1. Ta sử dụng tag `@keyframes` để định nghĩa hiệu ứng có 2 trạng thái, khi thành phần thay đổi độ trong suốt `opacity` và nó được dịch chuyển lên trong mặt phẳng 2D thì sử dụng thuộc tính `transform: translateY()`.

2. `.bouncing-loader` là khối chứa các hình tròn có hiệu ứng nảy lên  và các hình tròn đó có sử dụng các thuộc tính`display: flex`
   và `justify-content: center` để cố định vị trí của chúng vào giữa ( theo chiều dọc ).

3. thành phần `.bouncing-loader > div`, tập trung vào 3 thẻ con `div` nằm trong class cha `.bouncing-loader` để định dạng. Các thẻ `div`s được đặt các giá trị width và height là`1rem`, sử dụng thêm thuộc tính `border-radius: 50%` để chuyển nó từ hình vuông thành hình tròn.

4. Thuộc tính `margin: 3rem 0.2rem` để quy định mỗi hình tròn cách viền trên, dưới 1 khoảng `3rem` và cách viền trái/phải 1 khoảng `0.2rem` vì thế các hình tròn không bị chạm vào nhau, cách nhau 1 khoảng trống.

5. Thuộc tính `animation` mà một thuộc tính được dùng để viết chung cho các thuộc tính khác như: `animation-name`, `animation-duration`, `animation-iteration-count`, `animation-direction`.

6. Thuộc tính `nth-child(n)` nhắm tới các thành phần là con thứ n của thẻ cha chứa nó.

7. Thuộc tính `animation-delay` thường được sử dụng cho các thẻ div thứ 2, thứ 3, để mỗi phần tử không bắt đầu cái hiệu ứng cùng một lúc.

#### Hỗ trợ các trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-animation

<!-- tags: animation -->
### Đặt lại các kích thước của khối

Đặt lại kích thước khối sao cho các thuộc tính `width` và `height` Không bị ảnh hưởng bởi giá trị của thuộc tính `border` hoặc `padding`.

#### CSS

```css
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__box-sizing-reset">Demo</div>
</div>

<style>
.snippet-demo__box-sizing-reset {
  box-sizing: border-box;
  width: 200px;
  padding: 1.5em;
  color: #7983ff;
  font-family: sans-serif;
  background-color: white;
  border: 5px solid;
}
</style>

#### Giải thích

1. Sử dụng thuộc tính `box-sizing: border-box` là một cách để các giá trị của `padding` hoặc `border`không làm ảnh hưởng tới các giá trị `width` or `height`.
2. Sử dụng thuộc tính `box-sizing: inherit` cho 1 phần tử để nó buộc phải tuân theo những quy tắc trong thuộc tính `box-sizing` của thẻ cha.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Không có cảnh báo.</span>

* https://caniuse.com/#feat=css3-boxsizing

<!-- tags: layout -->
### Clearfix

Hãy chắc chắn là các phần tử con trong nó tự xoá các giá trị thuộc tính của chúng.

**Ensures that an element self-clears its children.**

###### Ghi chú: Việc này chỉ có tác dụng khi bạn sử dụng thuộc tính Float trong khi xây dựng bố cục trang web. This is only useful if you are still using float to build layouts. Cân nhắc việc sử dụng các bố cục hiện đại như flexbox hoặc grid.

#### HTML

```html
<div class="clearfix">
  <div class="floated">float a</div>
  <div class="floated">float b</div>
  <div class="floated">float c</div>
</div>
```

#### CSS

```css
.clearfix::after {
  content: '';
  display: block;
  clear: both;
}

.floated {
  float: left;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__clearfix">
    <div class="snippet-demo__floated">float a</div>
    <div class="snippet-demo__floated">float b</div>
    <div class="snippet-demo__floated">float c</div>
  </div>
</div>

<style>
.snippet-demo__clearfix::after {
  content: '';
  display: block;
  clear: both;
}

.snippet-demo__floated {
  float: left;
}
</style>

#### Giải thích

1. thuộc tính `.clearfix::after` tạo ra 1 phần tử ảo (phần tử giả).
2. thuộc tính `content: ''` cho phép các phần tử có thể gây ảnh hưởng tới bố cục.
3. thuộc tính `clear: both` chỉ định về bên trái, bên phải hoặc cả 2 bên của phần tử đó không liền kề nó trong cùng một khối.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Để thuộc tính này có thể làm việc hiệu quả, bạn cần đảm bảo nó không có phần tử con còn thuộc tính float trong khối chứa nó, và không có phần tử nào chứa thuộc tính float trước khi được clearfix nhưng nó phải ở trong cùng 1 bối cảnh định dạng giống nhau.</span>

<!-- tags: layout -->
### Cố định tỷ lệ chiều rộng với chiều cao

Với mỗi biến chiều rộng của phần tử, nó sẽ đảm bảo chiều cao luôn tương xứng với responsive.

Given an element of variable width, it will ensure its height remains proportionate in a responsive fashion
(tức là chiều rộng và chiều cao không đổi).

#### HTML

```html
<div class="constant-width-to-height-ratio"></div>
```

#### CSS

```css
.constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.constant-width-to-height-ratio::before {
  content: '';
  display: block;
  padding-top: 100%;
  float: left;
}
.constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
```

#### Demo
Thay đổi kích thước cửa sổ để thấy tỷ lệ của phần tử đó vẫn giữ nguyên.


<div class="snippet-demo">
  <div class="snippet-demo__constant-width-to-height-ratio"></div>
</div>

<style>
.snippet-demo__constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.snippet-demo__constant-width-to-height-ratio::before {
  content: '';
  display: block;
  padding-top: 100%;
  float: left;
}
.snippet-demo__constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
</style>

#### Giải thích

thuộc tính `padding-top` trong phần tử ảo `::before` luôn giữ nguyên tỷ lệ giữa chiều cao và chiều rộng.Vì thế chiều cao của phần tử sẽ luôn đạt 100% khi chiều rộng phần tử đạt 100%, nó tạo ra 1 hình vuông có thể co dãn.

Phương pháp này giúp cho nội dung bên trong phần tử có thể thể hiện một cách bình thường.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: layout -->
### Phân phối các phần tử con

Phân phối đều các phần tử con trong các phần tử cha.

#### HTML

```html
<div class="evenly-distributed-children">
  <p>Item1</p>
  <p>Item2</p>
  <p>Item3</p>
</div>
```

#### CSS

```css
.evenly-distributed-children {
  display: flex;
  justify-content: space-between;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__evenly-distributed-children">
    <p>Item1</p>
    <p>Item2</p>
    <p>Item3</p>
  </div>
</div>

<style>
.snippet-demo__evenly-distributed-children {
  display: flex;
  width: 100%;  
  justify-content: space-between;
}
</style>

#### Giải thích

1. thuộc tính `display: flex` giúp cho phần tử đó có thể sử dụng kĩ thuật flexbox.
2. thuộc tính `justify-content: space-between` khiến các phần tử con được phân phối đều theo chiều ngang. Phần tử con đầu tiên nằm ở cạnh bên trái, trong khi phần tử con cuối cùng lại ở cạnh bên phải.

Một cách khác là sử dụng thuộc tính `justify-content: space-around` để phân bố các phần tử con trong nó với các khoảng trống xung quanh chúng, thay vì chỉ nằm giữa chúng.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Cần các tiền tố để được hỗ trợ đầy đủ</span>

* https://caniuse.com/#feat=flexbox

<!-- tags: layout -->
### Flexbox centering

Đặt các phần tử con ở giữa trung tâm phần tử cha theo chiều dọc và ngang khi sử dụng thuộc tính `flexbox`.

#### HTML

```html
<div class="flexbox-centering">
  <div class="child">Centered content.</div>
</div>
```

#### CSS

```css
.flexbox-centering {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__flexbox-centering">
    <p class="snippet-demo__flexbox-centering__child">Centered content.</p>
  </div>
</div>

<style>
.snippet-demo__flexbox-centering {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
}
</style>

#### Giải thích

1. thuộc tính `display: flex` để cho phép sử dụng flexbox.
2. thuộc tính `justify-content: center` khiến các phần tử con nằm giữa theo chiều ngang.
3. thuộc tính `align-items: center` khiến các phần tử con nằm giữa theo chiều dọc.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Cần các tiền tố để được hỗ trợ đầy đủ.</span>

* https://caniuse.com/#feat=flexbox

<!-- tags: layout -->
### Grid centering

Đặt các phần tử con vào giữa phần tử cha theo chiều dọc và chiều ngang, sử dụng `grid`.

#### HTML

```html
<div class="grid-centering">
  <div class="child">Centered content.</div>
</div>
```

#### CSS

```css
.grid-centering {
  display: grid;
  justify-content: center;
  align-items: center;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__grid-centering">
    <p class="snippet-demo__grid-centering__child">Centered content.</p>
  </div>
</div>

<style>
.snippet-demo__grid-centering {
  display: grid;
  justify-content: center;
  align-items: center;
  height: 200px;
}
</style>

#### Giải thích

1. thuộc tính `display: grid` cho phép sử dụng grid.
2. thuộc tính `justify-content: center` giúp căn giữa các phần tử con theo chiều ngang.
3. thuộc tính `align-items: center` giúp căn giữa các phần tử con theo chiều dọc.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-grid

<!-- tags: layout -->
### Bố cục sử dụng Grid

Bố cục cơ bản của website sử dụng `grid`.

#### HTML

```html
<div class="grid-layout">
  <div class="header">Header</div>
  <div class="sidebar">Sidebar</div>
  <div class="content">
    Content
    <br>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit.
  </div>
  <div class="footer">Footer</div>
</div>
```

#### CSS

```css
.grid-layout {
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    'sidebar header header'
    'sidebar content content'
    'sidebar footer  footer';
  color: white;
}
.grid-layout > div {
  background: #333;
  padding: 10px;
}
.sidebar {
  grid-area: sidebar;
}
.content {
  grid-area: content;
}
.header {
  grid-area: header;
}
.footer {
  grid-area: footer;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__grid-layout">
    <div class="box snippet-demo__grid-layout__header">Header</div>
    <div class="box snippet-demo__grid-layout__sidebar">Sidebar</div>
    <div class="box snippet-demo__grid-layout__content">Content
      <br> Lorem ipsum dolor sit amet, consectetur adipisicing elit.
    </div>
    <div class="box snippet-demo__grid-layout__footer">Footer</div>
  </div>
</div>

<style>
.snippet-demo__grid-layout {
  margin: 1em;
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    "sidebar header header"
    "sidebar content content"
    "sidebar  footer  footer";
  background-color: #fff;
  color: white;
}
.snippet-demo__grid-layout > div {
  background: #333;
  padding: 10px;
}
.snippet-demo__grid-layout__sidebar {
    grid-area: sidebar;
}
.snippet-demo__grid-layout__content {
    grid-area: content;
}
.snippet-demo__grid-layout__header {
    grid-area: header;
}
.snippet-demo__grid-layout__footer {
    grid-area: footer;
}
</style>

#### Giải thích

1. thuộc tính `display: grid` cho phép sử dụng grid.
2. thuộc tính `grid-gap: 10px` định nghĩa khoảng trống giữa các phần tử.
3. thuộc tính `grid-template-columns: repeat(3, 1fr)` định nghĩa là 3 côt có cùng 1 kích thước.
4. thuộc tính `grid-template-areas` định nghĩa tên cho các vùng grid đó.
5. thuộc tính `grid-area: sidebar` gán tên cho thành phần sử dụng vùng đó là `sidebar`.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-grid

<!-- tags: layout -->
### Lược bỏ text

Nếu đoạn văn bản dài hơn 1 dòng nó sẽ loại bỏ và cho kết thúc bằng dấu `…`.

#### HTML

```html
<p class="truncate-text">If I exceed one line's width, I will be truncated.</p>
```

#### CSS

```css
.truncate-text {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  width: 200px;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__truncate-text">
    This text will be truncated if it exceeds 200px in width.
  </p>
</div>

<style>
.snippet-demo__truncate-text {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  width: 200px;
  margin: 0;
}
</style>

#### Giải thích

1. thuộc tính `overflow: hidden` ngăn không cho đoạn văn bản vượt ra khỏi kích thước của nó.
   (đối với một khối , độ rộng là  100% và chiều cao tự động).
2. thuộc tính `white-space: nowrap` ngăn không cho đoạn văn bản lớn hơn 1 dòng.
3. thuộc tính `text-overflow: ellipsis` khiến cho đoạn văn bản nếu vượt quá kích thước của nó sẽ kết thúc bằng dấu `...`
4. thuộc tính `width: 200px;` để đảm bảo phần tử có kích thước, và biết được khi nào cần có dấu `...`.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ chỉ làm việc trên các phần tử chỉ có một dòng.</span>

* https://caniuse.com/#feat=text-overflow

<!-- tags: layout -->
### Vòng tròn

Tạo hình tròn với CSS thuần

#### HTML

```html
<div class="circle"></div>
```

#### CSS

```css
.circle {
  border-radius: 50%;
  width: 2rem;
  height: 2rem;
  background: #333;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__circle"></div>
</div>

<style>
.snippet-demo__circle {
  border-radius: 50%;
  width: 2rem;
  height: 2rem;
  background: #333;
}
</style>

#### Giải thích

thuộc tính `border-radius: 50%` làm cong viền của phần tử để tạo ra hình tròn.
Vì 1 hình tròn sẽ có chiều rộng và chiều cao bằng nhau. nếu khác nhau nó sẽ tạo ra hình elipse.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=border-radius

<!-- tags: visual -->
### Tuỳ chỉnh thanh cuộn

Tùy chỉnh mẫu thanh cuộn cho các tài liệu và các phần tử với scrollable overflow, trên nền tảng WebKit.

#### HTML

```html
<div class="custom-scrollbar">
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
</div>
```

#### CSS

```css
/* Document scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  border-radius: 10px;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}

/* Scrollable element */
.some-element::webkit-scrollbar {
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__custom-scrollbar">
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?
    </p>
  </div>
</div>

<style>
.snippet-demo__custom-scrollbar {
  height: 100px;
  overflow: auto;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar {
  width: 8px;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar-thumb {
  border-radius: 10px;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}
</style>

#### Giải thích

1. thuộc tính `::-webkit-scrollbar` tập trung vào toàn bộ thành phần của thanh cuộn.
2. thuộc tính `::-webkit-scrollbar-track` tập trung vào phần track của thanh cuộn.
3. thuộc tính `::-webkit-scrollbar-thumb` tập trung vào hình dạng thanh cuộn.

Có rất nhiều mẫu khác nhau để bạn có thể áp dụng vào tạo mẫu thanh cuộn. Chi tiết hơn tại [WebKit Blog](https://webkit.org/blog/363/styling-scrollbars/)

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ Kiểu thanh cuốn không xuất hiện trên các đường tiêu chuẩn.</span>

* https://caniuse.com/#feat=css-scrollbar

<!-- tags: visual -->
### Tuỳ chỉnh bộ chọn văn bản

thay đổi định dạng văn bản được chọn.

#### HTML

```html
<p class="custom-text-selection">Select some of this text.</p>
```

#### CSS

```css
::selection {
  background: aquamarine;
  color: black;
}
.custom-text-selection::selection {
  background: deeppink;
  color: white;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__custom-text-selection">Select some of this text.</p>
</div>

<style>
.snippet-demo__custom-text-selection::selection {
  background: deeppink;
  color: white;
}
.snippet-demo__custom-text-selection::-moz-selection {
  background: deeppink;
  color: white;
}
</style>

#### Giải thích

thuộc tính `::selection` định nghĩa bộ chọn mẫu trên 1 phần tử để tạo mẫu văn bản bên trong nó khi được chọn. chú ý là với mọi phần tử được chọn, nếu bạn không tuỳ chỉnh 1 mẫu khác thì nó sẽ trở lại định dạng ban đầu.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ Yêu cầu tiền tố để hỗ trợ đầy đủ và không thực sự đúng trong bất kỳ hoàn cảnh nào.</span>

* https://caniuse.com/#feat=css-selection

<!-- tags: visual -->
### Đổ bóng động

Tạo một bóng tương tự như thuộc tính `box-shadow` nhưng dựa trên màu của chính phần tử đó.

#### HTML

```html
<div class="dynamic-shadow-parent">
  <div class="dynamic-shadow"></div>
</div>
```

#### CSS

```css
.dynamic-shadow-parent {
  position: relative;
  z-index: 1;
}
.dynamic-shadow {
  position: relative;
  width: 10rem;
  height: 10rem;
  background: linear-gradient(75deg, #6d78ff, #00ffb8);
}
.dynamic-shadow::after {
  content: '';
  width: 100%;
  height: 100%;
  position: absolute;
  background: inherit;
  top: 0.5rem;
  filter: blur(0.4rem);
  opacity: 0.7;
  z-index: -1;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__dynamic-shadow-parent">
    <div class="snippet-demo__dynamic-shadow"></div>
  </div>
</div>

<style>
.snippet-demo__dynamic-shadow-parent {
  position: relative;
  z-index: 1;
}
.snippet-demo__dynamic-shadow {
  position: relative;
  width: 10rem;
  height: 10rem;
  background: linear-gradient(75deg, #6d78ff, #00ffb8);
}
.snippet-demo__dynamic-shadow::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  background: inherit;
  top: 0.5rem;
  filter: blur(0.4rem);
  opacity: 0.7;
  z-index: -1;
}
</style>

#### Giải thích

Phần này yêu cầu 1 tập định nghĩa các thuộc tính phức tạp để thể hiện được, tương tự như một phần tử ảo sẽ được đặt giứa chính nó trong khi nó vẫn hiện ra.


1. thuộc tính `position: relative` ở phần tử cha thiết lập được định nghĩa về  vị trí Cartersian cho các phần tử con.
2. thuộc tính `z-index: 1` thiết lập một lớp bối cảnh xếp chồng lên nhau mới.
3. thuộc tính `position: relative` trong các phần tử con thiết lập ngữ cảnh về vị trí cho phần tử ảo ấy.
4. `::after` định nghĩa một phần tử giả.
5. thuộc tính `position: absolute` tách phần tử con ra khỏi sự phụ thuộc vào phần tử cha và thiết lập mối quan hệ về vị trí đối với phần tử cha.
6. thuộc tính `width: 100%` và `height: 100%` thiết lập kích thước của phần tử ảo bằng kích thước của phần tử cha.
7.thuộc tính `background: inherit` giúp cho phần tử đó kế thừa được các thuộc tính của phần tử được xác định trước đó.
8. thuộc tính  `top: 0.5rem` tạo khoảng cách của phần tử đó với phần tử cha chứa nó.
9. thuộc tính `filter: blur(0.4rem)` sẽ làm mờ phần tử giả đó , tạo ra một vùng bóng ở phía dưới đó.
10.thuộc tính  `opacity: 0.7` khiến cho phần tử đó trong suốt.
11.thuộc tính `z-index: -1` đặt vị trí của phần tử giả ra phía sau cảu phần tử cha của nó..

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ Requires prefixes for full support.</span>

* https://caniuse.com/#feat=css-filters

<!-- tags: visual -->
### Etched text

Tạo hiệu ứng khắc lên nền ở vùng có chữ.


#### HTML

```html
<p class="etched-text">I appear etched into the background.</p>
```

#### CSS

```css
.etched-text {
  text-shadow: 0 2px white;
  font-size: 1.5rem;
  font-weight: bold;
  color: #b8bec5;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__etched-text">I appear etched into the background.</p>
</div>

<style>
.snippet-demo__etched-text {
  font-size: 1.5rem;
  font-weight: bold;
  color: #b8bec5;
  text-shadow: 0 2px 0 white;
}
</style>

#### Giải thích

thuộc tính `text-shadow: 0 2px white` tạo ra 1 bóng trắng nhô theo chiều ngang `0px` và `2px` theo chiều dọc tính từ vị trí ban đầu.

Màu nền phải tối hơn màu bóng để hiệu ứng có thể hiện rõ
Màu văn bản phải hơi hạt hơn để tạo hiệu ứng giống như là khắc vào nền.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-textshadow

<!-- tags: visual -->
### Gradient text

tạo ra 1 vùng màu thay đổi.


#### HTML

```html
<p class="gradient-text">Gradient text</p>
```

#### CSS

```css
.gradient-text {
  background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__gradient-text">
    Gradient text
  </p>
</div>

<style>
.snippet-demo__gradient-text {
  background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
  font-size: 2rem;
  font-weight: bold;
  margin: 0;
}
</style>

#### Giải thích

1. thuộc tính `background: -webkit-linear-gradient(...)` tạo cho văn bản 1 màu nền là 1 dải màu.
2. thuộc tính `webkit-text-fill-color: transparent` làm cho đoạn văn bản có màu trong suốt
3. thuộc tính `webkit-background-clip: text` clips the background with the text, filling the text with
   the gradient background as the color.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ Uses non-standard properties.</span>

* https://caniuse.com/#feat=text-stroke

<!-- tags: visual -->
### Tạo viền dạng lượn sóng

tạo cho phần tử 1 đường viền rộng 1px, là sắc nét.

#### HTML

```html
<div class="hairline-border">text</div>
```

#### CSS

```css
.hairline-border {
  box-shadow: 0 0 0 1px;
}

@media (min-resolution: 2dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.5px;
  }
}

@media (min-resolution: 3dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.33333333px;
  }
}

@media (min-resolution: 4dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.25px;
  }
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__hairline-border">Text with a hairline border around it.</p>
</div>

<style>
.snippet-demo__hairline-border {
  box-shadow: 0 0 0 1px;
}

@media (min-resolution: 2dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.5px;
  }
}

@media (min-resolution: 3dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.33333333px;
  }
}

@media (min-resolution: 4dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.25px;
  }
}
</style>

#### Giải thích

1. thuộc tính `box-shadow`  thêm vào phần tử đó 1 điểm ảnh phụ có thể lan rộng khi sử dụng*.
2. Sử dụng `@media (min-resolution: ...)` đẻ kiểm tra mật độ điểm ảnh của thiết bị (`1dppx` equals 96 DPI),
   sao đó cài đặt độ rộng `box-shadow` bằng `1 / dppx`.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ Needs alternate syntax and JavaScript user agent checking for full support.</span>

* https://caniuse.com/#feat=css-boxshadow
* https://caniuse.com/#feat=css-media-resolution

<hr>

\*Chrome does not support subpixel values on `border`. Safari does not support subpixel values on `box-shadow`. Firefox supports subpixel values on both.

<!-- tags: visual -->
### Overflow scroll gradient
thêm 1 thanh cuộn để hiển thị tốt hơn phần nội dung cuộn được.

#### HTML

```html
<div class="overflow-scroll-gradient">
  <div class="overflow-scroll-gradient__scroller">
    Content to be scrolled
  </div>
</div>
```

#### CSS

```css
.overflow-scroll-gradient {
  position: relative;
}
.overflow-scroll-gradient::after {
  content: '';
  position: absolute;
  bottom: 0;
  width: 240px;
  height: 25px;
  background: linear-gradient(
    rgba(255, 255, 255, 0.001),
    white
  ); /* transparent keyword is broken in Safari */
  pointer-events: none;
}
.overflow-scroll-gradient__scroller {
  overflow-y: scroll;
  background: white;
  width: 240px;
  height: 200px;
  padding: 15px 0;
  line-height: 1.2;
  text-align: center;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__overflow-scroll-gradient">
    <div class="snippet-demo__overflow-scroll-gradient__scroller">
      Content to be scrolled
    </div>
  </div>
</div>

<style>
.snippet-demo__overflow-scroll-gradient {
  position: relative;
}
.snippet-demo__overflow-scroll-gradient::after {
  content: '';
  background: linear-gradient(rgba(255, 255, 255, 0.001), white);
  position: absolute;
  width: 240px;
  height: 25px;
  bottom: 0;
  pointer-events: none;
}
.snippet-demo__overflow-scroll-gradient__scroller {
  overflow-y: scroll;
  background: white;
  width: 240px;
  height: 200px;
  padding: 15px 0;
  line-height: 1.2;
  text-align: center;
}
</style>

<script>
document.querySelector('.snippet-demo__overflow-scroll-gradient__scroller').innerHTML = 'content '.repeat(100)
</script>

#### Giải thích

1.thuộc tính `position: relative` để tạo khung tại phần tử này, giúp các phần tử giả có thể định vị được.
2. `::after` để định nghĩa phần tử giả đó.
3. thuộc tính `background-image: linear-gradient(...)` thêm 1 dải màu mờ dần từ trong suốt sang trắng.( trên xuống dưới)
4. thuộc tính  `position: absolute` tách phần tử con ra khỏi sự phụ thuộc vào phần tử cha và thiết lập mối quan hệ về vị trí đối với phần tử cha.
5. thuộc tính `width: 240px` giúp cho phần tử có hiệu ứng cuộn có phù hợp với kích thước đó.(which is a child of the parent that has
   the pseudo element).
6. thuộc tính `height: 25px` là chiều cao của phần tử giả ấy, nên để nó nhỏ.
7. thuộc tính `bottom: 0` đặt vị trí của phần tử giả tại phía dưới cùng của phần tử cha nó.
8. thuộc tính `pointer-events: none` là thuộc tính đặc biệt cho phép phần tử ảo không tương tác với các sự kiện của chuột, cho phép văn bản sau nó có thể được lựa chọn, tương tác.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-gradients

<!-- tags: visual -->
### Pretty text underline

Một thuộc tính tốt hơn thay thế cho `text-decoration: underline` khi cần gạch chân.
Nó thực hiện 1 cách tự nhiên như `text-decoration-skip-ink: auto` nhưng nó được kiểm soát tốt hơn gạch chân.

#### HTML

```html
<p class="pretty-text-underline">Pretty text underline without clipping descending letters.</p>
```

#### CSS

```css
.pretty-text-underline {
  font-family: Arial, sans-serif;
  display: inline;
  font-size: 18px;
  text-shadow: 1px 1px 0 #f5f6f9, -1px 1px 0 #f5f6f9, -1px -1px 0 #f5f6f9, 1px -1px 0 #f5f6f9;
  background-image: linear-gradient(90deg, currentColor 100%, transparent 100%);
  background-position: 0 0.98em;
  background-repeat: repeat-x;
  background-size: 1px 1px;
}
.pretty-text-underline::-moz-selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
.pretty-text-underline::selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__pretty-text-underline">Pretty text underline without clipping descending letters.</p>
</div>

<style>
.snippet-demo__pretty-text-underline {
  font-family: Arial, sans-serif;
  display: inline;
  font-size: 18px !important;
  text-shadow: 1px 1px 0 #f5f6f9,
    -1px 1px 0 #f5f6f9,
    -1px -1px 0 #f5f6f9,
    1px -1px 0 #f5f6f9;
  background-image: linear-gradient(90deg, currentColor 100%, transparent 100%);
  background-position: 0 0.98em;
  background-repeat: repeat-x;
  background-size: 1px 1px;
}

.snippet-demo__pretty-text-underline::-moz-selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}

.snippet-demo__pretty-text-underline::selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
</style>

#### Giải thích

1. thuộc tính `text-shadow: ...` có 4 giá trị với độ phủ vùng là 4x4pixel để đảm bảo việc gạch dưới có 1 cái bóng đủ rộng để che phủ đường gạch  dưới đó. Sử dụng màu sắc trùng với màu nền. với các font chữ lớn, sử dụng số px lớn.
2. thuộc tính `background-image: linear-gradient(...)` tạo 1 gradient 1 góc 90deg với màu chữ hiện tại.
3. The `background-*` các thuộc tính có kích thước gradient như 1x1px ở phía dưới và lặp lại nó dọc theo trục x
4. The `::selection` đảm bảo bóng của văn bản không ảnh hưởng tới văn bản được chọn.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️Khoảng cách gạch chân từ văn bản phụ thuộc vào số liệu nội bộ của phông chữ, do đó bạn phải đảm bảo mọi người đều thấy cùng một phông chữ (tức là không có phông chữ hệ thống thay đổi dựa trên hệ điều hành)
.</span>

* https://caniuse.com/#feat=css-textshadow
* https://caniuse.com/#feat=css-gradients

<!-- tags: visual -->
### Đặt lại các định dạng

đặt lại tất cả các định dạng với 1 thuộc tính. nó không ảnh hưởng các tính chất như `direction` và `unicode-bidi`.

#### HTML

```html
<div class="reset-all-styles">
  <h4>Title</h4>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
</div>
```

#### CSS

```css
.reset-all-styles {
  all: initial;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__reset-all-styles">
    <h3>Title</h3>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
  </div>
</div>

<style>
.snippet-demo__reset-all-styles {
  all: initial;
}
</style>

#### Giải thích

The `all` cho phép bạn đặt lại các giá trị mặc định.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ MS Edge status is under consideration.</span>

* https://caniuse.com/#feat=css-all

<!-- tags: visual -->
### Shape separator

Sử dụng một hình dạng SVG để tách hai khối khác nhau để tạo ra một hình ảnh thú vị hơn phân chia ngang theo tiêu chuẩn.


#### HTML

```html
<div class="shape-separator"></div>
```

#### CSS

```css
.shape-separator {
  position: relative;
  height: 48px;
  background: #333;
}
.shape-separator::after {
  content: '';
  background-image: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiIHN0cm9rZS1taXRlcmxpbWl0PSIxLjQxNCI+PHBhdGggZD0iTTEyIDEybDEyIDEySDBsMTItMTJ6IiBmaWxsPSIjZmZmIi8+PC9zdmc+);
  position: absolute;
  width: 100%;
  height: 24px;
  bottom: 0;
}
```

#### Demo

<div class="snippet-demo is-distinct">
  <div class="snippet-demo__shape-separator"></div>
</div>

<style>
.snippet-demo__shape-separator {
  position: relative;
  height: 48px;
  margin: -0.75rem -1.25rem;
}
.snippet-demo__shape-separator::after {
  content: '';
  background-image: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiIHN0cm9rZS1taXRlcmxpbWl0PSIxLjQxNCI+PHBhdGggZD0iTTEyIDEybDEyIDEySDBsMTItMTJ6IiBmaWxsPSIjZmZmIi8+PC9zdmc+);
  position: absolute;
  width: 100%;
  height: 24px;
  bottom: 0;
}
</style>

#### Giải thích

1. thuộc tính `position: relative` để tạo khung tại phần tử này, giúp các phần tử giả có thể định vị được.
2.  `::after` để định nghĩa phần tử giả đó.
3. `background-image: url(...)` adds the SVG shape (a 24x24 triangle in base64 format) as the background image
   of the pseudo element, which repeats by default. It must be the same color as the block that is being
   separated.
4. thuộc tính  `position: absolute` tách phần tử con ra khỏi sự phụ thuộc vào phần tử cha và thiết lập mối quan hệ về vị trí đối với phần tử cha.
5. `width: 100%`  đảm bảo phần tử trải dài toàn bộ chiều rộng của thẻ cha.

6. thuộc tính `height: 24px` để đặt chiều cao phần tử thành 1 khối 
7. thuộc tính `bottom: 0` đặt vị trí của phần tử giả tại phía dưới cùng của phần tử cha nó.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=svg

<!-- tags: visual -->
### System font stack
Sử dụng font chữ sẵn có trong máy để có thể hiển thị đúng.

#### HTML

```html
<p class="system-font-stack">This text uses the system font.</p>
```

#### CSS

```css
.system-font-stack {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu,
    Cantarell, 'Helvetica Neue', Helvetica, Arial, sans-serif;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__system-font-stack">This text uses the system font.</p>
</div>

<style>
.snippet-demo__system-font-stack {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", Helvetica, Arial, sans-serif;
}
</style>

#### Giải thích

Trình duyệt tìm kiếm các phông chữ liên tiếp, chọn font đầu tiên nếu có thể, và chọn font kế tiếp nếu nó không thể tìm thấy phông chữ (trên hệ thống hoặc được định nghĩa trong CSS).

1. thuộc tính `-apple-system` là San Francisco, sử dụng cho iOS và macOS (not Chrome however)
2. thuộc tính `BlinkMacSystemFont` là San Francisco, sử dụng cho macOS Chrome
3. `Segoe UI` is used on Windows 10
4. `Roboto` is used on Android
5. `Oxygen-Sans` is used on GNU+Linux
6. `Ubuntu` is used on Linux
7. `"Helvetica Neue"` and `Helvetica` is used on macOS 10.10 and below (wrapped in quotes because it has a space)
8. `Arial` là font được hỗ trợ trên mọi hệ điều hành
9. `sans-serif` là font được dùng khi không có font nào được hỗ trợ.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: visual -->
### Triangle

Creates a triangle shape with pure CSS.

#### HTML

```html
<div class="triangle"></div>
```

#### CSS

```css
.triangle {
  width: 0;
  height: 0;
  border-top: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__triangles">
    <div class="snippet-demo__triangle snippet-demo__triangle-1"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-2"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-3"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-4"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-5"></div>
  </div>
</div>

<style>
.snippet-demo__triangles {
  display: flex;
  align-items: center;
}

.snippet-demo__triangle {
  display: inline-block;
  width: 0;
  height: 0;
  margin-right: 0.25rem;
}

.snippet-demo__triangle-1 {
  border-top: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}

.snippet-demo__triangle-2 {
  border-bottom: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}

.snippet-demo__triangle-3 {
  border-left: 20px solid #333;
  border-top: 20px solid transparent;
  border-bottom: 20px solid transparent;
}

.snippet-demo__triangle-4 {
  border-right: 20px solid #333;
  border-top: 20px solid transparent;
  border-bottom: 20px solid transparent;
}

.snippet-demo__triangle-5 {
  border-top: 40px solid #333;
  border-left: 15px solid transparent;
  border-right: 15px solid transparent;
}
</style>

#### Giải thích

[View this link for a detailed complain.](https://stackoverflow.com/q/7073484)

The color of the border is the color of the triangle. The side the triangle tip points
corresponds to the opposite `border-*` property. For example, a color on `border-top`
means the arrow points downward.

Experiment with the `px` values to change the proportion of the triangle.
#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: visual -->
### Bouncing loader

Creates a bouncing loader animation.

#### HTML

```html
<div class="bouncing-loader">
  <div></div>
  <div></div>
  <div></div>
</div>
```

#### CSS

```css
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.bouncing-loader {
  display: flex;
  justify-content: center;
}
.bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__bouncing-loader">
  	<div></div>
    <div></div>
    <div></div>
  </div>
</div>

<style>
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.snippet-demo__bouncing-loader {
  display: flex;
  justify-content: center;
}
.snippet-demo__bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.snippet-demo__bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.snippet-demo__bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
</style>

#### Giải thích

Note: `1rem` is usually `16px`.

1. `@keyframes` defines an animation that has two states, where the element changes `opacity` and is translated up on the 2D plane using `transform: translateY()`.

2. `.bouncing-loader` is the parent container of the bouncing circles and uses `display: flex`
   and `justify-content: center` to position them in the center.

3. `.bouncing-loader > div`, targets the three child `div`s of the parent to be styled. The `div`s are given a width and height of `1rem`, using `border-radius: 50%` to turn them from squares to circles.

4. `margin: 3rem 0.2rem` specifies that each circle has a top/bottom margin of `3rem` and left/right margin
   of `0.2rem` so that they do not directly touch each other, giving them some breathing room.

5. `animation` is a shorthand property for the various animation properties: `animation-name`, `animation-duration`, `animation-iteration-count`, `animation-direction` are used.

6. `nth-child(n)` targets the element which is the nth child of its parent.

7. `animation-delay` is used on the second and third `div` respectively, so that each element does not start the animation at the same time.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-animation

<!-- tags: animation -->
### Donut spinner

Creates a donut spinner that can be used to indicate the loading of content.

#### HTML

```html
<div class="donut"></div>
```

#### CSS

```css
@keyframes donut-spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.donut {
  display: inline-block;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #7983ff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: donut-spin 1.2s linear infinite;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__donut-spinner"></div>
</div>

<style>
@keyframes snippet-demo__donut-spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg);}
}
.snippet-demo__donut-spinner {
  display: inline-block;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #7983ff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: snippet-demo__donut-spin 1.2s linear infinite;
}
</style>

#### Giải thích

Use a semi-transparent `border` for the whole element, except one side that will
serve as the loading indicator for the donut. Use `animation` to rotate the element.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ Requires prefixes for full support.</span>

* https://caniuse.com/#feat=css-animation
* https://caniuse.com/#feat=transforms2d

<!-- tags: animation -->
### Easing variables

Các biến được sử dụng lại cho thuộc tính transition-timing-function, rõ ràng khi tích hợp sẵn với ease, ease-in, ease-out and ease-in-out.

#### HTML

```html
<div class="easing-variables"></div>
```

#### CSS

```css
:root {
  --ease-in-quad: cubic-bezier(0.55, 0.085, 0.68, 0.53);
  --ease-in-cubic: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  --ease-in-quart: cubic-bezier(0.895, 0.03, 0.685, 0.22);
  --ease-in-quint: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035);
  --ease-in-circ: cubic-bezier(0.6, 0.04, 0.98, 0.335);

  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-out-cubic: cubic-bezier(0.215, 0.61, 0.355, 1);
  --ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
  --ease-out-quint: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-out-circ: cubic-bezier(0.075, 0.82, 0.165, 1);

  --ease-in-out-quad: cubic-bezier(0.455, 0.03, 0.515, 0.955);
  --ease-in-out-cubic: cubic-bezier(0.645, 0.045, 0.355, 1);
  --ease-in-out-quart: cubic-bezier(0.77, 0, 0.175, 1);
  --ease-in-out-quint: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-in-out-expo: cubic-bezier(1, 0, 0, 1);
  --ease-in-out-circ: cubic-bezier(0.785, 0.135, 0.15, 0.86);
}

.easing-variables {
  width: 50px;
  height: 50px;
  background: #333;
  transition: transform 1s var(--ease-out-quart);
}

.easing-variables:hover {
  transform: rotate(45deg);
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__easing-variables">Hover</div>
</div>

<style>
:root {
  --ease-in-quad: cubic-bezier(0.55, 0.085, 0.68, 0.53);
  --ease-in-cubic: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  --ease-in-quart: cubic-bezier(0.895, 0.03, 0.685, 0.22);
  --ease-in-quint: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035);
  --ease-in-circ: cubic-bezier(0.6, 0.04, 0.98, 0.335);

  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-out-cubic: cubic-bezier(0.215, 0.61, 0.355, 1);
  --ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
  --ease-out-quint: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-out-circ: cubic-bezier(0.075, 0.82, 0.165, 1);

  --ease-in-out-quad: cubic-bezier(0.455, 0.03, 0.515, 0.955);
  --ease-in-out-cubic: cubic-bezier(0.645, 0.045, 0.355, 1);
  --ease-in-out-quart: cubic-bezier(0.77, 0, 0.175, 1);
  --ease-in-out-quint: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-in-out-expo: cubic-bezier(1, 0, 0, 1);
  --ease-in-out-circ: cubic-bezier(0.785, 0.135, 0.15, 0.86);
}

.snippet-demo__easing-variables {
  width: 75px;
  height: 75px;
  background: #333;
  color: white;
  font-size: 0.8rem;
  font-weight: bold;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: transform 1s var(--ease-out-quart);
}

.snippet-demo__easing-variables:hover {
  transform: rotate(45deg);
}
</style>

#### Giải thích

The variables are defined globally within the `:root` CSS pseudo-class which matches the root element of a tree representing the document. In HTML, `:root` represents the `<html>` element and is identical to the selector `html`, except that its specificity is higher.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: animation -->
### Hover underline animation

Creates an animated underline effect when the text is hovered over.

<small>**Credit:** https://flatuicolors.com/</small>

#### HTML

```html
<p class="hover-underline-animation">Hover this text to see the effect!</p>
```

#### CSS

```css
.hover-underline-animation {
  display: inline-block;
  position: relative;
  color: #0087ca;
}
.hover-underline-animation::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #0087ca;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}
.hover-underline-animation:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__hover-underline-animation">Hover this text to see the effect!</p>
</div>

<style>
.snippet-demo__hover-underline-animation {
  display: inline-block;
  position: relative;
  color: #0087ca;
}
.snippet-demo__hover-underline-animation::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #0087ca;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}
.snippet-demo__hover-underline-animation:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
</style>

#### Giải thích

1. `display: inline-block` makes the block `p` an `inline-block` to prevent the underline from
   spanning the entire parent width rather than just the content (text).
2. thuộc tính `position: relative` để tạo khung tại phần tử này, giúp các phần tử giả có thể định vị được.
3.  `::after` để định nghĩa phần tử giả đó.
4. thuộc tính  `position: absolute` tách phần tử con ra khỏi sự phụ thuộc vào phần tử cha và thiết lập mối quan hệ về vị trí đối với phần tử cha.
5.  `width: 100%`  đảm bảo phần tử trải dài toàn bộ chiều rộng của thẻ cha.
6. `transform: scaleX(0)` initially scales the pseudo element to 0 so it has no width and is not visible.
7. `bottom: 0` and `left: 0` position it to the bottom left of the block.
8. `transition: transform 0.25s ease-out` means changes to `transform` will be transitioned over 0.25 seconds
   with an `ease-out` timing function.
9. `transform-origin: bottom right` means the transform anchor point is positioned at the bottom right of the block.
10. `:hover::after` then uses `scaleX(1)` to transition the width to 100%, then changes the `transform-origin`
    to `bottom left` so that the anchor point is reversed, allowing it transition out in the other direction when
    hovered off.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=transforms2d
* https://caniuse.com/#feat=css-transitions

<!-- tags: animation -->
### Disable selection

Makes the content unselectable.

#### HTML

```html
<p>You can select me.</p>
<p class="unselectable">You can't select me!</p>
```

#### CSS

```css
.unselectable {
  user-select: none;
}
```

#### Demo

<div class="snippet-demo">
  <p>You can select me.</p>
  <p class="snippet-demo__disable-selection">You can't select me!</p>
</div>

<style>
.snippet-demo__disable-selection {
  user-select: none;
}
</style>

#### Giải thích

`user-select: none` specifies that the text cannot be selected.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ Requires prefixes for full support.</span>
<span class="snippet__support-note">⚠️ This is not a secure method to prevent users from copying content.</span>

* https://caniuse.com/#feat=user-select-none

<!-- tags: interactivity -->
### Mouse cursor gradient tracking

A hover effect where the gradient follows the mouse cursor.

<small class="snippet__credit">**Credit:** [Tobias Reich](https://codepen.io/electerious/pen/MQrRxX)</small>

#### HTML

```html
<button class="mouse-cursor-gradient-tracking">
  <span>Hover me</span>
</button>
```

#### CSS

```css
.mouse-cursor-gradient-tracking {
  position: relative;
  background: #7983ff;
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  border: none;
  color: white;
  cursor: pointer;
  outline: none;
  overflow: hidden;
}

.mouse-cursor-gradient-tracking span {
  position: relative;
}

.mouse-cursor-gradient-tracking::before {
  --size: 0;
  content: '';
  position: absolute;
  left: var(--x);
  top: var(--y);
  width: var(--size);
  height: var(--size);
  background: radial-gradient(circle closest-side, pink, transparent);
  transform: translate(-50%, -50%);
  transition: width 0.2s ease, height 0.2s ease;
}

.mouse-cursor-gradient-tracking:hover::before {
  --size: 200px;
}
```

#### JavaScript

```js
var btn = document.querySelector('.mouse-cursor-gradient-tracking')
btn.onmousemove = function(e) {
  var x = e.pageX - btn.offsetLeft
  var y = e.pageY - btn.offsetTop
  btn.style.setProperty('--x', x + 'px')
  btn.style.setProperty('--y', y + 'px')
}
```

#### Demo

<div class="snippet-demo">
  <button class="snippet-demo__mouse-cursor-gradient-tracking">
    <span>Hover me</span>
  </button>
</div>

<style>
.snippet-demo__mouse-cursor-gradient-tracking {
  position: relative;
  background: #7983ff;
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  border: none;
  color: white;
  cursor: pointer;
  outline: none;
  overflow: hidden;
}

.snippet-demo__mouse-cursor-gradient-tracking span {
  position: relative;
}

.snippet-demo__mouse-cursor-gradient-tracking::before {
  --size: 0;
  content: '';
  position: absolute;
  left: var(--x);
  top: var(--y);
  width: var(--size);
  height: var(--size);
  background: radial-gradient(circle closest-side, aqua, rgba(0,255,255,0.0001));
  transform: translate(-50%, -50%);
  transition: width .2s ease, height .2s ease;
}

.snippet-demo__mouse-cursor-gradient-tracking:hover::before {
  --size: 200px;
}
</style>

<script>
(function () {
  var btn = document.querySelector('.snippet-demo__mouse-cursor-gradient-tracking')
  btn.onmousemove = function (e) {
    var x = e.pageX - btn.offsetLeft - btn.offsetParent.offsetLeft
    var y = e.pageY - btn.offsetTop - btn.offsetParent.offsetTop
    btn.style.setProperty('--x', x + 'px')
    btn.style.setProperty('--y', y + 'px')
  }
})()
</script>

#### Giải thích

_TODO_

**Note!**

If the element's parent has a positioning context (`position: relative`), you will need to subtract
its offsets as well.

```js
var x = e.pageX - btn.offsetLeft - btn.offsetParent.offsetLeft
var y = e.pageY - btn.offsetTop - btn.offsetParent.offsetTop
```

#### Hỗ trợ trình duyệt

<div class="snippet__requires-javascript">Requires JavaScript</div>
<span class="snippet__support-note">⚠️ Requires JavaScript.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: visual, interactivity -->
### Popout menu

Reveals an interactive popout menu on hover.

#### HTML

```html
<div class="reference">
  <div class="popout-menu">
    Popout menu
  </div>
</div>
```

#### CSS

```css
.reference {
  position: relative;
}
.popout-menu {
  position: absolute;
  visibility: hidden;
  left: 100%;
}
.reference:hover > .popout-menu {
  visibility: visible;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__reference">
    <div class="snippet-demo__popout-menu">
      Popout menu
    </div>
  </div>
</div>

<style>
.snippet-demo__reference {
  background: linear-gradient(135deg, #ff4c9f, #ff7b74);
  height: 75px;
  width: 75px;
  position: relative;
  will-change: transform;
}
.snippet-demo__popout-menu {
  position: absolute;
  visibility: hidden;
  left: 100%;
  background: #333;
  color: white;
  font-size: 0.9rem;
  padding: 0.4rem 0.8rem;
  width: 100px;
  text-align: center;
}
.snippet-demo__reference:hover > .snippet-demo__popout-menu {
  visibility: visible;
}
</style>

#### Giải thích

1. thuộc tính `position: relative` để tạo khung tại phần tử này, giúp các phần tử giả có thể định vị được.
2. thuộc tính  `position: absolute` tách phần tử con ra khỏi sự phụ thuộc vào phần tử cha và thiết lập mối quan hệ về vị trí đối với phần tử cha.
3. `left: 100%` moves the the popout menu 100% of its parent's width from the left.
4. `visibility: hidden` hides the popout menu initially and allows for transitions (unlike `display: none`).
5. `.reference:hover > .popout-menu` means that when `.reference` is hovered over, select immediate
   children with a class of `.popout-menu` and change their `visibility` to `visible`, which shows the popout.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: interactivity -->
### Sibling fade

Fades out the siblings of a hovered item.

#### HTML

```html
<div class="sibling-fade">
  <span>Item 1</span>
  <span>Item 2</span>
  <span>Item 3</span>
  <span>Item 4</span>
  <span>Item 5</span>
  <span>Item 6</span>
</div>
```

#### CSS

```css
span {
  padding: 0 1rem;
  transition: opacity 0.2s;
}

.sibling-fade:hover span:not(:hover) {
  opacity: 0.5;
}
```

#### Demo

<div class="snippet-demo">
  <nav class="snippet-demo__sibling-fade">
    <span>Item 1</span>
    <span>Item 2</span>
    <span>Item 3</span>
    <span>Item 4</span>
    <span>Item 5</span>
    <span>Item 6</span>
  </nav>
</div>

<style>
.snippet-demo__sibling-fade {
  cursor: default;
  line-height: 2;
  vertical-align: middle;
}

.snippet-demo__sibling-fade span {
  padding: 1rem;
  transition: opacity 0.2s;
}

.snippet-demo__sibling-fade:hover span:not(:hover) {
  opacity: 0.5;
}
</style>

#### Giải thích

1. `transition: opacity 0.2s` specifies that changes to opacity will be transitioned over 0.2 seconds.
2. `.sibling-fade:hover span:not(:hover)` specifies that when the parent is hovered, select any `span` children
   that are not currently being hovered and change their opacity to `0.5`.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-sel3
* https://caniuse.com/#feat=css-transitions

<!-- tags: interactivity -->
### Custom variables

CSS variables that contain specific values to be reused throughout a document.

#### HTML

```html
<p class="custom-variables">CSS is awesome!</p>
```

#### CSS

```css
:root {
  --some-color: #da7800;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray, 0 0 0.2em slategray;
}

.custom-variables {
  color: var(--some-color);
  font-size: var(--some-size);
  font-style: var(--some-keyword);
  text-shadow: var(--some-complex-value);
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__custom-variables">
    <p>CSS is awesome!</p>
  </div>
</div>

<style>
.snippet-demo__custom-variables {
  --some-color: #686868;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray , 0 0 0.2em slategray;
}

.snippet-demo__custom-variables p {
  color: var(--some-color);
  font-size: var(--some-size);
  font-style: var(--some-keyword);
  text-shadow: var(--some-complex-value);
}
</style>

#### Giải thích

The variables are defined globally within the `:root` CSS pseudo-class which matches the root element of a tree representing the document. Variables can also be scoped to a selector if defined within the block.

Declare a variable with `--variable-name:`.

Reuse variables throughout the document using the `var(--variable-name)` function.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: other -->

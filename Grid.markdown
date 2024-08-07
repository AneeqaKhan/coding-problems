## Problem
Display a grid like the below screenshot using HTML/CSS
<img width="541" alt="Screenshot 2024-08-07 at 11 55 18 PM" src="https://github.com/user-attachments/assets/88dfe6e0-e2a8-4651-bcd1-a3ff085d8608">

## Solution

### index.html
```javascript
<!DOCTYPE html>
<html>
  <head>
    <title>Grid Boxes Layout</title>
    <link rel="stylesheet" href="styles.css" />
  </head>

  <body>
    <div class="my-50 mx-auto">
      <div class="container">
        <div class="layout">
          <div class="box" data-title="1"></div>
          <div class="box" data-title="2"></div>
          <div class="box" data-title="3"></div>
          <div class="box" data-title="4"></div>
          <div class="box" data-title="5"></div>
          <div class="box" data-title="6"></div>
          <div class="box" data-title="7"></div>
          <div class="box" data-title="8"></div>
          <div class="box" data-title="9"></div>
          <div class="box" data-title="10"></div>
          <div class="box" data-title="11"></div>
          <div class="box" data-title="12"></div>
        </div>
        <div class="template">
          <div class="box" data-title="1"></div>
          <div class="box" data-title="2"></div>
          <div class="box" data-title="3"></div>
          <div class="box" data-title="4"></div>
          <div class="box" data-title="5"></div>
          <div class="box" data-title="6"></div>
          <div class="box" data-title="7"></div>
          <div class="box" data-title="8"></div>
          <div class="box" data-title="9"></div>
          <div class="box" data-title="10"></div>
          <div class="box" data-title="11"></div>
          <div class="box" data-title="12"></div>
        </div>
      </div>
    </div>
  </body>
</html>
```
### styles.css
```javascript
.layout {
  display: grid;
  grid-template-columns: repeat(4, 100px);
  grid-template-rows: repeat(3, 100px);
  gap: 10px 30px;
  justify-content: center;
  grid-auto-flow: column;
  padding-top: 40px;
}

.box:nth-child(1) {
  order: 3;
}
.box:nth-child(2) {
  order: 4;
}
.box:nth-child(3) {
  order: 5;
}

.box {
  background-color: #94cef5;
  border: 1px solid #4ea4e0;
  border-radius: 10px;
  box-sizing: border-box;
  min-height: 35px;
  min-width: 40px;
  position: relative;
}

.box:nth-child(odd) {
  background-color: #c5e6fc;
  border: 1px solid #92caf1;
}

.layout .box {
  opacity: 0.8;
}

.template .box {
  background-color: initial;
  border: 1px solid gray;
}

.container {
  height: 500px;
}

.layout,
.template {
  height: 400px;
  width: 550px;
  border: 1px solid #94cef5;
  border-radius: 5px;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
}

.layout {
  z-index: 1;
}

.template .box {
  position: absolute;
}

.box:before {
  content: attr(data-title);
  position: absolute;
  top: 0;
  bottom: 0;
  display: flex;
  left: 0;
  right: 0;
  justify-content: center;
  align-items: center;
}

.template [data-title] {
  width: 100px;
  height: 100px;
}

.template [data-title="1"] {
  top: 40px;
  left: 420px;
}

.template [data-title="2"] {
  top: 150px;
  left: 420px;
}

.template [data-title="3"] {
  top: 260px;
  left: 420px;
}

.template [data-title="4"] {
  top: 40px;
  left: 30px;
}

.template [data-title="5"] {
  top: 150px;
  left: 30px;
}

.template [data-title="6"] {
  top: 260px;
  left: 30px;
}

.template [data-title="7"] {
  top: 40px;
  left: 160px;
}

.template [data-title="8"] {
  top: 150px;
  left: 160px;
}

.template [data-title="9"] {
  top: 260px;
  left: 160px;
}

.template [data-title="10"] {
  top: 40px;
  left: 290px;
}

.template [data-title="11"] {
  top: 150px;
  left: 290px;
}

.template [data-title="12"] {
  top: 260px;
  left: 290px;
}
```



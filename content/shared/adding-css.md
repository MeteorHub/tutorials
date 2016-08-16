{{#template name="addingCSS"}}

### Adding CSS

在我们继续之前，让我们通过添加css使我们的app看起来比较好看。
虽然这个教程专注于html和javascript，所以仅仅复制下面的css到`main.css`当中。这是本教程需要的所有CSS代码。没有CSS，APP依然可以正常工作，不过如果你添加了它会看起来更好一些。

{{#codeBox cssHeading cssFileName}}
```css
/* CSS declarations go here */
body {
  font-family: sans-serif;
  background-color: #315481;
  background-image: linear-gradient(to bottom, #315481, #918e82 100%);
  background-attachment: fixed;

  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;

  padding: 0;
  margin: 0;

  font-size: 14px;
}

.container {
  max-width: 600px;
  margin: 0 auto;
  min-height: 100%;
  background: white;
}

header {
  background: #d2edf4;
  background-image: linear-gradient(to bottom, #d0edf5, #e1e5f0 100%);
  padding: 20px 15px 15px 15px;
  position: relative;
}

#login-buttons {
  display: block;
}

h1 {
  font-size: 1.5em;
  margin: 0;
  margin-bottom: 10px;
  display: inline-block;
  margin-right: 1em;
}

form {
  margin-top: 10px;
  margin-bottom: -10px;
  position: relative;
}

.new-task input {
  box-sizing: border-box;
  padding: 10px 0;
  background: transparent;
  border: none;
  width: 100%;
  padding-right: 80px;
  font-size: 1em;
}

.new-task input:focus{
  outline: 0;
}

ul {
  margin: 0;
  padding: 0;
  background: white;
}

.delete {
  float: right;
  font-weight: bold;
  background: none;
  font-size: 1em;
  border: none;
  position: relative;
}

li {
  position: relative;
  list-style: none;
  padding: 15px;
  border-bottom: #eee solid 1px;
}

li .text {
  margin-left: 10px;
}

li.checked {
  color: #888;
}

li.checked .text {
  text-decoration: line-through;
}

li.private {
  background: #eee;
  border-color: #ddd;
}

header .hide-completed {
  float: right;
}

.toggle-private {
  margin-left: 5px;
}

@media (max-width: 600px) {
  li {
    padding: 12px 15px;
  }

  .search {
    width: 150px;
    clear: both;
  }

  .new-task input {
    padding-bottom: 5px;
  }
}
```
{{/codeBox}}

{{/template}}

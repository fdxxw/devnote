####js下载文件
```javascript
const saveData = (function () {
    const a = document.createElement("a");
    document.body.appendChild(a);
    a.style = "display: none";
    return function (url, fileName) {
        a.href = url;
        a.download = fileName;
        a.click();
    };
}());
```
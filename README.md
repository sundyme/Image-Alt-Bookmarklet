# 图片收藏及alt信息书签工具 (Image-Alt-Bookmarklet)

图片收藏及alt信息书签工具是一个简单的浏览器书签工具，允许用户在点击网页上的图片时，将图片的URL和alt信息复制到剪贴板。
此书签工具由GPT4完成，目的是为了方便的收集Midjourney官方社区的图片和对应的提示词。

## 功能

- 点击该书签进入点击监听模式
- 点击网页上的图片
- 复制图片的URL和alt信息到剪贴板
- 显示提示信息，确认已复制到剪贴板

## 如何安装

1. 打开你的浏览器，新建一个书签。
2. 将书签命名为“收藏图片及alt信息”（或任何你喜欢的名字），URL或地址栏留空，然后保存书签。
3. 打开书签管理器（通常可以通过浏览器的书签菜单找到）。
4. 在书签管理器中找到刚刚创建的书签，然后编辑它。
5. 将以下代码复制并粘贴到书签的URL或地址栏中：

```javascript
javascript:(function() {
    document.addEventListener('click', function(event) {
        var target = event.target;
        if (target.tagName.toLowerCase() === 'img') {
            event.preventDefault();
            var imageUrl = target.src;
            var altText = target.alt;
            var clipboardText = "图片链接：" + imageUrl + "\\n图片alt信息：" + altText;
            var textArea = document.createElement('textarea');
            textArea.value = clipboardText;
            textArea.style.position = 'fixed';
            textArea.style.top = '-1000px';
            document.body.appendChild(textArea);
            textArea.focus();
            textArea.select();
            document.execCommand('copy');
            document.body.removeChild(textArea);
            alert("图片链接和alt信息已复制到剪贴板！");
        }
    }, false);
})();
```

6. 保存更改后的书签。

## 使用方法

1. 访问一个包含图片的网页。
2. 点击保存的书签工具。
3. 在网页上点击任意图片，图片的URL和alt信息将自动复制到剪贴板。

## 贡献

欢迎为本项目提出改进意见和建议，请通过 [Issues](https://github.com/yourusername/your-repo-name/issues) 提交问题和建议。

## 许可证

本项目采用 [MIT License](LICENSE) 授权。
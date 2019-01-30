# 前端代码规范

前端代码规范文档，在这个地方我们整理了一些在实际开发中非常有意义的约定，在保持团队代码一致性方面有积极意义。

## 起步

安装依赖:
**Note:**
请确保你的`node`版本不要高于`8.15.0`
```node <=8.15.0```

``` bash
$ git clone https://github.com/f3f/guide.git
$ cd guide
$ npm install
```

## 开发

```bash
$ npm run serve
```

## 部署

本项目采用TrvaisCI来实现自动化部署，因此你如果需要修改文档内容只需要`push`修改后的内容到`master`分支即可。

## 手动部署

手动部署请使用 `npm run build` 命令，拷贝`public` 文件夹下的所有文件,复制到服务器目录。
当然，如果你要在build之前请确认 `_config.yml` 的配置和你部署的服务器一致，特别是以下两个选项：

```
url: https://f3f.github.io
root: /guide/
```
## Powered By

本文档由[HEXO](https://hexo.io/zh-cn/)驱动

## License

[CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)

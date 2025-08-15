### popmenu 社区自定义浮窗

操作步骤如下:

1. fork 本仓库.
2. 修改`data.json` 添加你的浮窗信息.
3. 在`html`目录下新增 html 文件,尽量单文件,不要有外部文件依赖.注意 html 文件名必须和第一步`data.json`里的`name`属性一致.
4. 提交代码,并提交 merge 请求,待审核通过之后,可以在程序的`社区`菜单中看见.

### 说明

程序中可以使用参数,最好不要超过 4 个参数.嵌入的参数是通过`url query`的方式传入的,所以可以使用`const params = new URLSearchParams(window.location.search);`这样来获取参数.

最好加上默认值,这样不管是不是在 popmenu 里打开,都可以正常显示.

### 参数解释

| 参数         | 说明                                                                            |
| ------------ | ------------------------------------------------------------------------------- |
| name         | 浮窗名称(注意`html`文件名也必须是这个)                                          |
| desc         | 浮窗说明,会显示在 popmenu`社区`列表里,最好不超过 50 个汉字                      |
| author       | 浮窗作者                                                                        |
| size         | 浮窗大小,这里设置默认的,可以手动拖拽放大或者缩小,所以要求你的 html 文件能自适应 |
| size.width   | 宽度                                                                            |
| size.height  | 高度                                                                            |
| params       | 自定义参数,JSON Object 对象                                                     |
| params.key   | 参数名称                                                                        |
| params.value | JSON Object 对象,包含`default`:默认值,`desc`:参数描述                           |

示例:

```json
{
  "name": "一言",
  "desc": "一言 - 触动心灵的句子",
  "author": "JerryWang",
  "size": {
    "width": 500,
    "height": 500
  },
  "params": {
    "category": {
      "default": "c",
      "desc": "句子类型"
    },
    "min_length": {
      "default": 0,
      "desc": "返回句子的最小长度（包含）"
    },
    "max_length": {
      "default": 30,
      "desc": "返回句子的最大长度（包含）"
    },
    "interval": {
      "default": 60,
      "desc": "刷新的间隔,单位秒"
    }
  }
}
```

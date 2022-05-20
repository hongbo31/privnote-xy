# privnote-xy
搭建privnote-个人版


privote



一期需求：

用户打开页面， 出现文本输入框， 输入文本，点击创建

创建后生成唯一的一次性链接

用户点击链接可以看到文本的内容，同时链接失效

打开链接后用户可以拷贝链接内容， 快速回复内容， 点击快速回复时， 带入原有文案内容。



技术方案：

写数据

用户 —> write —> 传给后端 —>「ID，timestamp, context, is_read=0， 链接」 写入db

读数据

用户 —> read  —> 请求后端 —> 根据链接去匹配， 检查read状态， 返回context内容， 翻转read状态 —>返回给前端


Db设计

id、timestamp、create_type、 context 、 unique_link、 is_read



接口设计:

create/
Req:
create_type: int
Context: str
Resp:
unique_link: str

Read/
Req:
unique_link: str
Resp:
take_times: date time
Context: str


后端设计：

要实现哪些功能？
框架需要提供哪些基础能力？
需要哪些技术？
实现这些功能需要哪些库、 如何选型？ 
项目的目录结构应该是怎么样的

先出一个demo
再抽象你的实现，实现封装、配置化
如何接收前端传过来的数据， 拿到数据要怎么处理， 选用那种数据结构，怎么保存数据？

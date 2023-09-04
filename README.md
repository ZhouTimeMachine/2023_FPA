# 浙江大学 2023 秋冬程序设计与算法基础
本仓库为浙江大学 2023 秋冬《程序设计与算法基础》课程仓库，目前暂定主要面向 2023 级图灵班翁恺老师教学班，也欢迎其他同学批评指正。

本人是第一次使用 mkdocs 搭建课程指导网站，参考了 [Guahao](https://github.com/Guahao31/2023_DD)、[zjuerDFL](https://github.com/zjuerDFL/2023_EBD/tree/main) 和 [CTF 短学期课程仓库](https://github.com/team-s2/summer_course_2023)。

可以查看[在线文档](https://zhoutimemachine.github.io/2023_FPA/)，或者如果希望本地部署，可以首先安装 mkdocs 支持
```
pip install mkdocs
pip install mkdocs-material
```

打开实时渲染服务（默认端口 8000）
```
mkdocs serve
```

如果顺利的话，在浏览器中输入 `127.0.0.1:8000` 就可以本地预览了。但是如果 8000 端口被占用，可能需要指定一个新的端口，以 8001 为例：
```
mkdocs serve -a 127.0.0.1:8001
```

此时就需要使用 `127.0.0.1:8001` 进行本地预览了。

本仓库实时更新，因此如果使用本地预览，可以时不时 `git pull` 以获取最新版本。
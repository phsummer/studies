requirements.txt 语法备忘
===

- 参考：[Python requirements.txt 语法 - ChnMig - 博客园](https://www.cnblogs.com/chnmig/p/12107199.html)
- 标准文档：[PEP 508 – Dependency specification for Python Software Packages | peps.python.org](https://peps.python.org/pep-0508/#environment-markers)


## 示例
```shell
# requirements.txt
ipywidgets
loky>=3.0.0
jaxlib; sys_platform != 'win32'
pywinpty==1.1.6; python_version < '3.7' and sys_platform == 'win32'
```
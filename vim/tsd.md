1. 使用vscode进行nodejs的开发和调试
vscode使用DefinitelyTyped进行自动完成所以需要先安装tsd，命令：
``
npm install -g tsd
``
安装完成后，首先安装node基本语法支持
``
tsd query node --action install
``
然后根据使用的modules安装，相应的支持，例如express的
``
tsd query express --action install
``
具体的包可以到这里查询：http://definitelytyped.org/tsd/

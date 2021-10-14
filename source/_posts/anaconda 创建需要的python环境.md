## anaconda 创建需要的python环境

1. **打开anaconda的prompt，即终端**

   ```
   conda create --name "环境的名字" python=="版本号"
   #例如创建名为tf，python版本为3.6的python环境
   conda create --name tf python==3.6
   ```

   创建过程中会要求你输入y，接下来就会自动下载对应的python环境，下载好后会让你激活并进入创建的环境。使用activate 环境名字。例如这里的activate tf。进入后你会看到命令的最左边的小括号里就是你创建的环境的名字。

2. **进入后检测当前的python版本，输入python回车，就能看到你创建的python环境是否是你上一步中安装的环境。**

3. **退出创建的环境**

   ```
   conda deactivate
   ```

4. **查看当前anaconda的环境**

   ```
   conda info --evn
   ```

   这个命令可以让你看到在anaconda下的环境名字

5. **更换源为国内源**（为了提高下载速度）

     临时使用国内源下载包或库，在安装的命令后面加上-i url（即源的地址）

     ```
     pip install jieba -i https://pypi.tuna.tsinghua.edu.cn/simple
     ```
     
6.  **一些pip命令**

    更新pip指令

    ```
    python -m pip install --upgrade pip
    ```

    查看pip下安装的库列表

    ```
    pip list
    ```

    安装某个包

    ```
    pip install 包名
    ```

    

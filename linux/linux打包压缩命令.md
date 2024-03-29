<img width="717" alt="截屏2024-03-29 22 16 45" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/56625728-e811-4848-a736-d5c9a73974ca">
tar 命令在 Linux 中用于文件的打包和备份。它可以将多个文件或目录组合成一个档案文件，通常用于备份或将文件从一个地方传输到另一个地方。这个命令还可以与压缩命令结合使用，比如 gzip 或 bzip2，来减少档案文件的大小。

这里是一些常用的 tar 命令选项：    

-c：创建一个新的档案文件。    
-x：从档案文件中提取文件。    
-z：通过 gzip 来压缩或解压文件。    
-j：通过 bzip2 来压缩或解压文件。    
-v：在处理文件时显示详细信息。    
-f：指定档案文件的名称。    
-t：列出档案内容。    
-r：向档案文件追加文件。    
-u：仅更新已改变的文件到现有的档案文件。    
以下是一些 tar 命令的使用示例：      

创建档案文件：     

```code
tar -cvf archive.tar file1 file2 dir1
```

这个命令将 file1、file2 以及 dir1 目录（包括它的内容）打包成一个名为 archive.tar 的档案文件，并且显示详细信息。       

提取档案文件：        

```code
tar -xvf archive.tar
```
这个命令将 archive.tar 档案文件中的内容提取出来，并显示详细信息。         

查看档案内容：      

```code
tar -tvf archive.tar
```

这个命令将列出 archive.tar 文件中的所有文件和目录。       
  
创建经过 gzip 压缩的档案文件：      

```code
tar -czvf archive.tar.gz file1 file2 dir1
```

这个命令将 file1、file2 和 dir1 打包成一个经过 gzip 压缩的档案文件 archive.tar.gz。     

提取经过 gzip 压缩的档案文件：      

```code
tar -xzvf archive.tar.gz
```

这个命令将 archive.tar.gz 文件解压并提取。     

向档案文件追加文件：     

```code
tar -rvf archive.tar newfile
```
这个命令将 newfile 文件追加到现有的 archive.tar 档案文件中。      

更新档案中的文件：     
  
```code
tar -uvf archive.tar file1
```

如果 file1 自档案文件创建或上次更新以来已经改变了，这个命令将更新 archive.tar 中的 file1 文件。       

记住，在使用 tar 命令时，选项的顺序很重要。-f 选项通常是最后一个选项，后面紧跟档案文件的名字。对于实际使用的情况，建议参考命令的手册页 man tar，以获得最准确和详细的信息。          

好难理解啊为什么每一个都要加v啊      

-v 选项在 tar 命令中代表“verbose”（详细），它的作用是让命令在执行的时候显示更多的信息。这个选项并不是必需的，只是为了能让用户看到更多的执行过程信息。       

在没有 -v 的情况下，tar 命令会在没有任何输出的情况下执行，这意味着你不会知道命令是否正在正常工作，也看不到正在被打包或解包的文件列表。这在脚本或自动化任务中可能是理想的，因为输出可以保持干净，不会被日志信息所淹没。       

但是，对于命令行的实际使用，大多数人会倾向于使用 -v 选项，因为它提供了一种反馈形式来确认命令正在按照预期执行。这对于调试或仅仅验证过程非常有用。      

例如：      

创建档案时，-v 会显示哪些文件被添加到了档案中。       
提取档案时，-v 会显示哪些文件被提取了。                 
列出档案内容时，-v 通常不必要，因为 -t 选项本身就会列出内容。         
如果你不需要这些额外信息，可以安全地省略 -v 选项。以下是不使用 -v 选项的命令示例：         

创建档案文件：          
```code
tar -cf archive.tar file1 file2 dir1
```
提取档案文件：        
```code
tar -xf archive.tar
````
创建经过 gzip 压缩的档案文件：    

```code
tar -czf archive.tar.gz file1 file2 dir1
```
提取经过 gzip 压缩的档案文件：    
```code
tar -xzf archive.tar.gz
````

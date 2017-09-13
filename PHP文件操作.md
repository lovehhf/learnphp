#### PHP操作文件
> PHP 拥有的多种函数可供创建、读取、上传以及编辑文件。

##### fopen()
> fopen() 的第一个参数包含被打开的文件名，第二个参数规定打开文件的模式。

fopen打开模式:

* r	打开文件为只读。文件指针在文件的开头开始。
* w	打开文件为只写。删除文件的内容或创建一个新的文件，如果它不存在。文件指针在文件的开头开始。
* a	打开文件为只写。文件中的现有数据会被保留。文件指针在文件结尾开始。创建新的文件，如果文件不存在。
* x	创建新文件为只写。返回 FALSE 和错误，如果文件已存在。
* r+	打开文件为读/写、文件指针在文件开头开始。
* w+	打开文件为读/写。删除文件内容或创建新文件，如果它不存在。文件指针在文件开头开始。
* a+	打开文件为读/写。文件中已有的数据会被保留。文件指针在文件结尾开始。创建新文件，如果它不存在。
* x+	创建新文件为读/写。返回 FALSE 和错误，如果文件已存在。

fopen() 函数也用于创建文件。文件被打开为写入(w)或增加(a),则会创建一个新文件。


##### fread()
> fread() 函数读取打开的文件。

fread() 的第一个参数包含待读取文件的文件名，第二个参数规定待读取的最大字节数。

##### fclose()

> fclose() 函数用于关闭打开的文件。

注释：用完文件后把它们全部关闭是一个良好的编程习惯。您并不想打开的文件占用您的服务器资源。

fclose() 需要待关闭文件的名称（或者存有文件名的变量）：

示例:
```
<?php
$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
echo fread($myfile,filesize("webdictionary.txt"));
fclose($myfile);
?>
```

##### fgets()
> fgets() 函数用于从文件读取单行。 调用 fgets() 函数之后，文件指针会移动到下一行。

##### feof()
> feof() 函数检查是否已到达 "end-of-file" (EOF)。feof() 对于遍历未知长度的数据很有用。

#####  fgetc()
> fgetc() 函数用于从文件中读取单个字符。

下例逐字符读取 "webdictionary.txt" 文件，直到 end-of-file：
```
<?php
$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
// 输出单字符直到 end-of-file
while(!feof($myfile)) {
  echo fgetc($myfile);
}
fclose($myfile);
?>
```

##### fwrite()
> fwrite() 函数用于写入文件。第一个参数包含要写入的文件的文件名，第二个参数是被写的字符串。
# 查看logging文件

[How to View & Read Linux Log Files](https://phoenixnap.com/kb/how-to-view-read-linux-log-files)


### 使用`grep`查找关键词

在`scrapy_log_03_26.txt`文件中查找包含`ERROR: Error downloading` 的行：
>
`$ grep 'ERROR: Error downloading' /Users/kevin/scrapy_log_03_26.txt`
>
```
ERROR: Error downloading <GET https://movie.douban.com/celebrity/1031909/>
ERROR: Error downloading <GET https://movie.douban.com/celebrity/1032113/>
ERROR: Error downloading <GET https://movie.douban.com/celebrity/1098631/>
```
### tail
tail – Output the last few lines of files

### more

### cat
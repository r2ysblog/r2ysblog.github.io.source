
// 基本状况
# free -h

// 应用程序物理内存消耗
# ps -eo rss | awk 'BEGIN{sum=0}{sum=sum+$1}END{print sum}'

// 应用程序状况
# top -b -n 1

# cat /proc/meminfo


## 清理buffer cache
$ sync
# 将内存中数据强制先刷新到磁盘中

清理Buffer缓存区域
$ echo 1 > /proc/sys/vm/drop_caches  # 表示清除pagecache。
$ echo 2 > /proc/sys/vm/drop_caches  # 表示清除回收slab分配器中的对象（包括目录项缓存和inode缓存）。slab分配器是内核中管理内存的一种机制，其中很多缓存数据实现都是用的pagecache。
$ echo 3 > /proc/sys/vm/drop_caches  # 表示清除pagecache和slab分配器中的缓存对象
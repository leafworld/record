# 虚拟机3节点swift测试结果

## xfs性能测试

### 1.不同磁盘运行结果
![image](https://github.com/leafworld/record/blob/master/pictures/xfs_fio_disk_bandwidth.png)

![image](https://github.com/leafworld/record/blob/master/pictures/xfs_fio_disk_iops.png)

问题：
/dev/sdb,/dev/sdc性能会降低

### 2.文件大小和seq/rand
![image](https://github.com/leafworld/record/blob/master/pictures/xfs_fio_size_bandwidth.png)

![image](https://github.com/leafworld/record/blob/master/pictures/xfs_fio_iops_bandwidth.png)

结论：
- 在256kb一下增长趋势更大
- 随机和顺序存取影响很大

## swift性能测试
### 1.对象大小
![image](https://github.com/leafworld/record/blob/master/pictures/swift_cosbench_stage_bandwidth.png)

![image](https://github.com/leafworld/record/blob/master/pictures/swift_cosbench_avg_bandwidth.png)

![image](https://github.com/leafworld/record/blob/master/pictures/swift_cosbench_avg_throughput.png)

结论1：在256kb,512kb,1m带宽变化不明显，而对<256kb对象大小影响较大

结论2：这3个数值带宽变化不大的情况下，选择256为分界能获得相对较高的吞吐

![image](https://github.com/leafworld/record/blob/master/pictures/swift_cosbench_size_RT.png)

结论3：在超过1m后响应时间略长

### 2.每container中对象数目影响
![image](https://github.com/leafworld/record/blob/master/pictures/swift_cosbench_onum_bandwidth.png)

![image](https://github.com/leafworld/record/blob/master/pictures/swift_cosbench_onum_throughput.png)

结论：目前由于对象数目较少，变化不大

正在进行下一步的测试

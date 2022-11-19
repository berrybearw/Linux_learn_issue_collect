# Linux_learn_issue_collect
Linux 基本資訊收集

Client ip : 

bash SSH_CLIENT , ksh `who am i|awk '{ print $5}'`

CPU : 

```bash
cpu_n=`cat /proc/cpuinfo |grep "processor"|wc -l`
wa=`echo "scale=5; 1/$cpu_n" |bc`
wa2=`echo "$wa*100" |bc`
echo "CPU數量:" `lscpu |grep '^CPU(s):' |sed 's/^[ \t]*//g'|cut -d: -f 2`
echo "CPU型號:" `lscpu |grep '^Model name:' |sed 's/^[ \t]*//g'|cut -d: -f 2`
echo "CPU MHz:" `lscpu |grep '^CPU MHz:' |sed 's/^[ \t]*//g'|cut -d: -f 2` 
echo "wa上限 :" $wa2"%"
```

OS 版本 : `cat /etc/redhat-release`

硬碟 :

```bash
cat /proc/scsi/scsi |grep -E 'Vendor|Type' |sed 's/^[ \t]*//g'

echo -e "\n##### 9. 0為 SSD, 1為 HDD ##### \n"
lsblk -d -o name,rota
```

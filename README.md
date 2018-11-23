# DNS Performance Test

Shell script to test the performance of the most popular DNS resolvers from your location.

Includes by default:
 * AzureInternal 168.63.129.16
 * Umbrella 208.67.222.222
 * CloudFlare 1.1.1.1
 * Level3 4.2.2.1
 * Google 8.8.8.8
 * Quad9 9.9.9.9
 * Freenom 80.80.80.80
 * OpenDNS 208.67.222.123
 * Norton 199.85.126.20
 * CleanBrowsing 185.228.168.168
 * Dyn 216.146.35.35

# Required 

You need to install bc and dig. For Ubuntu:

```
 $ sudo apt-get install bc dnsutils
```

# Utilization

``` 
 $ git clone --depth=1 https://github.com/cleanbrowsing/dnsperftest/
 $ cd dnsperftest
 $ bash ./dnstest.sh 
                  baidu.com   qq.com      taobao.com  tmall.com   sohu.com    jd.com      sina.com.cn weibo.com   360.cn      csdn.net    alipay.com  Average     
10.126.144.4      1 ms        1 ms        1 ms        1 ms        5 ms        84 ms       34 ms       38 ms       1 ms        1 ms        1 ms              15.27
10.126.144.5      3 ms        4 ms        2 ms        1 ms        3 ms        96 ms       6 ms        5 ms        1 ms        1 ms        4 ms              11.45
AzureInternal     1 ms        1 ms        1 ms        1 ms        5 ms        2 ms        1 ms        5 ms        2 ms        1 ms        1 ms              1.90
umbrella1         80 ms       80 ms       190 ms      189 ms      80 ms       80 ms       240 ms      81 ms       259 ms      165 ms      82 ms             138.72
cloudflare        178 ms      198 ms      162 ms      165 ms      164 ms      383 ms      164 ms      163 ms      178 ms      164 ms      179 ms            190.72
level3            255 ms      307 ms      212 ms      228 ms      259 ms      473 ms      570 ms      200 ms      223 ms      512 ms      350 ms            326.27
google            62 ms       117 ms      200 ms      203 ms      190 ms      121 ms      85 ms       177 ms      115 ms      107 ms      66 ms             131.18
quad9             111 ms      117 ms      107 ms      197 ms      110 ms      203 ms      290 ms      110 ms      281 ms      295 ms      292 ms            192.09
freenom           82 ms       56 ms       60 ms       208 ms      94 ms       181 ms      77 ms       50 ms       93 ms       90 ms       53 ms             94.90
opendns           5152 ms     144 ms      5142 ms     153 ms      148 ms      5357 ms     237 ms      136 ms      136 ms      252 ms      257 ms            1555.81
norton            10 ms       4 ms        4 ms        3 ms        4 ms        4 ms        4 ms        4 ms        5 ms        3 ms        4 ms              4.45
cleanbrowsing     82 ms       83 ms       82 ms       88 ms       84 ms       196 ms      192 ms      192 ms      83 ms       82 ms       82 ms             113.27
dyn               82 ms       80 ms       86 ms       80 ms       84 ms       215 ms      203 ms      206 ms      88 ms       86 ms       85 ms             117.72
```

To sort with the fastest first, add `sort -k 22 -n` at the end of the command:

```
  $ bash ./dnstest.sh |sort -k 22 -n
                  baidu.com   qq.com      taobao.com  tmall.com   sohu.com    jd.com      sina.com.cn weibo.com   360.cn      csdn.net    alipay.com  Average     
AzureInternal     1 ms        1 ms        1 ms        1 ms        5 ms        2 ms        1 ms        5 ms        2 ms        1 ms        1 ms              1.90
norton            10 ms       4 ms        4 ms        3 ms        4 ms        4 ms        4 ms        4 ms        5 ms        3 ms        4 ms              4.45
freenom           82 ms       56 ms       60 ms       208 ms      94 ms       181 ms      77 ms       50 ms       93 ms       90 ms       53 ms             94.90
cleanbrowsing     82 ms       83 ms       82 ms       88 ms       84 ms       196 ms      192 ms      192 ms      83 ms       82 ms       82 ms             113.27
dyn               82 ms       80 ms       86 ms       80 ms       84 ms       215 ms      203 ms      206 ms      88 ms       86 ms       85 ms             117.72
google            62 ms       117 ms      200 ms      203 ms      190 ms      121 ms      85 ms       177 ms      115 ms      107 ms      66 ms             131.18
umbrella1         80 ms       80 ms       190 ms      189 ms      80 ms       80 ms       240 ms      81 ms       259 ms      165 ms      82 ms             138.72
cloudflare        178 ms      198 ms      162 ms      165 ms      164 ms      383 ms      164 ms      163 ms      178 ms      164 ms      179 ms            190.72
quad9             111 ms      117 ms      107 ms      197 ms      110 ms      203 ms      290 ms      110 ms      281 ms      295 ms      292 ms            192.09
level3            255 ms      307 ms      212 ms      228 ms      259 ms      473 ms      570 ms      200 ms      223 ms      512 ms      350 ms            326.27
opendns           5152 ms     144 ms      5142 ms     153 ms      148 ms      5357 ms     237 ms      136 ms      136 ms      252 ms      257 ms            1555.81
```

# For Windows users using the Linux subsystem

If you receive an error `$'\r': command not found`, convert the file to a Linux-compatible line endings using:

    tr -d '\15\32' < dnstest.sh > dnstest-2.sh
    
Then run `bash ./dnstest-2.sh`

# jarvisoj.com -- CRYPTO -- Extremely hard RSA

## Challenge

```
没想到RSA4096都被你给破了，一定是我的问题，给了你太多信息，这次我只给你一个flag的加密值和公钥，仍然是RSA4096，我就不信你还能解出来。


extremelyhardRSA.rar.8782e822c895a2af3d8ba4ffbb3e280b
```

## Solution

压缩包里包含一份加密文件和公钥文件。

用openssl看下公钥信息

```shell
$ openssl rsa -in ./pubkey.pem -pubin -text
Public-Key: (4096 bit)
Modulus:
    00:b0:be:e5:e3:e9:e5:a7:e8:d0:0b:49:33:55:c6:
    18:fc:8c:7d:7d:03:b8:2e:40:99:51:c1:82:f3:98:
    de:e3:10:45:80:e7:ba:70:d3:83:ae:53:11:47:56:
    56:e8:a9:64:d3:80:cb:15:7f:48:c9:51:ad:fa:65:
    db:0b:12:2c:a4:0e:42:fa:70:91:89:b7:19:a4:f0:
    d7:46:e2:f6:06:9b:af:11:ce:bd:65:0f:14:b9:3c:
    97:73:52:fd:13:b1:ee:a6:d6:e1:da:77:55:02:ab:
    ff:89:d3:a8:b3:61:5f:d0:db:49:b8:8a:97:6b:c2:
    05:68:48:92:84:e1:81:f6:f1:1e:27:08:91:c8:ef:
    80:01:7b:ad:23:8e:36:30:39:a4:58:47:0f:17:49:
    10:1b:c2:99:49:d3:a4:f4:03:8d:46:39:38:85:15:
    79:c7:52:5a:69:98:4f:15:b5:66:7f:34:20:9b:70:
    eb:26:11:36:94:7f:a1:23:e5:49:df:ff:00:60:18:
    83:af:d9:36:fe:41:1e:00:6e:4e:93:d1:a0:0b:0f:
    ea:54:1b:bf:c8:c5:18:6c:b6:22:05:03:a9:4b:24:
    13:11:0d:64:0c:77:ea:54:ba:32:20:fc:8f:4c:c6:
    ce:77:15:1e:29:b3:e0:65:78:c4:78:bd:1b:eb:e0:
    45:89:ef:9a:19:7f:6f:80:6d:b8:b3:ec:d8:26:ca:
    d2:4f:53:24:cc:de:c6:e8:fe:ad:2c:21:50:06:86:
    02:c8:dc:dc:59:40:2c:ca:c9:42:4b:79:00:48:cc:
    dd:93:27:06:80:95:ef:a0:10:b7:f1:96:c7:4b:a8:
    c3:7b:12:8f:9e:14:11:75:16:33:f7:8b:7b:9e:56:
    f7:1f:77:a1:b4:da:ad:3f:c5:4b:5e:7e:f9:35:d9:
    a7:2f:b1:76:75:97:65:52:2b:4b:bc:02:e3:14:d5:
    c0:6b:64:d5:05:4b:7b:09:6c:60:12:36:e6:cc:f4:
    5b:5e:61:1c:80:5d:33:5d:ba:b0:c3:5d:22:6c:c2:
    08:d8:ce:47:36:ba:39:a0:35:44:26:fa:e0:06:c7:
    fe:52:d5:26:7d:cf:b9:c3:88:4f:51:fd:df:df:4a:
    97:94:bc:fe:0e:15:57:11:37:49:e6:c8:ef:42:1d:
    ba:26:3a:ff:68:73:9c:e0:0e:d8:0f:d0:02:2e:f9:
    2d:34:88:f7:6d:eb:62:bd:ef:7b:ea:60:26:f2:2a:
    1d:25:aa:2a:92:d1:24:41:4a:80:21:fe:0c:17:4b:
    98:03:e6:bb:5f:ad:75:e1:86:a9:46:a1:72:80:77:
    0f:12:43:f4:38:74:46:cc:ce:b2:22:2a:96:5c:c3:
    0b:39:29
Exponent: 3 (0x3)
```

可以看到`e`仅仅只有3。那这样，我们可以通过找到`i`使得`c + i * n`是一个完全立方数，这样开立方就可以得到消息`m`。

题目里的`i`数量级在10^9，大概跑个4分钟左右就可以了。

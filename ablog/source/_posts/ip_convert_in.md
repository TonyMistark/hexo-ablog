---
layout: post
title:  "IP转换为整数几种方式"
date:   2019-08-21 15:32:40 +0800
categories: Python
---

```python
import socket
import struct


def ip_to_int(ip_str: str) -> int:
    """
    IP转换成int
    思路：将IP按照'.'split分隔成4段，然后将每个部分转成二进制类型.
    然后将这些二进制进行拼接成一个32位的二进制字符串.
    然后将二进制数,转换成int类型
    :param ip_str:
    :return:
    """
    ip_list = ip_str.split(".")

    bin_str = ""
    for i in ip_list:
        part = bin(int(i))[2:]  # 将前面的0b标识去掉
        part = part.zfill(8)  # 将part前面补充0到8位
        bin_str += part
    # 将这个二进制串转换为int
    ip_int = int(bin_str, 2)
    return ip_int


def ip_to_int_2(ip_str: str) -> int:
    """
    方法二，通过内置socket模块
    先将ip地址字符串转为整形，使用inet_aton
    :param ip_str:
    :return:
    """
    return socket.ntohl(struct.unpack("I", socket.inet_aton(ip_str))[0])


def ip_to_int_3(ip_str: str) -> int:
    """
    方法三：通过移位的方式
    :param ip_str:
    :return:
    """
    parts = [int(x) for x in ip_str.split(".")]
    return sum(parts[i] << [24, 16, 8, 0][i] for i in range(4))


def int_to_ip(ip_int: int) -> str:
    """
    将int类型的ip数，转为32位的二进制数，然后按照8位进行分割，每8位标识一个IP的一部分即可
    :param ip_int:
    :return:
    """
    ip_bin = bin(ip_int)[2:]
    ip_bin = ip_bin.zfill(32)

    bin_list = []
    ip_str = []

    for i in range(0, 32, 8):
        bin_list.append(ip_bin[i : i + 8])

    for temp in bin_list:
        ip_str.append(str(int(temp, 2)))
    return ".".join(ip_str)


def int_to_ip_2(ip_int: int) -> str:
    """
    方法二, 通过内置模块完成
    :param ip_int:
    :return:
    """
    return socket.inet_ntoa(struct.pack("I", socket.htonl(ip_int)))


if __name__ == "__main__":
    str_ip = "127.0.0.1"
    print("ip_to_int: ", ip_to_int(str_ip))
    print("ip_to_int_2: ", ip_to_int_2(str_ip))
    print("ip_to_int_3: ", ip_to_int_3(str_ip))

    int_ip = 2130706433
    print("int_to_ip: ", int_to_ip(int_ip))
    print("int_to_ip_2: ", int_to_ip_2(int_ip))

```
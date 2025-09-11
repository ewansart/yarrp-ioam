Yarrp (Yelling at Random Routers Progressively)
=========

Yarrp is a next-generation active network topology discovery technique and tool
designed for rapid mapping at Internet scales. As with traditional traceroute,
Yarrp discovers router interfaces and the links between them. However, Yarrp
can probe at over 100Kpps and has been shown to discover >200K router
interfaces in less than 5 minutes. Yarrp supports TCP, UDP-paris, and
ICMP-paris probing over both IPv4 and IPv6. Yarrp is written in C++, runs on
Linux and BSD systems, and is open-sourced with a BSD license.

## Build

```shell
./bootstrap
./configure
make
```

## Technical details

* See https://www.cmand.org/yarrp

## Usage for IOAM probing

```shell
./yarrp -vvv -i <destination_file> -t ICMP6 -a <local_iface_ip> -I <local_iface_name> -M <local_iface_mac> -G <next_hop_iface_mac> -X 0
```

## Analysis

`yarrp` generates a `.yrp` file.

`yrp2warts` inside the [utils](./utils/) sub-directory to convert from `.yrp` to `.warts` file.

Then, we can use tools from [CAIDA's scamper](https://www.caida.org/catalog/software/scamper/), such as `sc_warts2text` and `sc_warts2json` to parse the `.warts` file.


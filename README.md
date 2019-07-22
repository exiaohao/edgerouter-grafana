# EdgeRouter monitor

办公室路由器是一台 Ubiquiti 的 EdgeRouter 6p(下面简称 ER-6p), 配置了 200Mbps 中国电信精品网和 35Mbps 的沪港线.
为了监控 ER-6p 的资源占用情况, Google 发现了一块已经做好的 dashboard: [UBNT EdgeRouter Dashboard](https://grafana.com/grafana/dashboards/1756)

正好办公室有一台小服务器(真的是小 · 服务器, E3-1220v6, 16GB, 1TB x 2) 和 [Proxmox](https://www.proxmox.com/), 于是乎安装了 [k3s](https://k3s.io/) 和以下资源完成了路由器监控看板:

- Grafana
- InfluxDB
- Telegraf

在安装 InfluxDB 和 Grafana 时为了持久化数据和配置, 为了方便就配置了一个 hostPash(因为只有一台机器, 再 nodeAffifity 把 pod 固化在一台主机就好了), 持久化方式有很多种, 可以按需配置。

在安装 Telegraf 时根据实际情况修改 SNMP 和 InfluxDB 的配置。

# OpenWrt-momo

OpenWrt 上的透明代理，基于 sing-box。

此项目是基于 [homeproxy](https://github.com/immortalwrt/homeproxy) 的修改版本。

## 特性

*   **轻量级**：使用 sing-box 作为核心，内存占用低，性能高。
*   **简洁易用**：基于 LuCI 的配置界面，保留了 homeproxy 的简洁风格。
*   **强大**：支持多种代理协议，包括 Shadowsocks, VMess, VLESS, Trojan, Hysteria, Hysteria2, Tuic 等。
*   **灵活**：支持多种路由策略，包括 规则集, GeoIP, Geosite 等。
*   **DNS 分流**：支持国内外 DNS 分流，防止 DNS 污染。
*   **TProxy**：支持 TProxy 透明代理。

## 依赖

*   `sing-box` (>= 1.8.0)
*   `luci-base`
*   `jsonfilter`

## 安装

您可以从 [Releases](https://github.com/JADECHEN248/OpenWrt-momo/releases) 页面下载最新的 ipk 包并在 OpenWrt 上安装。

```bash
opkg install luCI-app-openwrt-momo_*.ipk
```

或者您可以自行编译：

```bash
# 添加 feed 源
echo "src-git openwrt_momo https://github.com/JADECHEN248/OpenWrt-momo.git" >> feeds.conf.default

# 更新并安装 feed
./scripts/feeds update openwrt_momo
./scripts/feeds install -a -p openwrt_momo

# 在 make menuconfig 中选择 LuCI -> Applications -> luci-app-openwrt-momo
make menuconfig

# 编译
make package/luci-app-openwrt-momo/compile V=s
```

## 配置

安装完成后，您可以在 OpenWrt 的 LuCI 界面中找到 "服务" -> "OpenWrt-momo"。

1.  **添加节点**：在 "节点" 页面添加您的代理节点，或通过订阅链接导入。
2.  **配置路由**：在 "路由" 页面配置您的分流规则。
3.  **启动服务**：在 "概览" 页面启用并启动服务。

## 鸣谢

*   [immortalwrt/homeproxy](https://github.com/immortalwrt/homeproxy) - 本项目的基础
*   [SagerNet/sing-box](https://github.com/SagerNet/sing-box) - 核心代理程序

## 许可证

本项目遵循 [GPL-3.0](LICENSE) 许可证。

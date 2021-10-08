# Repo Status

- DONT WORK TILL NOW

# Github Actions Padavan K2P

- Padavan源码是[hanwckf/rt-n56u](https://github.com/hanwckf/rt-n56u)。
- Github Actions参考自[P3TERX/Actions-OpenWrt](https://github.com/P3TERX/Actions-OpenWrt)&[hanwckf/scut_padavan_build](https://github.com/hanwckf/scut_padavan_build)&[Ljzkirito/Actions-Padavan_Redmi-AC2100](https://github.com/Ljzkirito/Actions-Padavan_Redmi-AC2100)。
- 编译目标为K2P
- 默认登陆地址[192.168.5.1](http://192.168.5.1),登录名admin/admin

### Actions secrets配置
- 有关`secrets.ACTIONS_REPO_PAT`请参阅[源码更新自动编译内容](https://p3terx.com/archives/build-openwrt-with-github-actions.html#toc_13)

### 防火墙ipv6配置参考
- 关闭ipv6防火墙
```
ip6tables -F
ip6tables -X
ip6tables -P INPUT ACCEPT
ip6tables -P OUTPUT ACCEPT
ip6tables -P FORWARD ACCEPT
```
- 允许ipv6防火墙特定端口转发
```
ip6tables -A FORWARD -p tcp --dport 11899 -j ACCEPT
ip6tables -A FORWARD -p udp --dport 11899 -j ACCEPT
```
- 开放ipv6防火墙特定端口80/443
```
ip6tables -A INPUT -p tcp --dport 80 -j ACCEPT
ip6tables -A OUTPUT -p tcp --sport 80 -j ACCEPT
ip6tables -A INPUT -p tcp --dport 443 -j ACCEPT
ip6tables -A OUTPUT -p tcp --sport 443 -j ACCEPT
```
按需选择，添加在`自定义设置——脚本——在防火墙规则启动后执行`

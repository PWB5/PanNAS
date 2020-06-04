# 1. User Docs 用户文档  
系统: <kbd>Pan_NAS_RPi</kbd> 版本：<kbd>V1.1</kbd> 最后编辑时间：<kbd>*20/06/04*</kbd>  

# 2. Catalog 目录
<!-- TOC -->

- [1. User Docs 用户文档](#1-user-docs-用户文档)
- [2. Catalog 目录](#2-catalog-目录)
- [3. Zero Tier 虚拟局域网](#3-zero-tier-虚拟局域网)
- [4. Open Media Vault 网络附属存储系统](#4-open-media-vault-网络附属存储系统)
    - [4.1. SMB 网络文件共享](#41-smb-网络文件共享)
- [5. NextCloud 私有云网盘](#5-nextcloud-私有云网盘)
    - [5.1. 客户端下载安装](#51-客户端下载安装)
    - [5.2. 网页端访问](#52-网页端访问)
    - [5.3. 网盘拓展功能](#53-网盘拓展功能)
- [6. Jellyfin](#6-jellyfin)
- [7. 版本更新日志](#7-版本更新日志)

<!-- /TOC -->

# 3. Zero Tier 虚拟局域网  
* [Zero Tier](https://www.zerotier.com/) 是一个虚拟局域网 (VLAN) 方案。  
* 如果**不需要**在外网（无法连接家里的路由器，如使用4G蜂窝网络）时访问家里局域网的资源，**可跳过此步骤**。
* 因为我们家使用的~~垃圾~~移动宽带网络无法申请到公网 IP，所以在外网无法直接访问家里局域网的资源。因此，想要随时随地访问家里的资源就要安装 Zero Tier 软件。
1. 安装及配置
    <details>
    <summary><u>显示详细教程</u>（点击此处）</summary>  
  
    * 软件安装包下载地址：[官方下载网址](https://www.zerotier.com/download/) https://www.zerotier.com/download/  
    1. Windows：  
        <img src="./pic/ZeroTier_Install.png">  
        + 安装过程：略……  
            - 软件安装位置：（无限制）
        + 双击图标，运行软件
        + 配置：  
            - 右键点击系统托盘处软件图标，点击 <kbd>Join Network…</kbd>   
            <img src="./pic/176ae0f90a1dc0275afc1b77192054d.png" width=50%>  
            - 输入：`6ab565387af53c59`  
            <img src="./pic/481977efaf8f12b5ec5e1ed5440d481.png" width=50%>  
            - 网络：选择 <kbd>是</kbd>  
            <img src="./pic/5d51675868707839fef5ff34ff9e50a.png" width=50%>   
            - 可选配置：开机自启：  
                点击 <kbd>Preferences</kbd>  
                <img src="./pic/66efdbfe2379d656dc8b2bdeb63493a.png" width=50%>   
                勾选 <kbd>Launch ZeroTier On Startup</kbd>  
                <img src="./pic/b0d1f70f8843e6f9d671ef2f73afd0a.png" width=50%>   

    1.ios(iPhone/iPad…)：  
        + 因为~~富强、民主、文明、和谐、自由、平等、公正、法治、爱国、敬业、诚信、友善~~，  
            App Store 中国区无法下载安装 <kbd>ZeroTier One</kbd> 软件。需要自行百度：美区 Apple ID 账号分享。  
            使用美区 Apple ID 账号下载安装 <kbd>ZeroTier One</kbd> 软件。  
        + 输入 <kbd>Network ID</kbd> ：`6ab565387af53c59` ，点击 <kbd>Add Network</kbd> 。  

    </details>

1. 网络测试  
    * 打开[Nextcloud网站链接](http://NextCloud.PWB5.top:2020)：http://NextCloud.PWB5.top:2020  
1. 下文提及**外网访问**处，均需要 启动 ZeroTier One 软件，并 Join Network 。
    * 若按照上面教程设置，平时基本无需维护。电脑开机后会 自动启动 ZeroTier One 软件并 Join Network 。

*[返回目录](#2-catalog-目录)*  

# 4. Open Media Vault 网络附属存储系统  
* [Open Media Vault](https://www.openmediavault.org/) 是一个网络附属存储 (NAS) 系统。

1. 修改用户密码：
    <details>
    <summary><u>显示详细教程</u>（点击此处）</summary>  
    
    * 初始密码为 <kbd>22331820</kbd>    
        打开 [OpenMediaVault 用户管理](http://smb.pwb5.top:88) 网页，登录后按如下操作即可修改密码。  
        <img src="./pic/微信截图_20200602214550.png" width=100%>  
    </details>

## 4.1. SMB 网络文件共享  
* 服务器信息块（Server Message Block，SMB）是一个网络文件共享协议，它允许应用程序和终端用户从远端的文件服务器访问文件资源。
    <img src="./pic/微信截图_20200603092720.png" width=75%>  

    <details>
    <summary><u>显示详细教程</u>（点击此处）</summary>  
    
    * 局域网访问：文件夹地址栏输入：`\\NAS-PAN`  
    * 外网访问：文件夹地址栏输入：`\\SMB.PWB5.TOP`
    * 输入账号密码即可使用。
    * 映射网络驱动器 到 此电脑：  
        <img src="./pic/73d40facd2d4ec0ba179fa53c151a02.png" width=50%>   
    * 勾选 <kbd>登录时重新连接</kbd> ，则电脑开机后，会自动重新连接SMB。
        <img src="./pic/93c66d8ca870d478119e5a49e935377.png" width=80%>  
    </details>  
      

*[返回目录](#2-catalog-目录)*  

# 5. NextCloud 私有云网盘  
* [NextCloud](https://nextcloud.com/) 是一个免费专业的私有云存储网盘开源项目，可以架设一套属于自己或团队专属的云同步网盘，从而实现跨平台跨设备文件同步、共享、版本控制、团队协作等功能。  
## 5.1. 客户端下载安装   
* [官方下载网址](https://nextcloud.com/install/#install-clients)  
* 根据需求安装windows、ios客户端。  
    + windows客户端有 **文件夹同步** 功能。  
    + 可以不安装客户端，只直接使用网页端。  

    <img src="./pic/微信截图_20200603090746.png" width=100%>  

## 5.2. 网页端访问  
<!-- 1. [NextCloud_ZeroTier网址](http://192.168.192.125:2020) -->
1. 局域网访问地址：[NextCloud_Local网址](http://192.168.3.66:2020) http://192.168.3.66:2020  
1. 外网访问地址：[NextCloud_DNS网址](http://nextcloud.pwb5.top:2020) http://nextcloud.pwb5.top:2020  

    <img src="./pic/微信截图_20200603090336.png" width=100%>

## 5.3. 网盘拓展功能
* <details>
    <summary><u>显示详细教程</u>（点击此处）</summary>  
        
    * 点击网页左上角，打开**功能栏**。
    <img src="./pic/2031ca177190b85d7851653a56ac26d.png" width=50%>  
    
    1. **下载器**  
        * 在1中输入下载地址，点击2开始下载。  
        <img src="./pic/f540ad392dd8f2efa7b9f2101d7ac3c.png" width=100%>   
        * 下载完成后，文件自动保存在 <kbd>NAS_Download/Download_NextCloud/Files</kbd> 目录。   
        <img src="./pic/7777ccc91a1b838690ef28c07a16cc7.png" width=100%>   
    1. **Flowupload 大文件上传**

    </details>  

*[返回目录](#2-catalog-目录)*  

<!-- # 6. BaiduPCS  百度网盘网页版
* [baidupcs-web](https://github.com/liuzhuoling2011/baidupcs-web)是一个百度网盘网页版软件。  
1. 局域网访问地址：[BaiduPCS_Local网址](http://192.168.3.66:5299) http://192.168.3.66:5299  
1. 外网访问地址：[BaiduPCS_DNS网址](http://OMV.PWB5.top:5299) http://OMV.PWB5.top:5299  

    <img src="./pic/微信截图_20200604151228.png" width="100%">

1. 登录：
    + 注意：目前使用账号密码登录可能失败，目前无法通过分享链接下载。 -->

# 6. Jellyfin
* [Jellyfin](https://jellyfin.org/) 是一个自由的软件媒体系统，用于控制和管理媒体和流媒体。  
1. 局域网访问地址：[Jellyfin_Local网址](http://192.168.3.66:8096) http://192.168.3.66:8096  
1. 外网访问地址：[Jellyfin_DNS网址](http://Jellyfin.PWB5.top:8096) http://Jellyfin.PWB5.top:8096  

    <img src="./pic/微信截图_20200603111121.png" width="100%">

1. 添加资源到媒体库。
    * **电影**
        + 已下载的电影：通过 NextCloud 网盘的 Flowupload 上传至 /NAS_Movie 文件夹。
            <details>
            <summary><u>显示详细教程</u>（点击此处）</summary>  
              
            <img src="./pic/微信截图_20200603114218.png" width=100%>  
            <img src="./pic/39fa12963248741bd17fe8a17c88af6.png" width=100%>  
            </details>
        + 未下载的电影：电影链接使用 [Deluge 下载器](http://Jellyfin.PWB5.top:8112) 下载。
            - 登录密码：8899
    * **电视剧**
        + 同上，文件夹为 /NAS_TVShows
    * **音乐**

*[返回目录](#2-catalog-目录)*  

# 7. 版本更新日志
1. V1.0 20/06/03
    * 新增：
        + [Zero Tier 虚拟局域网](#3-zero-tier-虚拟局域网) ;  
        + [Open Media Vault 网络附属存储系统](#4-open-media-vault-网络附属存储系统) ;  
        + [NextCloud 私有云网盘](#5-nextcloud-私有云网盘) ;  
        + [Jellyfin](#6-jellyfin) ;
<!-- 1. V1.1 20/06/04
    * 新增： -->

*[返回目录](#2-catalog-目录)*  

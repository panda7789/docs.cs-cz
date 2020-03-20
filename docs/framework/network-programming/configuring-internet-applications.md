---
title: Konfigurace internetových aplikací
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, default proxy
- sending data, default proxy
- receiving data, default proxy
- downloading Internet resources, configuring Internet applications
- protocol-specific modules
- custom authentication modules
- receiving data, configuring Internet applications
- configuration settings [.NET Framework], Internet applications
- requesting data from Internet, configuring Internet applications
- requesting data from Internet, default proxy
- response to Internet request, default proxy
- Internet, configuring Internet applications
- response to Internet request, configuring Internet applications
- default proxy
- network resources, default proxy
- sending data, configuring Internet applications
- network resources, configuring Internet applications
- Internet, default proxy
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
ms.openlocfilehash: ee4dc87383153ae4e8df0a3bed7cce5220e65405
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048636"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="ff0f0-102">Konfigurace internetových aplikací</span><span class="sxs-lookup"><span data-stu-id="ff0f0-102">Configuring Internet Applications</span></span>
<span data-ttu-id="ff0f0-103">Konfigurační prvek [ \<system.Net> Element (Nastavení sítě)](../configure-apps/file-schema/network/system-net-element-network-settings.md) obsahuje informace o konfiguraci sítě pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-103">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="ff0f0-104">Pomocí system.Net [> Element (Nastavení sítě) můžete nastavit proxy servery, nastavit parametry správy připojení a zahrnout do aplikace vlastní moduly ověřování a požadavků. \<](../configure-apps/file-schema/network/system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ff0f0-104">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="ff0f0-105">Element [ \<defaultProxy> Element (Nastavení sítě)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) definuje proxy `GlobalProxySelection` server vrácený třídou.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-105">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="ff0f0-106">Každý, <xref:System.Net.HttpWebRequest> který nemá <xref:System.Net.HttpWebRequest.Proxy%2A> vlastní vlastnost nastavenou na určitou hodnotu, používá výchozí proxy server.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="ff0f0-107">Kromě nastavení adresy proxy můžete vytvořit seznam adres serveru, které nebudou používat proxy server, a můžete označit, že proxy server by neměl být používán pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="ff0f0-108">Je důležité si uvědomit, že nastavení aplikace Microsoft Internet Explorer jsou kombinována s nastavením konfigurace, přičemž druhé má přednost.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="ff0f0-109">Následující příklad nastaví výchozí adresu `http://proxyserver`serveru proxy na , označuje, že proxy server by neměl být používán pro místní adresy, a určuje, že všechny požadavky na servery umístěné v contoso.com doméně by měly proxy server obejít.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-109">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="ff0f0-110">Pomocí elementu [ \<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) nakonfigurujte počet trvalých připojení, která lze provést na určitém serveru nebo na všech ostatních serverech.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-110">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="ff0f0-111">Následující příklad konfiguruje aplikaci tak, `www.contoso.com`aby používala dvě trvalá připojení k serveru , čtyři trvalá připojení k serveru s adresou IP 192.168.1.2 a jedno trvalé připojení ke všem ostatním serverům.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-111">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="ff0f0-112">Vlastní ověřovací moduly jsou konfigurovány s prvkem [ \<authenticationModules> Element (Network Settings).](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ff0f0-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="ff0f0-113">Vlastní ověřovací moduly <xref:System.Net.IAuthenticationModule> musí implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="ff0f0-114">Následující příklad konfiguruje vlastní ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="ff0f0-115">Pomocí elementu [ \<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) můžete nakonfigurovat aplikaci tak, aby používala vlastní moduly specifické pro protokol k vyžádání informací z internetových prostředků.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-115">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="ff0f0-116">Zadané moduly musí <xref:System.Net.IWebRequestCreate> implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="ff0f0-117">Výchozí moduly požadavků HTTP, HTTPS a souborů můžete přepsat zadáním vlastního modulu v konfiguračním souboru, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ff0f0-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff0f0-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff0f0-118">See also</span></span>

- [<span data-ttu-id="ff0f0-119">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ff0f0-119">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="ff0f0-120">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="ff0f0-120">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="ff0f0-121">\<system.Net> element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="ff0f0-121">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)

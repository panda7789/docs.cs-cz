---
title: "Konfigurace Internetové aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6891f6e8081862fdbf0e9423a6b74fbea0d6e149
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="9037c-102">Konfigurace Internetové aplikace</span><span class="sxs-lookup"><span data-stu-id="9037c-102">Configuring Internet Applications</span></span>
<span data-ttu-id="9037c-103">[ \<System.Net > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) konfigurační prvek obsahuje informace o konfiguraci sítě pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="9037c-103">The [\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="9037c-104">Pomocí [ \<system.Net > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) elementu, můžete nastavit proxy servery, nastavte připojení parametry správy a zahrnout vlastní moduly ověřování a požadavek do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="9037c-104">Using the [\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="9037c-105">[ \<DefaultProxy – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element definuje proxy serveru vrácené `GlobalProxySelection` třídy.</span><span class="sxs-lookup"><span data-stu-id="9037c-105">The [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="9037c-106">Všechny <xref:System.Net.HttpWebRequest> , nemá vlastní <xref:System.Net.HttpWebRequest.Proxy%2A> vlastnost nastavit na konkrétní hodnotu používá výchozí proxy server.</span><span class="sxs-lookup"><span data-stu-id="9037c-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="9037c-107">Kromě nastavení adresu proxy serveru, můžete vytvořit seznam adres serveru, které nebudou využívat proxy server, a můžete určit, že by neměl používat proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="9037c-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="9037c-108">Je důležité si uvědomit, že nastavení aplikace Microsoft Internet Explorer jsou společně s nastavením konfigurace s přednost před pozdější pořízení.</span><span class="sxs-lookup"><span data-stu-id="9037c-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="9037c-109">Následující příklad nastaví výchozí proxy server adresu serveru http://proxyserver, označuje, že by se neměla používat pro místní adresy proxy serveru a určuje, že všechny požadavky na servery umístěné v doméně contoso.com, měli používat proxy server.</span><span class="sxs-lookup"><span data-stu-id="9037c-109">The following example sets the default proxy server address to http://proxyserver, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
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
  
 <span data-ttu-id="9037c-110">Použití [ \<connectionManagement – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) elementu, který chcete nakonfigurovat počet trvalého připojení, které můžete provést pro konkrétní server nebo na jiné servery.</span><span class="sxs-lookup"><span data-stu-id="9037c-110">Use the [\<connectionManagement> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="9037c-111">Následující příklad konfiguruje aplikaci, aby používala dva trvalé připojení k serveru www.contoso.com, čtyři trvalé připojení k serveru s IP adresou 192.168.1.2 a jeden trvalé připojení na jiné servery.</span><span class="sxs-lookup"><span data-stu-id="9037c-111">The following example configures the application to use two persistent connections to the server www.contoso.com, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
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
  
 <span data-ttu-id="9037c-112">Vlastní ověřovací moduly jsou nakonfigurovány s [ \<authenticationModules – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="9037c-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="9037c-113">Vlastní ověřovací moduly musí implementovat <xref:System.Net.IAuthenticationModule> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9037c-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="9037c-114">Následující příklad konfiguruje modul vlastní ověřování.</span><span class="sxs-lookup"><span data-stu-id="9037c-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="9037c-115">Můžete použít [ \<webRequestModules – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) elementu, který chcete nakonfigurovat aplikace použijte vlastní moduly protokolu specifické pro žádost o informace z prostředků z Internetu.</span><span class="sxs-lookup"><span data-stu-id="9037c-115">You can use the [\<webRequestModules> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="9037c-116">Zadané moduly musí implementovat <xref:System.Net.IWebRequestCreate> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9037c-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="9037c-117">Výchozí HTTP, HTTPS a soubor žádosti o moduly můžete přepsat zadáním vlastního modulu v konfiguračním souboru, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9037c-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9037c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="9037c-118">See Also</span></span>  
 [<span data-ttu-id="9037c-119">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9037c-119">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="9037c-120">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="9037c-120">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="9037c-121">\<system.Net > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="9037c-121">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)

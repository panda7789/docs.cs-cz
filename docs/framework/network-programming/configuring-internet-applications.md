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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048636"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="7fefe-102">Konfigurace internetových aplikací</span><span class="sxs-lookup"><span data-stu-id="7fefe-102">Configuring Internet Applications</span></span>
<span data-ttu-id="7fefe-103">Prvek konfigurace System .NET [> (nastavení sítě) obsahuje informace o konfiguraci sítě pro aplikace. \<](../configure-apps/file-schema/network/system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7fefe-103">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="7fefe-104">Pomocí elementu System .NET [> element (nastavení sítě) můžete nastavit proxy servery, nastavit parametry správy připojení a zahrnout do aplikace vlastní ověřování a moduly požadavků. \<](../configure-apps/file-schema/network/system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7fefe-104">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="7fefe-105">`GlobalProxySelection` [ PrvekdefaultProxy>element(nastavenísítě)definujeproxyserver\<](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) vrácenou třídou.</span><span class="sxs-lookup"><span data-stu-id="7fefe-105">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="7fefe-106">Všechny <xref:System.Net.HttpWebRequest> , které nemají svou vlastní <xref:System.Net.HttpWebRequest.Proxy%2A> vlastnost nastavenou na určitou hodnotu, používají výchozí proxy server.</span><span class="sxs-lookup"><span data-stu-id="7fefe-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="7fefe-107">Kromě nastavení adresy proxy můžete vytvořit seznam adres serverů, které nepoužívají proxy server, a můžete určit, že proxy server by neměl být používán pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="7fefe-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="7fefe-108">Je důležité si uvědomit, že nastavení aplikace Microsoft Internet Explorer jsou kombinována s nastaveními konfigurace, přičemž druhá má přednost.</span><span class="sxs-lookup"><span data-stu-id="7fefe-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="7fefe-109">Následující příklad nastaví výchozí adresu proxy server na `http://proxyserver`, označuje, že proxy server by neměl být používán pro místní adresy a určuje, že všechny požadavky na servery nacházející se v doméně contoso.com by měly obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="7fefe-109">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
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
  
 <span data-ttu-id="7fefe-110">Pomocí prvku connectionManagement > [element (nastavení sítě) nakonfigurujte počet trvalých připojení, která lze provést na konkrétní server nebo na všechny ostatní servery. \<](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7fefe-110">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="7fefe-111">Následující příklad nakonfiguruje aplikaci tak, aby používala dvě trvalá připojení `www.contoso.com`k serveru, čtyři trvalá připojení k serveru s IP adresou 192.168.1.2 a jedno trvalé připojení ke všem ostatním serverům.</span><span class="sxs-lookup"><span data-stu-id="7fefe-111">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
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
  
 <span data-ttu-id="7fefe-112">Vlastní moduly ověřování jsou nakonfigurovány pomocí [ \<elementu authenticationModules > element (nastavení sítě)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) .</span><span class="sxs-lookup"><span data-stu-id="7fefe-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="7fefe-113">Vlastní moduly ověřování musí implementovat <xref:System.Net.IAuthenticationModule> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7fefe-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="7fefe-114">Následující příklad konfiguruje vlastní ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="7fefe-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="7fefe-115">Pomocí prvku [webRequestModules > element (nastavení sítě) můžete nakonfigurovat aplikaci tak, aby používala vlastní moduly specifické pro protokol k vyžádání informací z internetových prostředků. \<](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7fefe-115">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="7fefe-116">Zadané moduly musí implementovat <xref:System.Net.IWebRequestCreate> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7fefe-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="7fefe-117">Výchozí moduly HTTP, HTTPS a požadavky na soubor můžete přepsat tak, že do konfiguračního souboru zadáte vlastní modul, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7fefe-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7fefe-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7fefe-118">See also</span></span>

- [<span data-ttu-id="7fefe-119">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7fefe-119">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="7fefe-120">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="7fefe-120">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="7fefe-121">\<System .NET > – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="7fefe-121">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)

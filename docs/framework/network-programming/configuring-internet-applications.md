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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d2f3f015689510237142572f230b53ba7bd393ca
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780950"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="13690-102">Konfigurace internetových aplikací</span><span class="sxs-lookup"><span data-stu-id="13690-102">Configuring Internet Applications</span></span>
<span data-ttu-id="13690-103">[ \<System.Net > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) prvek konfigurace obsahuje informace o konfiguraci sítě pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="13690-103">The [\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="13690-104">Použití [ \<system.Net > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element, můžete nastavit proxy servery, nastavit správu parametry připojení a vlastní moduly ověřování a žádosti do aplikace zahrnout.</span><span class="sxs-lookup"><span data-stu-id="13690-104">Using the [\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="13690-105">[ \<DefaultProxy > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element definuje proxy serveru vrácenému službou `GlobalProxySelection` třídy.</span><span class="sxs-lookup"><span data-stu-id="13690-105">The [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="13690-106">Žádné <xref:System.Net.HttpWebRequest> , který nemá vlastní <xref:System.Net.HttpWebRequest.Proxy%2A> nastavenou na určitou hodnotu používá výchozí proxy server.</span><span class="sxs-lookup"><span data-stu-id="13690-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="13690-107">Kromě nastavení adresu proxy serveru, můžete vytvořit seznam adres serveru, které nebudou využívat proxy server, a můžete určit, že by neměla použít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="13690-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="13690-108">Je důležité si uvědomit, že nastavení aplikace Microsoft Internet Explorer spolu s nastavením konfigurace se přednost před pozdější a současně.</span><span class="sxs-lookup"><span data-stu-id="13690-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="13690-109">Následující příklad nastaví výchozí proxy server adresu serveru na http://proxyserver, označuje, že by neměla používat pro místní adresy proxy serveru a určuje, že všechny požadavky na servery umístěné v doméně contoso.com by měl používat proxy server.</span><span class="sxs-lookup"><span data-stu-id="13690-109">The following example sets the default proxy server address to http://proxyserver, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
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
  
 <span data-ttu-id="13690-110">Použití [ \<connectionManagement – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) prvek, který chcete nakonfigurovat počet trvalých připojení, které mohou být provedeny na konkrétní server nebo do všech ostatních serverech.</span><span class="sxs-lookup"><span data-stu-id="13690-110">Use the [\<connectionManagement> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="13690-111">Následující příklad nastaví aplikace pro použití dvou trvalé připojení k serveru www.contoso.com, čtyři trvalé připojení k serveru s IP adresou 192.168.1.2 a jeden trvalé připojení pro všechny ostatní servery.</span><span class="sxs-lookup"><span data-stu-id="13690-111">The following example configures the application to use two persistent connections to the server www.contoso.com, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
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
  
 <span data-ttu-id="13690-112">Vlastní ověřovací moduly jsou nakonfigurovány s [ \<authenticationModules – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="13690-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="13690-113">Musíte implementovat vlastní ověřování moduly <xref:System.Net.IAuthenticationModule> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="13690-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="13690-114">Následující příklad nastaví vlastní ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="13690-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="13690-115">Můžete použít [ \<webRequestModules – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element konfigurace aplikace pomocí vlastních modulů specifické informace o žádostech ze zdrojů v Internetu.</span><span class="sxs-lookup"><span data-stu-id="13690-115">You can use the [\<webRequestModules> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="13690-116">Zadané moduly musí implementovat <xref:System.Net.IWebRequestCreate> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="13690-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="13690-117">Výchozí HTTP, HTTPS a soubor žádosti o moduly můžete přepsat zadáním vlastního modulu v konfiguračním souboru, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="13690-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13690-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="13690-118">See Also</span></span>  
 [<span data-ttu-id="13690-119">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="13690-119">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="13690-120">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="13690-120">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="13690-121">\<system.Net > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="13690-121">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)

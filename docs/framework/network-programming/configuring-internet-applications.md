---
title: Konfigurace internetových aplikací
description: Naučte se, jak pomocí elementu <system.Net> nakonfigurovat internetové aplikace v .NET Framework. Tento článek obsahuje příklad kódu.
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
ms.openlocfilehash: 760a4ac7cec9abeabfc372c3be5bd3860a6fb03a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502636"
---
# <a name="configuring-internet-applications"></a>Konfigurace internetových aplikací
Prvek konfigurace [ \<system.Net> elementu (nastavení sítě)](../configure-apps/file-schema/network/system-net-element-network-settings.md) obsahuje informace o konfiguraci sítě pro aplikace. Pomocí elementu [ \<system.Net> (nastavení sítě)](../configure-apps/file-schema/network/system-net-element-network-settings.md) můžete nastavit proxy servery, nastavit parametry správy připojení a zahrnout do aplikace vlastní ověřování a moduly požadavků.  
  
 Element [ \<defaultProxy> (nastavení sítě)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) definuje proxy server vráceného `GlobalProxySelection` třídou. Všechny <xref:System.Net.HttpWebRequest> , které nemají svou vlastní <xref:System.Net.HttpWebRequest.Proxy%2A> vlastnost nastavenou na určitou hodnotu, používají výchozí proxy server. Kromě nastavení adresy proxy můžete vytvořit seznam adres serverů, které nepoužívají proxy server, a můžete určit, že proxy server by neměl být používán pro místní adresy.  
  
 Je důležité si uvědomit, že nastavení aplikace Microsoft Internet Explorer jsou kombinována s nastaveními konfigurace, přičemž druhá má přednost.  
  
 Následující příklad nastaví výchozí adresu proxy server na `http://proxyserver` , označuje, že proxy server by neměl být používán pro místní adresy a určuje, že všechny požadavky na servery nacházející se v doméně contoso.com by měly obejít proxy server.  
  
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
  
 Pomocí elementu [ \<connectionManagement> (nastavení sítě)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) nakonfigurujte počet trvalých připojení, která lze provést na konkrétní server nebo na všechny ostatní servery. Následující příklad nakonfiguruje aplikaci tak, aby používala dvě trvalá připojení k serveru `www.contoso.com` , čtyři trvalá připojení k serveru s IP adresou 192.168.1.2 a jedno trvalé připojení ke všem ostatním serverům.  
  
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
  
 Vlastní moduly ověřování jsou nakonfigurovány pomocí elementu [ \<authenticationModules> (nastavení sítě)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) . Vlastní moduly ověřování musí implementovat <xref:System.Net.IAuthenticationModule> rozhraní.  
  
 Následující příklad konfiguruje vlastní ověřovací modul.  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 Pomocí elementu [ \<webRequestModules> (nastavení sítě)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) můžete nakonfigurovat aplikaci tak, aby používala vlastní moduly specifické pro protokol k vyžádání informací z internetových prostředků. Zadané moduly musí implementovat <xref:System.Net.IWebRequestCreate> rozhraní. Výchozí moduly HTTP, HTTPS a požadavky na soubor můžete přepsat tak, že do konfiguračního souboru zadáte vlastní modul, jak je uvedeno v následujícím příkladu.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Síťové programování v rozhraní .NET Framework](index.md)
- [Schéma nastavení sítě](../configure-apps/file-schema/network/index.md)
- [\<system.Net>– Element (nastavení sítě)](../configure-apps/file-schema/network/system-net-element-network-settings.md)

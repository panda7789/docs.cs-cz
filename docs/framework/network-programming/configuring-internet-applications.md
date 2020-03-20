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
# <a name="configuring-internet-applications"></a>Konfigurace internetových aplikací
Konfigurační prvek [ \<system.Net> Element (Nastavení sítě)](../configure-apps/file-schema/network/system-net-element-network-settings.md) obsahuje informace o konfiguraci sítě pro aplikace. Pomocí system.Net [> Element (Nastavení sítě) můžete nastavit proxy servery, nastavit parametry správy připojení a zahrnout do aplikace vlastní moduly ověřování a požadavků. \<](../configure-apps/file-schema/network/system-net-element-network-settings.md)  
  
 Element [ \<defaultProxy> Element (Nastavení sítě)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) definuje proxy `GlobalProxySelection` server vrácený třídou. Každý, <xref:System.Net.HttpWebRequest> který nemá <xref:System.Net.HttpWebRequest.Proxy%2A> vlastní vlastnost nastavenou na určitou hodnotu, používá výchozí proxy server. Kromě nastavení adresy proxy můžete vytvořit seznam adres serveru, které nebudou používat proxy server, a můžete označit, že proxy server by neměl být používán pro místní adresy.  
  
 Je důležité si uvědomit, že nastavení aplikace Microsoft Internet Explorer jsou kombinována s nastavením konfigurace, přičemž druhé má přednost.  
  
 Následující příklad nastaví výchozí adresu `http://proxyserver`serveru proxy na , označuje, že proxy server by neměl být používán pro místní adresy, a určuje, že všechny požadavky na servery umístěné v contoso.com doméně by měly proxy server obejít.  
  
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
  
 Pomocí elementu [ \<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) nakonfigurujte počet trvalých připojení, která lze provést na určitém serveru nebo na všech ostatních serverech. Následující příklad konfiguruje aplikaci tak, `www.contoso.com`aby používala dvě trvalá připojení k serveru , čtyři trvalá připojení k serveru s adresou IP 192.168.1.2 a jedno trvalé připojení ke všem ostatním serverům.  
  
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
  
 Vlastní ověřovací moduly jsou konfigurovány s prvkem [ \<authenticationModules> Element (Network Settings).](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) Vlastní ověřovací moduly <xref:System.Net.IAuthenticationModule> musí implementovat rozhraní.  
  
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
  
 Pomocí elementu [ \<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) můžete nakonfigurovat aplikaci tak, aby používala vlastní moduly specifické pro protokol k vyžádání informací z internetových prostředků. Zadané moduly musí <xref:System.Net.IWebRequestCreate> implementovat rozhraní. Výchozí moduly požadavků HTTP, HTTPS a souborů můžete přepsat zadáním vlastního modulu v konfiguračním souboru, jako v následujícím příkladu.  
  
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
  
## <a name="see-also"></a>Viz také

- [Síťové programování v rozhraní .NET Framework](index.md)
- [Schéma nastavení sítě](../configure-apps/file-schema/network/index.md)
- [\<system.Net> element (nastavení sítě)](../configure-apps/file-schema/network/system-net-element-network-settings.md)

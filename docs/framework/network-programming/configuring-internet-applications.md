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
ms.openlocfilehash: 81b0f69306a0f9a4ed6d35e3c8ef95271a779294
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847929"
---
# <a name="configuring-internet-applications"></a>Konfigurace internetových aplikací
[ \<System.Net > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) prvek konfigurace obsahuje informace o konfiguraci sítě pro aplikace. Použití [ \<system.Net > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element, můžete nastavit proxy servery, nastavit správu parametry připojení a vlastní moduly ověřování a žádosti do aplikace zahrnout.  
  
 [ \<DefaultProxy > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element definuje proxy serveru vrácenému službou `GlobalProxySelection` třídy. Žádné <xref:System.Net.HttpWebRequest> , který nemá vlastní <xref:System.Net.HttpWebRequest.Proxy%2A> nastavenou na určitou hodnotu používá výchozí proxy server. Kromě nastavení adresu proxy serveru, můžete vytvořit seznam adres serveru, které nebudou využívat proxy server, a můžete určit, že by neměla použít proxy server pro místní adresy.  
  
 Je důležité si uvědomit, že nastavení aplikace Microsoft Internet Explorer spolu s nastavením konfigurace se přednost před pozdější a současně.  
  
 Následující příklad nastaví výchozí proxy server adresu serveru na `http://proxyserver`, označuje, že by neměla používat pro místní adresy proxy serveru a určuje, že všechny požadavky na servery umístěné v doméně contoso.com by měl používat proxy server.  
  
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
  
 Použití [ \<connectionManagement – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) prvek, který chcete nakonfigurovat počet trvalých připojení, které mohou být provedeny na konkrétní server nebo do všech ostatních serverech. Následující příklad nastaví aplikace pro použití dvou trvalé připojení k serveru www.contoso.com, čtyři trvalé připojení k serveru s IP adresou 192.168.1.2 a jeden trvalé připojení pro všechny ostatní servery.  
  
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
  
 Vlastní ověřovací moduly jsou nakonfigurovány s [ \<authenticationModules – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) elementu. Musíte implementovat vlastní ověřování moduly <xref:System.Net.IAuthenticationModule> rozhraní.  
  
 Následující příklad nastaví vlastní ověřovací modul.  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 Můžete použít [ \<webRequestModules – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element konfigurace aplikace pomocí vlastních modulů specifické informace o žádostech ze zdrojů v Internetu. Zadané moduly musí implementovat <xref:System.Net.IWebRequestCreate> rozhraní. Výchozí HTTP, HTTPS a soubor žádosti o moduly můžete přepsat zadáním vlastního modulu v konfiguračním souboru, jako v následujícím příkladu.  
  
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
 [Síťové programování v rozhraní .NET Framework](../../../docs/framework/network-programming/index.md)  
 [Schéma nastavení sítě](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<system.Net > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)

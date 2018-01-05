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
# <a name="configuring-internet-applications"></a>Konfigurace Internetové aplikace
[ \<System.Net > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) konfigurační prvek obsahuje informace o konfiguraci sítě pro aplikace. Pomocí [ \<system.Net > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) elementu, můžete nastavit proxy servery, nastavte připojení parametry správy a zahrnout vlastní moduly ověřování a požadavek do vaší aplikace.  
  
 [ \<DefaultProxy – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element definuje proxy serveru vrácené `GlobalProxySelection` třídy. Všechny <xref:System.Net.HttpWebRequest> , nemá vlastní <xref:System.Net.HttpWebRequest.Proxy%2A> vlastnost nastavit na konkrétní hodnotu používá výchozí proxy server. Kromě nastavení adresu proxy serveru, můžete vytvořit seznam adres serveru, které nebudou využívat proxy server, a můžete určit, že by neměl používat proxy server pro místní adresy.  
  
 Je důležité si uvědomit, že nastavení aplikace Microsoft Internet Explorer jsou společně s nastavením konfigurace s přednost před pozdější pořízení.  
  
 Následující příklad nastaví výchozí proxy server adresu serveru http://proxyserver, označuje, že by se neměla používat pro místní adresy proxy serveru a určuje, že všechny požadavky na servery umístěné v doméně contoso.com, měli používat proxy server.  
  
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
  
 Použití [ \<connectionManagement – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) elementu, který chcete nakonfigurovat počet trvalého připojení, které můžete provést pro konkrétní server nebo na jiné servery. Následující příklad konfiguruje aplikaci, aby používala dva trvalé připojení k serveru www.contoso.com, čtyři trvalé připojení k serveru s IP adresou 192.168.1.2 a jeden trvalé připojení na jiné servery.  
  
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
  
 Vlastní ověřovací moduly jsou nakonfigurovány s [ \<authenticationModules – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) elementu. Vlastní ověřovací moduly musí implementovat <xref:System.Net.IAuthenticationModule> rozhraní.  
  
 Následující příklad konfiguruje modul vlastní ověřování.  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 Můžete použít [ \<webRequestModules – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) elementu, který chcete nakonfigurovat aplikace použijte vlastní moduly protokolu specifické pro žádost o informace z prostředků z Internetu. Zadané moduly musí implementovat <xref:System.Net.IWebRequestCreate> rozhraní. Výchozí HTTP, HTTPS a soubor žádosti o moduly můžete přepsat zadáním vlastního modulu v konfiguračním souboru, jako v následujícím příkladu.  
  
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
 [\<system.Net > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)

---
title: Konfigurace proxy serveru
ms.date: 06/18/2018
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6cf25d3d7dcde963f06729794716b75dffdb64ae
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207362"
---
# <a name="proxy-configuration"></a>Konfigurace proxy serveru
Proxy server zpracovává požadavky na klienta pro prostředky. Proxy server můžete vrátit požadovaný prostředek ze své mezipaměti nebo předat požadavek na server, kde je umístěn daný prostředek. Proxy může zlepšit výkon sítě snížením počtu požadavky odeslané na vzdálených serverech. Proxy lze také omezit přístup k prostředkům.  
  
## <a name="adaptive-proxies"></a>Adaptivní proxy  
 V rozhraní .NET Framework, proxy servery existují ve dvou variantách: Adaptivní a statické. Adaptivní proxy úprava jejich nastavení, když se změny v konfiguraci sítě. Například pokud uživatel přenosný počítač spustí telefonické připojení sítě, adaptivní proxy by rozpoznat tuto změnu, zjistit a spusťte nový skript pro konfiguraci a jeho nastavení, odpovídajícím způsobem.  
  
 Adaptivní proxy se nakonfiguroval konfigurační skript (viz [automatické zjišťování Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)). Tento skript generuje sadu protokoly aplikací a proxy serveru pro každý protokol.  
  
 Změny v prostředí sítě můžou vyžadovat, že systém použít novou sadu serverů proxy. Pokud připojení k síti ocitne mimo provoz nebo je inicializován nového připojení k síti, systém musí vyhledat příslušný zdroj konfigurační skript v nové verzi prostředí a spusťte nový skript.  
  
 Můžete použít `usesystemdefault` atribut [ `<proxy>` ](../configure-apps/file-schema/network/proxy-element-network-settings.md) element v konfiguračním souboru. `usesystemdefault` Atribut ovládací prvky, zda nastavení statické proxy (adresa proxy serveru, seznam obcházení a nepoužívat v místní) byste si měli přečíst z nastavení proxy serveru aplikace Internet Explorer pro uživatele. Pokud tato hodnota nastavena na `true`, použije se nastavení statické proxy serveru z Internet Exploreru. Pokud je tato hodnota `false` nebo není nastavený, nastavení statické proxy může být zadaný v konfiguraci a přepíše nastavení proxy serveru aplikace Internet Explorer. Tato hodnota musí být také nastaven na `false` nebo není nastaveno adaptivní proxy, aby byl povolen.  
  
 Následující příklad ukazuje konfiguraci typické adaptivní proxy.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Statické proxy  
 Statické proxy jsou obvykle explicitně nakonfigurovaná aplikací, nebo při vyvolání konfiguračního souboru aplikace nebo systému. Statické proxy jsou užitečné v sítích, ve kterých změny topologie zřídka, jako je například stolní počítač připojený k podnikové síti.  
  
 Několik možností, jak řídit, jak funguje statické proxy server. Můžete zadat následující:  
  
-   Adresa proxy serveru.  
  
-   Jestli by měl obejít proxy pro místní adresy.  
  
-   Jestli má u sadu adres název proxy serveru.  
  
 V následující tabulce jsou uvedeny možnosti konfigurace pro statické proxy server.  
  
|Atribut, vlastnost nebo konfigurace nastavení souboru|Popis|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` Nebo <xref:System.Net.WebProxy.Address>|Adresa proxy serveru používat.|  
|`bypassonlocal` Nebo <xref:System.Net.WebProxy.BypassProxyOnLocal>|Určuje, zda je vynechá proxy pro místní adresy.|  
|`bypasslist` Nebo <xref:System.Net.WebProxy.BypassArrayList>|Popisuje sadu adres, které používat proxy server s použitím regulárních výrazů.|  
|`usesystemdefault`|Určuje, zda nastavení statické proxy (adresa proxy seznam obcházení a nepoužívat místního) byste si měli přečíst z nastavení proxy serveru aplikace Internet Explorer pro uživatele. Pokud tato hodnota nastavena na `true`, pak se použije nastavení statické proxy serveru z Internet Exploreru. V rozhraní .NET Framework 2.0, pokud je tato hodnota nastavena na `true`, ostatní nastavení proxy serveru v konfiguračním souboru nejsou přepsat nastavení proxy serveru aplikace Internet Explorer. V rozhraní .NET Framework 1.1 je možné přepsat nastavení proxy serveru aplikace Internet Explorer Další nastavení proxy serveru v konfiguračním souboru.<br /><br /> Pokud je tato hodnota `false` nebo není nastavený, potom nastavení statické proxy může být zadaný v konfiguraci a přepíše nastavení proxy serveru aplikace Internet Explorer. Tato hodnota musí být také nastaven na `false` nebo není nastaveno adaptivní proxy, aby byl povolen.|  
  
 Následující příklad ukazuje konfiguraci typické statické proxy.  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [Automatické rozpoznávání proxy serveru](../../../docs/framework/network-programming/automatic-proxy-detection.md)

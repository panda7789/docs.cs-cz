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
ms.openlocfilehash: eaabb382a7bbb2cdd19c884fcd8499e626f70d4a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180988"
---
# <a name="proxy-configuration"></a>Konfigurace proxy serveru
Proxy server zpracovává požadavky klientů na prostředky. Proxy server můžete vrátit požadovaný prostředek uloženou v mezipaměti nebo předání požadavku na server, ve kterém je prostředek umístěn. Proxy může zlepšit výkon sítě snížením počtu požadavky odeslané na vzdálených serverech. Proxy servery lze také omezit přístup k prostředkům.  
  
## <a name="adaptive-proxies"></a>Adaptivní proxy servery  
 V rozhraní .NET Framework, existují proxy servery ve dvou variantách: Adaptivní a statická. Adaptivní proxy upravit jejich nastavení, když se změní konfiguraci sítě. Například pokud uživatel přenosný počítač spustí telefonického připojení k síti, adaptivní proxy by rozpozná tuto změnu, zjišťování a spusťte nový skript pro konfiguraci a jeho nastavení, odpovídajícím způsobem.  
  
 Adaptivní proxy servery jsou nakonfigurovány pomocí konfigurační skript (viz [automatické zjišťování Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)). Tento skript generuje sadu protokoly aplikací a proxy serveru pro každý protokol.  
  
 Změny v prostředí sítě může vyžadovat, že systém použít novou sadu proxy servery. Pokud připojení k síti ocitne mimo provoz nebo nového připojení k síti je inicializována, systém musí vyhledat příslušný zdrojový konfigurační skript v novém prostředí a spusťte nový skript.  
  
 Můžete použít `usesystemdefault` atribut [ `<proxy>` ](../configure-apps/file-schema/network/proxy-element-network-settings.md) element v konfiguračním souboru. `usesystemdefault` Atribut ovládací prvky, jestli byste si měli přečíst nastavení statické proxy serveru (adresa proxy serveru, seznam obcházení a obejít v místní) z nastavení proxy aplikace Internet Explorer pro daného uživatele. Pokud tato hodnota nastavená na `true`, použije se nastavení statické proxy serveru z aplikace Internet Explorer. Pokud je tato hodnota `false` nebo není nastavený, nastavení statické proxy serveru se dá nastavit v konfiguraci a přepíše nastavení proxy aplikace Internet Explorer. Tato hodnota musí být také nastavena `false` nebo nebyla nastavena adaptivní proxy, aby byla povolená.  
  
 Následující příklad ukazuje konfiguraci typické adaptivní proxy.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Statické proxy servery  
 Statické proxy servery jsou obvykle explicitně nakonfigurovat aplikace, nebo při vyvolání konfigurační soubor aplikace nebo systému. Statické proxy jsou užitečné v sítích, ve kterých topologie mění zřídka, jako je například stolní počítač připojený k podnikové síti.  
  
 Několik možností, jak řídit, jak funguje statické proxy serveru. Můžete zadat následující:  
  
-   Adresa proxy serveru.  
  
-   Určuje, zda by měl obejít proxy server pro místní adresy.  
  
-   Určuje, zda by měl obejdou pro sadu adres proxy serveru.  
  
 V následující tabulce jsou uvedeny možnosti konfigurace pro statické proxy serveru.  
  
|Nastavení konfigurace, vlastnosti nebo atributu souboru|Popis|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` Nebo <xref:System.Net.WebProxy.Address>|Adresa proxy serveru používat.|  
|`bypassonlocal` Nebo <xref:System.Net.WebProxy.BypassProxyOnLocal>|Určuje, zda je pro místní adresy obejít proxy server.|  
|`bypasslist` Nebo <xref:System.Net.WebProxy.BypassArrayList>|Popisuje sadu adresy, které obcházení proxy serveru pomocí regulárních výrazů.|  
|`usesystemdefault`|Určuje, zda nastavení statické proxy serveru (adresa proxy serveru, seznam obcházení a obejít na místních) byste si měli přečíst z nastavení proxy aplikace Internet Explorer pro daného uživatele. Pokud tato hodnota nastavená na `true`, pak budou použita nastavení statické proxy z aplikace Internet Explorer. V rozhraní .NET Framework 2.0, pokud je tato hodnota nastavena na `true`, nastavení proxy aplikace Internet Explorer nejsou přepsána další nastavení proxy v konfiguračním souboru. V rozhraní .NET Framework 1.1 mohou být přepsány nastavení proxy aplikace Internet Explorer Další nastavení proxy v konfiguračním souboru.<br /><br /> Pokud je tato hodnota `false` nebo není nastavený, potom nastavení statické proxy serveru se dá nastavit v konfiguraci a přepíše nastavení proxy aplikace Internet Explorer. Tato hodnota musí být také nastavena `false` nebo nebyla nastavena adaptivní proxy, aby byla povolená.|  
  
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

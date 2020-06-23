---
title: Konfigurace proxy serveru
description: Přečtěte si, jak nakonfigurovat adaptivní a statické proxy servery. Konfigurace proxy řídí způsob, jakým proxy server zpracovává požadavky klienta na prostředky.
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
ms.openlocfilehash: 4d62f5736e9aa469be49d101e85851bc01b7c159
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141602"
---
# <a name="proxy-configuration"></a>Konfigurace proxy serveru
Proxy server zpracovává požadavky klienta na prostředky. Proxy může vrátit požadovaný prostředek ze své mezipaměti nebo odeslat požadavek na server, kde se nachází prostředek. Proxy mohou zlepšit výkon sítě snížením počtu požadavků odesílaných na vzdálené servery. Proxy servery je také možné použít k omezení přístupu k prostředkům.  
  
## <a name="adaptive-proxies"></a>Adaptivní proxy  
 V .NET Framework jsou proxy servery součástí dvou variant: adaptivní a statické. Adaptivní proxy servery upravují jejich nastavení při změně konfigurace sítě. Pokud třeba uživatel přenosného počítače spustí telefonické připojení k síti, adaptivní proxy tuto změnu rozpozná, zjistí a spustí nový konfigurační skript a patřičně upraví jeho nastavení.  
  
 Adaptivní proxy servery jsou nakonfigurovány pomocí konfiguračního skriptu (viz [Automatická detekce proxy serveru](automatic-proxy-detection.md)). Skript vygeneruje sadu aplikačních protokolů a proxy pro každý protokol.  
  
 Změny v síťovém prostředí můžou vyžadovat, aby systém používal novou sadu proxy serverů. Pokud dojde k výpadku síťového připojení nebo k inicializaci nového síťového připojení, musí systém zjistit příslušný zdroj konfiguračního skriptu v novém prostředí a spustit nový skript.  
  
 Můžete použít `usesystemdefault` atribut [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) prvku v konfiguračním souboru. `usesystemdefault`Atribut určuje, zda má být nastavení statického proxy serveru (adresa proxy serveru, seznam obcházení a obejití v místní síti) čteno z nastavení proxy serveru aplikace Internet Explorer pro uživatele. Pokud je tato hodnota nastavená na `true` , použijí se nastavení statického proxy serveru z Internet Exploreru. Pokud tato hodnota není `false` nastavená, může být nastavení statického proxy serveru zadáno v konfiguraci a přepíše nastavení proxy serveru aplikace Internet Explorer. Tato hodnota musí být také nastavená na `false` nebo není nastavená pro adaptivní proxy servery, které se mají povolit.  
  
 Následující příklad ukazuje typickou konfiguraci adaptivního proxy serveru.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Statické proxy servery  
 Statické proxy servery jsou obvykle konfigurovány explicitně aplikací nebo při vyvolání konfiguračního souboru aplikací nebo systémem. Statické proxy servery jsou užitečné v sítích, ve kterých se topologie mění zřídka, jako je stolní počítač připojený k podnikové síti.  
  
 Několik možností řídí fungování statického proxy serveru. Můžete zadat následující:  
  
- Adresa proxy serveru.  
  
- Určuje, zda má být proxy server pro místní adresy obejít.  
  
- Určuje, zda má být proxy server pro sadu adres vynechán.  
  
 V následující tabulce jsou uvedeny možnosti konfigurace pro statický proxy server.  
  
|Nastavení atributu, vlastnosti nebo konfiguračního souboru|Description|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` nebo <xref:System.Net.WebProxy.Address>|Adresa proxy serveru, který se má použít.|  
|`bypassonlocal` nebo <xref:System.Net.WebProxy.BypassProxyOnLocal>|Určuje, jestli se proxy server pro místní adresy nepoužívá.|  
|`bypasslist` nebo <xref:System.Net.WebProxy.BypassArrayList>|Popisuje, s regulárními výrazy, sada adres, které obcházejí proxy serveru.|  
|`usesystemdefault`|Určuje, jestli se má pro uživatele přečíst nastavení statického proxy serveru (adresa proxy serveru, seznam obcházení a obejití v místní síti). Pokud je tato hodnota nastavená na `true` , použijí se nastavení statického proxy serveru z Internet Exploreru. V .NET Framework 2,0 Pokud je tato hodnota nastavena na `true` , nastavení proxy serveru aplikace Internet Explorer nejsou přepsána jinými nastaveními proxy v konfiguračním souboru. V .NET Framework 1,1 lze nastavení proxy serveru aplikace Internet Explorer přepsat jinými nastaveními proxy v konfiguračním souboru.<br /><br /> Pokud tato hodnota není `false` nastavená, můžete v konfiguraci zadat nastavení statického proxy serveru a přepsat nastavení proxy serveru aplikace Internet Explorer. Tato hodnota musí být také nastavená na `false` nebo není nastavená pro adaptivní proxy servery, které se mají povolit.|  
  
 Následující příklad ukazuje typickou konfiguraci statického proxy serveru.  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="True"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [Automatické rozpoznávání proxy serveru](automatic-proxy-detection.md)

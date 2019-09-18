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
ms.openlocfilehash: 1fbfe25b90e810ff96924a2341582ff3f5ee5e5d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047361"
---
# <a name="proxy-configuration"></a>Konfigurace proxy serveru
Proxy server zpracovává požadavky klienta na prostředky. Proxy může vrátit požadovaný prostředek ze své mezipaměti nebo odeslat požadavek na server, kde se nachází prostředek. Proxy mohou zlepšit výkon sítě snížením počtu požadavků odesílaných na vzdálené servery. Proxy servery je také možné použít k omezení přístupu k prostředkům.  
  
## <a name="adaptive-proxies"></a>Adaptivní proxy  
 V .NET Framework jsou proxy servery součástí dvou variant: adaptivní a statické. Adaptivní proxy servery upravují jejich nastavení při změně konfigurace sítě. Pokud třeba uživatel přenosného počítače spustí telefonické připojení k síti, adaptivní proxy tuto změnu rozpozná, zjistí a spustí nový konfigurační skript a patřičně upraví jeho nastavení.  
  
 Adaptivní proxy servery jsou nakonfigurovány pomocí konfiguračního skriptu (viz [Automatická detekce proxy serveru](automatic-proxy-detection.md)). Skript vygeneruje sadu aplikačních protokolů a proxy pro každý protokol.  
  
 Změny v síťovém prostředí můžou vyžadovat, aby systém používal novou sadu proxy serverů. Pokud dojde k výpadku síťového připojení nebo k inicializaci nového síťového připojení, musí systém zjistit příslušný zdroj konfiguračního skriptu v novém prostředí a spustit nový skript.  
  
 Můžete použít `usesystemdefault` atribut [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) prvku v konfiguračním souboru. `usesystemdefault` Atribut určuje, zda má být nastavení statického proxy serveru (adresa proxy serveru, seznam obcházení a obejití v místní síti) čteno z nastavení proxy serveru aplikace Internet Explorer pro uživatele. Pokud je tato hodnota nastavená `true`na, použijí se nastavení statického proxy serveru z Internet Exploreru. Pokud tato hodnota `false` není nastavená, může být nastavení statického proxy serveru zadáno v konfiguraci a přepíše nastavení proxy serveru aplikace Internet Explorer. Tato hodnota musí být také nastavená `false` na nebo není nastavená pro adaptivní proxy servery, které se mají povolit.  
  
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
  
|Nastavení atributu, vlastnosti nebo konfiguračního souboru|Popis|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` Nebo <xref:System.Net.WebProxy.Address>|Adresa proxy serveru, který se má použít.|  
|`bypassonlocal` Nebo <xref:System.Net.WebProxy.BypassProxyOnLocal>|Určuje, jestli se proxy server pro místní adresy nepoužívá.|  
|`bypasslist` Nebo <xref:System.Net.WebProxy.BypassArrayList>|Popisuje, s regulárními výrazy, sada adres, které obcházejí proxy serveru.|  
|`usesystemdefault`|Určuje, jestli se má pro uživatele přečíst nastavení statického proxy serveru (adresa proxy serveru, seznam obcházení a obejití v místní síti). Pokud je tato hodnota nastavená `true`na, použijí se nastavení statického proxy serveru z Internet Exploreru. V .NET Framework 2,0 Pokud je tato hodnota nastavena na `true`, nastavení proxy serveru aplikace Internet Explorer nejsou přepsána jinými nastaveními proxy v konfiguračním souboru. V .NET Framework 1,1 lze nastavení proxy serveru aplikace Internet Explorer přepsat jinými nastaveními proxy v konfiguračním souboru.<br /><br /> Pokud tato hodnota `false` není nastavená, můžete v konfiguraci zadat nastavení statického proxy serveru a přepsat nastavení proxy serveru aplikace Internet Explorer. Tato hodnota musí být také nastavená `false` na nebo není nastavená pro adaptivní proxy servery, které se mají povolit.|  
  
 Následující příklad ukazuje typickou konfiguraci statického proxy serveru.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [Automatické rozpoznávání proxy serveru](automatic-proxy-detection.md)

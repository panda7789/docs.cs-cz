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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047361"
---
# <a name="proxy-configuration"></a>Konfigurace proxy serveru
Proxy server zpracovává požadavky klientů na prostředky. Proxy server může vrátit požadovaný prostředek ze své mezipaměti nebo předat požadavek na server, kde je prostředek umístěn. Servery proxy mohou zvýšit výkon sítě snížením počtu požadavků odeslaných na vzdálené servery. Proxy servery lze také omezit přístup k prostředkům.  
  
## <a name="adaptive-proxies"></a>Adaptivní proxy servery  
 V rozhraní .NET Framework jsou proxy servery ve dvou variantách: adaptivní a statické. Adaptivní proxy servery upravují nastavení při změně konfigurace sítě. Pokud například uživatel přenosného počítače spustí telefonické připojení k síti, adaptivní proxy server tuto změnu rozpozná, zjišťuje a spouští nový konfigurační skript a odpovídajícím způsobem upravuje jeho nastavení.  
  
 Adaptivní proxy servery jsou konfigurovány pomocí konfiguračního skriptu (viz [Automatická detekce proxy serveru).](automatic-proxy-detection.md) Skript generuje sadu aplikačních protokolů a proxy server pro každý protokol.  
  
 Změny v síťovém prostředí mohou vyžadovat, aby systém používal novou sadu proxy serverů. Pokud dojde k vypnutí síťového připojení nebo inicializováno nové síťové připojení, musí systém v novém prostředí zjistit příslušný zdroj konfiguračního skriptu a spustit nový skript.  
  
 Atribut [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) prvku `usesystemdefault` můžete použít v konfiguračním souboru. Atribut `usesystemdefault` určuje, zda má být nastavení statického serveru proxy (adresa proxy, seznam obejití a obejití v místním) přečteno z nastavení serveru proxy aplikace Internet Explorer pro uživatele. Pokud je tato `true`hodnota nastavena na hodnotu , bude použito statické nastavení proxy serveru z aplikace Internet Explorer. Pokud je `false` tato hodnota nastavena nebo není nastavena, lze v konfiguraci zadat nastavení statického serveru proxy a přepsat nastavení serveru proxy aplikace Internet Explorer. Tato hodnota musí být `false` také nastavena na nebo není nastavena pro adaptivní proxy servery, které mají být povoleny.  
  
 Následující příklad ukazuje typickou adaptivní konfiguraci proxy serveru.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Statické proxy servery  
 Statické proxy servery jsou obvykle konfigurovány explicitně aplikací nebo při vyvolání konfiguračního souboru aplikací nebo systémem. Statické proxy servery jsou užitečné v sítích, ve kterých se topologie mění zřídka, například v stolním počítači připojeném k podnikové síti.  
  
 Několik možností řídí fungování statického proxy serveru. Můžete zadat následující:  
  
- Adresa proxy serveru.  
  
- Určuje, zda má být proxy server vynechán pro místní adresy.  
  
- Určuje, zda má být proxy server vynechán pro sadu adres.  
  
 V následující tabulce jsou uvedeny možnosti konfigurace statického proxy serveru.  
  
|Nastavení atributu, vlastnosti nebo konfiguračního souboru|Popis|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` nebo <xref:System.Net.WebProxy.Address>|Adresa proxy použít.|  
|`bypassonlocal` nebo <xref:System.Net.WebProxy.BypassProxyOnLocal>|Určuje, zda je proxy server vynechán pro místní adresy.|  
|`bypasslist` nebo <xref:System.Net.WebProxy.BypassArrayList>|Popisuje pomocí regulárních výrazů sadu adres, které obcházejí proxy server.|  
|`usesystemdefault`|Určuje, zda má být nastavení statického serveru proxy (adresa proxy, seznam obejití a obejití v místním) čteno z nastavení serveru proxy aplikace Internet Explorer pro uživatele. Pokud je tato `true`hodnota nastavena na hodnotu , bude použito statické nastavení proxy serveru z aplikace Internet Explorer. V rozhraní .NET Framework 2.0, `true`pokud je tato hodnota nastavena na , nejsou nastavení serveru proxy aplikace Internet Explorer přepsána jinými nastaveními serveru proxy v konfiguračním souboru. V rozhraní .NET Framework 1.1 lze přepsáno nastavení mno žláby proxy aplikace Internet Explorer jinými nastaveními serveru proxy v konfiguračním souboru.<br /><br /> Pokud je `false` tato hodnota nastavena nebo není nastavena, lze v konfiguraci zadat nastavení statického serveru proxy a přepsat nastavení serveru proxy aplikace Internet Explorer. Tato hodnota musí být `false` také nastavena na nebo není nastavena pro adaptivní proxy servery, které mají být povoleny.|  
  
 Následující příklad ukazuje typickou statickou konfiguraci proxy serveru.  
  
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

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [Automatické rozpoznávání proxy serveru](automatic-proxy-detection.md)

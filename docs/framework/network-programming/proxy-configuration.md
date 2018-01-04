---
title: Konfigurace proxy serveru
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 41f7cfe76acfb4b6bbf66207685935c190a51901
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="proxy-configuration"></a>Konfigurace proxy serveru
Proxy server zpracovává požadavky na klienta pro prostředky. Proxy server můžete vrátit požadovaný prostředek ze své mezipaměti nebo předat požadavek na server, kde je umístěn daný prostředek. Proxy může zlepšit výkon sítě snížením počtu požadavky odeslané na vzdálených serverech. Proxy lze také omezit přístup k prostředkům.  
  
## <a name="adaptive-proxies"></a>Adaptivní proxy  
 V rozhraní .NET Framework, proxy servery existují ve dvou variantách: Adaptivní a statické. Adaptivní proxy úprava jejich nastavení, když se změny v konfiguraci sítě. Například pokud uživatel přenosný počítač spustí telefonické připojení sítě, adaptivní proxy by rozpoznat tuto změnu, zjistit a spusťte nový skript pro konfiguraci a jeho nastavení, odpovídajícím způsobem.  
  
 Adaptivní proxy se nakonfiguroval konfigurační skript (viz [automatické zjišťování Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)). Tento skript generuje sadu protokoly aplikací a proxy serveru pro každý protokol.  
  
 Několik možností, jak řídit, jak je konfigurační skript spustit. Můžete zadat následující:  
  
-   Jak často je konfigurační skript stáhnout a spustit.  
  
-   Jak dlouho chcete čekat na skript, který chcete stáhnout.  
  
-   Které přihlašovací údaje systému má použít pro přístup k proxy serveru.  
  
-   Které přihlašovací údaje systému měli používat ke stažení konfigurační skript.  
  
 Změny v prostředí sítě můžou vyžadovat, že systém použít novou sadu serverů proxy. Pokud připojení k síti ocitne mimo provoz nebo je inicializován nového připojení k síti, systém musí vyhledat příslušný zdroj konfigurační skript v nové verzi prostředí a spusťte nový skript.  
  
 V následující tabulce jsou uvedeny možnosti konfigurace pro adaptivní proxy serveru.  
  
|Atribut, vlastnost nebo konfigurace nastavení souboru|Popis|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|Uplynulý čas v sekundách mezi stahováním skriptu.|  
|`scriptDownloadTimeout`|Doba čekání (v sekundách) pro skript, který chcete stáhnout.|  
|`useDefaultCredentials`nebo<xref:System.Net.WebProxy.UseDefaultCredentials>|Určuje, zda systém používá výchozí síťové přihlašovací údaje pro přístup k proxy serveru.|  
|`useDefaultCredentialForScriptDownload`|Určuje, zda systém použije výchozí přihlašovací údaje pro síť se stáhnout skript konfigurace.|  
|`usesystemdefaults`|Určuje, zda nastavení statické proxy (adresa proxy seznam obcházení a nepoužívat místního) byste si měli přečíst z nastavení proxy serveru aplikace Internet Explorer pro uživatele. Pokud tato hodnota nastavena na hodnotu "true" a pak nastavení statické proxy z Internet Exploreru se použije.<br /><br /> Pokud je tato hodnota "false" nebo není sada, potom nastavení statické proxy může být zadaný v konfiguraci a přepíše nastavení proxy serveru aplikace Internet Explorer. Tato hodnota musí také na hodnotu "false" nebo není nastavená adaptivní proxy, aby byl povolen.|  
  
 Následující příklad ukazuje konfiguraci typické adaptivní proxy.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy  scriptDownloadInterval="600"  
              scriptDownloadTimeout="30"  
              useDefaultCredentials="true"  
              usesystemdefaults="true"  
      />  
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
|`proxyaddress`nebo<xref:System.Net.WebProxy.Address>|Adresa proxy serveru používat.|  
|`bypassonlocal`nebo<xref:System.Net.WebProxy.BypassProxyOnLocal>|Určuje, zda je vynechá proxy pro místní adresy.|  
|`bypasslist`nebo<xref:System.Net.WebProxy.BypassArrayList>|Popisuje sadu adres, které používat proxy server s použitím regulárních výrazů.|  
|`usesystemdefaults`|Určuje, zda nastavení statické proxy (adresa proxy seznam obcházení a nepoužívat místního) byste si měli přečíst z nastavení proxy serveru aplikace Internet Explorer pro uživatele. Pokud tato hodnota nastavena na hodnotu "true" a pak nastavení statické proxy z Internet Exploreru se použije. V rozhraní .NET Framework 2.0 když tato hodnota nastavena na hodnotu "PRAVDA", ostatní nastavení proxy serveru v konfiguračním souboru nejsou přepsat nastavení proxy serveru aplikace Internet Explorer. V rozhraní .NET Framework 1.1 je možné přepsat nastavení proxy serveru aplikace Internet Explorer Další nastavení proxy serveru v konfiguračním souboru.<br /><br /> Pokud je tato hodnota "false" nebo není sada, potom nastavení statické proxy může být zadaný v konfiguraci a přepíše nastavení proxy serveru aplikace Internet Explorer. Tato hodnota musí také na hodnotu "false" nebo není nastavená adaptivní proxy, aby byl povolen.|  
  
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

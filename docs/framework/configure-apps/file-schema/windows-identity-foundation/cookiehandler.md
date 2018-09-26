---
title: '&lt;z toho důvodu&gt;'
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 99bf6edb4e4f631eba292990c65c1f0c8553d8c0
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084693"
---
# <a name="ltcookiehandlergt"></a>&lt;z toho důvodu&gt;
Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , který <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) používá ke čtení a zápis souborů cookie.  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<z toho důvodu >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Určuje základní název pro všechny soubory cookie zapsána. Výchozí hodnota je "FedAuth".|  
|cesta|Určuje hodnotu cesty pro všechny soubory cookie zapsána. Výchozí hodnota je "HttpRuntime.AppDomainAppVirtualPath".|  
|režim|Jeden z <xref:System.IdentityModel.Services.CookieHandlerMode> hodnoty, které určuje typ obslužné rutiny souborů cookie používá SAM. Slouží následující hodnoty:<br /><br /> -"Výchozí" – stejně jako "Bloku dat".<br />-"Blokové" – používá instanci <xref:System.IdentityModel.Services.ChunkedCookieHandler> třídy. Tato obslužná rutina souboru cookie zajistí, že jednotlivé soubory cookie nepřekračují nastavení maximální velikosti. Provádí se to tak potenciálně "bloků" jeden logický soubor cookie do několika souborů cookie v přenosu.<br />– "Vlastní" – používá instanci vlastní třídy odvozené od <xref:System.IdentityModel.Services.CookieHandler>. Odvozené třídy odkazuje `<customCookieHandler>` podřízený element.<br /><br /> Výchozí hodnota je "Výchozí".|  
|persistentSessionLifetime|Určuje dobu životnosti trvalých relací. Pokud je nula, se vždycky použijí přechodné relace. Výchozí hodnota je "0:0:0", který určuje přechodné relace. Maximální hodnota je "365:0:0", který určuje relaci 365 dnů. Hodnota se musí nastavit podle následující omezení: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, kde levou krajní hodnotu určuje dny, hodiny určuje střední hodnotu (pokud existuje) a pravou krajní hodnotu (pokud existuje) určuje minut.|  
|Vlastnost RequireSsl|Určuje, zda je příznak "Zabezpečení" vygenerován pro všechny soubory cookie zapsána. Pokud je tato hodnota nastavena, soubory cookie relace přihlášení budou k dispozici pouze prostřednictvím protokolu HTTPS. Výchozí hodnota je "true".|  
|hideFromScript|Určuje, zda je příznak "HttpOnly" vygenerován pro všechny soubory cookie zapsána. V některých webových prohlížečích případném dalším sdílení dodržovat tento příznak udržováním skriptu na straně klienta v přístupu k hodnotě souboru cookie. Výchozí hodnota je "true".|  
|doména|Hodnota domény pro všechny soubory cookie zapsána. Výchozí hodnota je "".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chunkedCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Tento element může být pouze přítomen, pokud `mode` atribut `<cookieHandler>` elementu je "Výchozí" nebo "Rozdělený do bloků dat".|  
|[\<customCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|Nastaví typ obslužné rutiny vlastních souborů cookie. Tento element musí být k dispozici Pokud `mode` atribut `<cookieHandler>` elementu je "Vlastní". Nemůže být k dispozici pro všechny ostatní hodnoty `mode` atribut. Vlastní typ musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.IdentityModel.Services.CookieHandler> Zodpovídá za čtení a zápis nezpracovaných souborů cookie na HTTP úroveň protokolu. Můžete nakonfigurovat buď <xref:System.IdentityModel.Services.ChunkedCookieHandler> nebo vlastní soubor cookie obslužnou rutinu odvozené z <xref:System.IdentityModel.Services.CookieHandler> třídy.  
  
 Pokud chcete nakonfigurovat obslužná rutina bloku dat souboru cookie, nastavte atribut mode "Bloku dat" nebo "Výchozí". Výchozí velikost bloku je 2 000 bajtů, ale můžete volitelně zadat velikost bloku dat různých zahrnutím `<chunkedCookieHandler>` podřízený element.  
  
 Pokud chcete nakonfigurovat vlastní soubor cookie obslužnou rutinu, nastavte atribut mode na "Vlastní". Musíte zadat také `<customCookieHandler>` podřízený prvek, který odkazuje na typ vlastní obslužnou rutinu.  
  
 `<cookieHandler>` Prvek je reprezentován <xref:System.IdentityModel.Services.CookieHandlerElement> třídy. Obslužná rutina souboru cookie, který byl zadán v konfiguraci je k dispozici <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> vlastnost <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> nastavena na objekt <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
 Zobrazí se následující XML `<cookieHandler>` elementu. V tomto příkladu protože `mode` atribut není zadán, použije výchozí soubor cookie obslužnou rutinu SAM. Toto je instance <xref:System.IdentityModel.Services.ChunkedCookieHandler> třídy. Vzhledem k tomu, `<chunkedCookieHandler>` podřízený prvek není zadán, použije se výchozí velikost bloku. Protokol HTTPS se nevyžaduje, protože `requireSsl` atribut je nastaven `false`.  
  
> [!WARNING]
>  V tomto příkladu není HTTPS vyžadovaných k zápisu souborů cookie relace. Je to proto, `requireSsl` atribut na `<cookieHandler>` prvek je nastaven na `false`. Toto nastavení se nedoporučuje pro většinu produkčních prostředí, protože to může představovat bezpečnostní riziko.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>

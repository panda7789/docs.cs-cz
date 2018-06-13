---
title: '&lt;cookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7fcdf1e89c3b68daa36ee80fe7234737c61a5a3c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758136"
---
# <a name="ltcookiehandlergt"></a>&lt;cookieHandler&gt;
Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) používá ke čtení a zápis souborů cookie.  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<cookieHandler >  
  
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
|režim|Jeden z <xref:System.IdentityModel.Services.CookieHandlerMode> hodnoty, které určuje typ obslužné rutiny souborů cookie používá správce zabezpečení účtů. Mohou být použity následující hodnoty:<br /><br /> -"Výchozí" – stejný jako "Chunked".<br />-"Blokové" – používá instanci <xref:System.IdentityModel.Services.ChunkedCookieHandler> třídy. Tato obslužná rutina souboru cookie zajistí, že jednotlivé soubory cookie nepřekračují nastavit maximální velikost. Se dosahuje tak, že potenciálně "rozdělování" jednoho logického souboru cookie do několika souborů cookie na přenosu.<br />– "Vlastní" – používá instanci vlastní třídy odvozené od <xref:System.IdentityModel.Services.CookieHandler>. Odvozené třídy odkazuje `<customCookieHandler>` podřízený element.<br /><br /> Výchozí hodnota je "Default".|  
|persistentSessionLifetime|Určuje životnost trvalé relací. Pokud nula, se vždycky použijí přechodný relací. Výchozí hodnota je "0:0:0", který určuje přechodný relace. Maximální hodnota je "365:0:0", který určuje relaci 365 dnů. Hodnota musí být zadán podle následující omezení: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, kde levou krajní hodnotu určuje počet dnů, hodin určuje střední hodnota (pokud existuje) a pravou krajní hodnotu (pokud existuje) určuje počet minut.|  
|requireSsl|Určuje, zda je příznak "Zabezpečeného" vygenerované pro všechny soubory cookie zapsána. Pokud je tato hodnota nastavená, soubory cookie relace přihlášení bude k dispozici pouze prostřednictvím protokolu HTTPS. Výchozí hodnota je "true".|  
|hideFromScript|Určuje, zda je pro všechny soubory cookie zapsána vygenerované příznak "HttpOnly". Některé webové prohlížeče respektovat tento příznak udržováním klientský skript v přístupu k hodnotě souboru cookie. Výchozí hodnota je "true".|  
|doména|Hodnota domény pro všechny soubory cookie zapsána. Výchozí hodnota je "".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chunkedCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|Nakonfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Tento element může být pouze existuje-li `mode` atribut `<cookieHandler>` element je "Výchozí" nebo "Blokové".|  
|[\<customCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|Nastaví typ obslužné rutiny vlastní soubor cookie. Tento element musí být přítomen Pokud `mode` atribut `<cookieHandler>` element je "Vlastní". Nemůže být k dispozici pro všechny ostatní hodnoty `mode` atribut. Vlastní typ musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.IdentityModel.Services.CookieHandler> Zodpovídá za čtení a zápis nezpracované soubory cookie na HTTP úroveň protokolu. Můžete nakonfigurovat buď <xref:System.IdentityModel.Services.ChunkedCookieHandler> nebo obslužná rutina vlastní soubor cookie odvozené od <xref:System.IdentityModel.Services.CookieHandler> třídy.  
  
 Pokud chcete konfigurovat soubor cookie rozdělený obslužná rutina, nastavte atribut režimu "Chunked" nebo "Výchozí". Výchozí velikost bloku je 2000 bajtů, ale může volitelně zadejte velikost bloku různých zahrnutím `<chunkedCookieHandler>` podřízený element.  
  
 Pokud chcete konfigurovat vlastní soubor cookie obslužnou rutinu, nastavte atribut režimu k "Vlastní". Musíte zadat také `<customCookieHandler>` podřízený element, který odkazuje na typ vaší vlastní obslužné rutiny.  
  
 `<cookieHandler>` Element je reprezentována <xref:System.IdentityModel.Services.CookieHandlerElement> třídy. Soubor cookie obslužnou rutinu, která byla zadaná v konfiguraci je k dispozici z <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> vlastnost <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> nastavit u objektu <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následují XML `<cookieHandler>` elementu. V tomto příkladu protože `mode` atribut nezadá, použije výchozí soubor cookie obslužnou rutinu správce zabezpečení účtů. Toto je instance <xref:System.IdentityModel.Services.ChunkedCookieHandler> třídy. Protože `<chunkedCookieHandler>` podřízený element nezadáte, použije se výchozí velikost bloku. Protokol HTTPS se nevyžaduje, protože `requireSsl` nastavený atribut `false`.  
  
> [!WARNING]
>  V tomto příkladu není potřeba HTTPS zapisovat soubory cookie relace. Důvodem je, že `requireSsl` atributu u `<cookieHandler>` element je nastaven na hodnotu `false`. Toto nastavení se nedoporučuje pro většinu produkční prostředí, protože ho může představovat bezpečnostní riziko.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>

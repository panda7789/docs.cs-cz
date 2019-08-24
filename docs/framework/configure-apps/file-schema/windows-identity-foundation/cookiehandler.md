---
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 1c044f7346fabc77d7744f42c5bfd3d86d72402e
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988342"
---
# <a name="cookiehandler"></a>\<cookieHandler>
<xref:System.IdentityModel.Services.SessionAuthenticationModule> Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> , jak bude (SAM) používat ke čtení a zápisu souborů cookie.  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<cookieHandler>  
  
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
|name|Určuje základní název pro všechny zapsané soubory cookie. Výchozí hodnota je "FedAuth".|  
|cesta|Určuje hodnotu cesty pro všechny zapsané soubory cookie. Výchozí hodnota je "HttpRuntime. AppDomainAppVirtualPath".|  
|režim|Jedna z <xref:System.IdentityModel.Services.CookieHandlerMode> hodnot, která určuje druh obslužné rutiny souborů cookie, kterou používá Sam. Lze použít následující hodnoty:<br /><br /> -"Default" – totéž jako "blokování".<br />-"Bloked" – používá instanci <xref:System.IdentityModel.Services.ChunkedCookieHandler> třídy. Tato obslužná rutina souborů cookie zajišťuje, že individuální soubory cookie nepřekračují nastavenou maximální velikost. Tím to provede potenciálně "jeden logický soubor cookie" pomocí "bloků" na několik souborů cookie.<br />-"Custom" – používá instanci vlastní třídy odvozené z <xref:System.IdentityModel.Services.CookieHandler>. Na odvozenou třídu odkazuje `<customCookieHandler>` podřízený element.<br /><br /> Výchozí hodnota je "výchozí".|  
|persistentSessionLifetime|Určuje dobu života trvalých relací. Pokud je nula, přechodné relace se vždycky používají. Výchozí hodnota je "0:0:0", která určuje přechodnou relaci. Maximální hodnota je "365:0:0", která určuje relaci 365 dnů. Hodnota by měla být zadána v závislosti na následujících omezeních `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`:, kde hodnota vlevo určuje dny, střední hodnota (Pokud je k dispozici) Určuje hodiny a hodnota vpravo (Pokud je k dispozici) Určuje minuty.|  
|Vlastnost requireSSL|Určuje, zda je pro všechny zapsané soubory cookie vygenerován příznak "Secure". Pokud je tato hodnota nastavena, budou soubory cookie přihlašovacích relací k dispozici pouze prostřednictvím protokolu HTTPS. Výchozí hodnota je "true".|  
|hideFromScript|Určuje, zda je pro všechny zapsané soubory cookie vygenerován příznak "HttpOnly". Některé webové prohlížeče tento příznak dodržují tím, že budou mít skript na straně klienta přístup k hodnotě souboru cookie. Výchozí hodnota je "true".|  
|doména|Hodnota domény pro všechny zapsané soubory cookie. Výchozí hodnota je "".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chunkedCookieHandler>](chunkedcookiehandler.md)|Nakonfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Tento element může být k dispozici pouze `mode` v případě, `<cookieHandler>` že atribut elementu je "výchozí" nebo "v bloku".|  
|[\<customCookieHandler>](customcookiehandler.md)|Nastaví typ obslužné rutiny vlastního souboru cookie. Tento prvek musí být přítomen, je `mode` -li atribut `<cookieHandler>` elementu "Custom". Nemůže být k dispozici pro žádné jiné hodnoty `mode` atributu. Vlastní typ musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Obsahuje nastavení, která konfigurují <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> a (SAM).|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.IdentityModel.Services.CookieHandler> Zodpovídá za čtení a zápis nezpracovaných souborů cookie na úrovni protokolu HTTP. Můžete nakonfigurovat buď <xref:System.IdentityModel.Services.ChunkedCookieHandler> obslužnou rutinu nebo vlastní soubor cookie odvozený <xref:System.IdentityModel.Services.CookieHandler> z třídy.  
  
 Chcete-li nakonfigurovat obslužnou rutinu souborů cookie s proměnlivým blokem, nastavte atribut Mode na hodnotu "v bloku" nebo "default". Výchozí velikost bloku je 2000 bajtů, ale můžete volitelně zadat jinou velikost bloku zahrnutím `<chunkedCookieHandler>` podřízeného prvku.  
  
 Pokud chcete nakonfigurovat vlastní obslužnou rutinu souborů cookie, nastavte atribut Mode na Custom (vlastní). Musíte také zadat `<customCookieHandler>` podřízený element, který odkazuje na typ vlastní obslužné rutiny.  
  
 Element je reprezentován <xref:System.IdentityModel.Services.CookieHandlerElement>třídou. `<cookieHandler>` Obslužná rutina souborů cookie, která byla zadána v konfiguraci, <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> je k dispozici z vlastnosti <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objektu <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> nastavené u vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje `<cookieHandler>` element. V tomto příkladu, protože `mode` atribut není zadán, bude soubor Sam použit jako výchozí obslužná rutina souborů cookie. Toto je instance <xref:System.IdentityModel.Services.ChunkedCookieHandler> třídy. Vzhledem k tomu, že podřízenýelementnenízadán,budepoužitavýchozívelikostbloku.`<chunkedCookieHandler>` Protokol HTTPS nebude vyžadován, protože `requireSsl` je nastaven `false`atribut.  
  
> [!WARNING]
> V tomto příkladu není protokol HTTPS nutný k zápisu souborů cookie relace. Důvodem je `requireSsl` , že atribut `<cookieHandler>` prvku je nastaven na `false`hodnotu. Toto nastavení se nedoporučuje pro většinu produkčních prostředí, protože může představovat bezpečnostní riziko.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>

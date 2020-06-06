---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152501"
---
# \<system.identityModel.services>
Konfigurační oddíl pro ověřování pomocí protokolu WS-Federation.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Obsahuje nastavení, která konfigurují <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> moduly protokolu HTTP (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
 Žádné  
  
## <a name="remarks"></a>Poznámky  
 Přidejte `<system.identityModel.services>` oddíl do konfiguračního souboru aplikace a poskytněte tak nastavení pro Sam a WSFAM.  
  
> [!IMPORTANT]
> Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích v kódu jsou deklarace identity Manageru ( <xref:System.Security.Claims.ClaimsAuthorizationManager> ) a zásady, které se používají k rozhodování o autorizaci, konfigurovány prostřednictvím `<identityConfiguration>` elementu, který je implicitně nebo explicitně odkazován z `<federationConfiguration>` prvku v této části. Další informace naleznete v **poznámkách** pod [\<federationConfiguration>](federationconfiguration.md) prvkem.  
  
 `<system.identityModel.services>`Oddíl je reprezentován <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> třídou. Kolekce podřízených `<federationConfiguration>` prvků nakonfigurovaných v oddílu je reprezentována <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> třídou.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak přidat `<system.identityModel.services>` oddíl do konfiguračního souboru. Nejdřív musíte přidat deklarace oddílů pro `<system.identityModel.services>` oddíl i `<system.identityModel>` oddíly. (Když přidáte `<system.identityModel.services>` oddíl, měli byste také přidat deklaraci pro `<system.identityModel>` oddíl, abyste měli jistotu, že `<identityConfiguration>` v případě potřeby může modul runtime vytvořit výchozí oddíl.) Po přidání oddílu deklarace můžete nakonfigurovat nastavení federovaného ověřování pod `<system.identityModel.services>` prvkem.  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true"
        issuer="http://localhost:15839/wsFederationSTS/Issue"
        realm="http://localhost:50969/" reply="http://localhost:50969/"
        requireHttps="false"
        signOutReply="http://localhost:50969/SignedOutPage.html"
        signOutQueryString="Param1=value2&Param2=value2"
        persistentCookiesOnPassiveRedirects="true" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
  
</configuration>  
```

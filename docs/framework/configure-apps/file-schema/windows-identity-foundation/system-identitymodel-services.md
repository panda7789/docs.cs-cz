---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: e9488c0681e1a5f0fe94112a36b65ec73bf9fd09
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251811"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
Konfigurační oddíl pro ověřování pomocí protokolu WS-Federation.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp; **\<> System. identityModel. Services**  
  
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
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Obsahuje nastavení, která konfigurují <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> moduly protokolu HTTP (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> a (SAM).|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
 Žádné  
  
## <a name="remarks"></a>Poznámky  
 `<system.identityModel.services>` Přidejte oddíl do konfiguračního souboru aplikace a poskytněte tak nastavení pro Sam a WSFAM.  
  
> [!IMPORTANT]
> <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích ve vašem kódu se Správce autorizací deklarací identity<xref:System.Security.Claims.ClaimsAuthorizationManager>() a zásady, které se používají `<identityConfiguration>` k rozhodování o autorizaci, nakonfigurují prostřednictvím prvek, který je implicitně nebo explicitně odkazován z `<federationConfiguration>` prvku v této části. Další informace naleznete v **poznámkách** pod [ \<prvkem federationConfiguration >](federationconfiguration.md) .  
  
 Oddíl je reprezentován <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>třídou. `<system.identityModel.services>` Kolekce podřízených `<federationConfiguration>` prvků nakonfigurovaných v oddílu je reprezentována <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> třídou.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak přidat `<system.identityModel.services>` oddíl do konfiguračního souboru. Nejdřív musíte přidat deklarace oddílů pro `<system.identityModel.services>` oddíl `<system.identityModel>` i oddíly. (Když přidáte `<system.identityModel.services>` oddíl, měli byste také přidat deklaraci `<system.identityModel>` pro oddíl, abyste měli jistotu, že v případě `<identityConfiguration>` potřeby může modul runtime vytvořit výchozí oddíl.) Po přidání oddílu deklarace můžete nakonfigurovat nastavení federovaného ověřování pod `<system.identityModel.services>` prvkem.  
  
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

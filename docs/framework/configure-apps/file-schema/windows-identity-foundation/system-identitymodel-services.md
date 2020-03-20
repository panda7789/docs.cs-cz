---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152501"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
Konfigurační část pro ověřování pomocí protokolu WS-Federation.  
  
[**\<>konfigurace**](../configuration-element.md)\
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
 Žádný  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Obsahuje nastavení, která <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> konfigurují moduly HTTP (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
 Žádný  
  
## <a name="remarks"></a>Poznámky  
 Přidejte `<system.identityModel.services>` oddíl do konfiguračního souboru aplikace a zadejte nastavení pro sam a wsfam.  
  
> [!IMPORTANT]
> Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k poskytování řízení přístupu na základě<xref:System.Security.Claims.ClaimsAuthorizationManager>deklarací identity ve vašem kódu, správce `<identityConfiguration>` autorizace deklarací ( ) a `<federationConfiguration>` zásady, které se používají k rozhodování o autorizaci jsou konfigurovány prostřednictvím prvku, který je implicitně nebo explicitně odkazován z prvku v této části. Další informace naleznete v **části Poznámky** v části [ \<federationConfiguration>](federationconfiguration.md) element.  
  
 Oddíl `<system.identityModel.services>` je reprezentován <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> třídou. Kolekce podřízených `<federationConfiguration>` prvků nakonfigurovaných <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> v části je reprezentována třídou.  
  
## <a name="example"></a>Příklad  
 Následující jazyk XML ukazuje, `<system.identityModel.services>` jak přidat oddíl do konfiguračního souboru. Nejprve je nutné přidat deklarace oddílů `<system.identityModel.services>` pro oddíl i oddíly. `<system.identityModel>` (Když přidáte `<system.identityModel.services>` oddíl, měli byste také přidat `<system.identityModel>` deklaraci pro `<identityConfiguration>` oddíl, abyste zajistili, že v případě potřeby může být výchozí oddíl vytvořen za běhu.) Po přidání deklarací oddílu můžete nakonfigurovat federovaná `<system.identityModel.services>` nastavení ověřování pod elementem.  
  
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

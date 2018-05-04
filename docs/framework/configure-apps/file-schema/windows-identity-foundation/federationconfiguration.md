---
title: '&lt;federationConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 44014d620dcd03e055eb58b50a1428b8e1b41186
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltfederationconfigurationgt"></a>&lt;federationConfiguration&gt;
Nakonfiguruje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) při použití federovaného ověřování pomocí protokolu WS-Federation. Nakonfiguruje <xref:System.Security.Claims.ClaimsAuthorizationManager> při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k poskytování řízení přístupu založené na deklaracích identity.  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
  
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
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Název tohoto elementu konfigurace federace. Tento atribut především poskytuje bod rozšiřitelnosti pro budoucí protokoly. Volitelné.|  
|identityConfigurationName|Název konfiguračního oddílu identity zadané v [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu, který chcete použít. Pokud tento atribut nezadá, použije se výchozí identity konfigurační oddíl. Volitelné.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Konfiguruje soubor cookie obslužná rutina používá správce zabezpečení účtů. Volitelné.|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Nakonfiguruje certifikát, který se používá k šifrování a dešifrování tokenů. Volitelné.|  
|[\<wsFederation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|Nakonfiguruje ověřování modulu WS-Federation (WSFAM). Volitelné.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.identityModel.services >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|Konfigurační oddíl pro ověřování pomocí protokolu WS-Federation.|  
  
## <a name="remarks"></a>Poznámky  
 \<FederationConfiguration > element poskytuje nastavení ve dvou různých scénářích:  
  
-   Při použití protokolu WS-Federation pasivní webové aplikace, elementu obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM). Odkazuje také konfigurace identity, který se má použít ke konfiguraci obslužné rutiny tokenu zabezpečení, certifikáty a součásti jako Správce autorizací deklarace identity a Správce ověřování deklarací identity.  
  
-   Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k poskytování řízení přístupu na základě deklarace identity ve vašem kódu, element odkazuje konfigurace identity, který konfiguruje správce ověřování deklarací identity a zásadu, která se používá k zajištění autorizace rozhodnutí. To platí, i ve scénářích, které nejsou pasivní scénáře webového; například aplikace Windows Communication Foundation (WCF) nebo aplikaci, která není založené na webu. Pokud aplikace není pasivní webové aplikace [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) – element (a jeho podřízených elementů zásad, pokud existuje) konfigurace identity odkazuje `<federationConfiguration>` – element platí pouze nastavení. Všechny další se ignorují.  
  
 Modul runtime bez ohledu na to scénář, načte výchozí konfigurace federace. Chování je definován následujícím způsobem:  
  
1.  Pokud není žádná `<federationConfiguration>` element přítomen, modul runtime vytvoří konfigurace federace a naplní s výchozími hodnotami. Tato výchozí konfigurace federace bude odkazovat výchozí konfigurace identity.  
  
2.  Pokud jeden `<federationConfiguration>` element nachází, je výchozí konfigurace federace bez ohledu na to, jestli je s názvem nebo nepojmenované. Pokud jeho `identityConfiguration` ; je zadaný atribut konfigurace s názvem identity se odkazuje, jinak se odkazuje výchozí konfigurace identity.  
  
3.  Pokud nepojmenované `<federationConfiguration>` element nachází, je výchozí konfigurace federace. Pokud jeho `identityConfiguration` ; je zadaný atribut konfigurace s názvem identity se odkazuje, jinak se odkazuje výchozí konfigurace identity.  
  
4.  Pokud název více `<federationConfiguration>` prvky jsou přítomna a ne nepojmenované `<federationConfiguration>` element nachází, je vyvolána výjimka.  
  
 Obvykle jediným `<federationConfiguration>` je definován oddíl. Tato část je výchozí konfigurace federace. Můžete určit více jednoznačně názvem `<federationConfiguration>` elementy; ale v takovém případě Pokud chcete načíst konfiguraci federace než nepojmenované, je nutné zadat obslužnou rutinu pro. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> události a sadu <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost uvnitř obslužná rutina <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objekt inicializovat pomocí hodnoty z příslušné `<federationConfiguration>` element v konfiguračním souboru.  
  
 `<federationConfiguration>` Element je reprezentována <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> třídy. Samotný objekt konfigurace je reprezentována <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> třídy. Jediný <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance je nastavený na <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost a poskytuje federované konfigurace pro aplikaci.  
  
## <a name="example"></a>Příklad  
 Následují XML `<federationConfiguration>` element, který určuje nastavení pro WSFAM a určuje, že soubor cookie výchozí obslužnou rutinu (instance <xref:System.IdentityModel.Services.ChunkedCookieHandler> – třída) používat Správce zabezpečení účtů.  
  
> [!WARNING]
>  V tomto příkladu obslužná rutina souboru cookie ani WSFAM vyžadovaných pro použití protokolu HTTPS. Důvodem je, že `requireHttps` atributu u `<wsFederation>` elementu a `requireSsl` atributu u `<cookieHandlerElement>` jsou `false`. Tato nastavení nejsou doporučuje pro většinu provozní prostředí, neboť mohou představovat bezpečnostní riziko.  
  
```xml  
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
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>  
 [\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)

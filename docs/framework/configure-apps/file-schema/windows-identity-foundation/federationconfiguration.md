---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: 102aadaaa7d7780f1266e1abcea46f0fcf95671e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622554"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
Konfiguruje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM), používáte federované ověřování pomocí protokolu WS-Federation. Konfiguruje <xref:System.Security.Claims.ClaimsAuthorizationManager> při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k poskytování řízení přístupu na základě deklarací identity.  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
  
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
|name|Název tohoto elementu konfigurace federace. Tento atribut primárně poskytuje bod rozšiřitelnosti pro budoucí protokoly. Volitelné.|  
|identityConfigurationName|Název oddílu konfigurace identity, jak je uvedeno v [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek, který chcete použít. Pokud tento atribut není zadán, použije se výchozí identit konfigurační oddíl. Volitelné.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<cookieHandler>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Konfiguruje soubor cookie obslužná rutina používá SAM. Volitelné.|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Nakonfiguruje certifikát používaný k šifrování a dešifrování tokenů. Volitelné.|  
|[\<wsFederation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|Nakonfiguruje ověřovací modul WS-Federation (WSFAM). Volitelné.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|Konfigurační oddíl pro ověřování pomocí protokolu WS-Federation.|  
  
## <a name="remarks"></a>Poznámky  
 \<FederationConfiguration > element obsahuje nastavení na dvou různých scénářů:  
  
- Při použití WS-Federation passive webové aplikace, element obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM). Odkazy taky konfigurace identity, který se má použít ke konfiguraci obslužné rutiny tokenů zabezpečení a certifikátů a komponenty, jako jsou Správce autorizace deklarací identity a Správce ověřování deklarací identity.  
  
- Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k poskytování řízení přístupu na základě deklarací identity ve vašem kódu, odkazuje na element konfigurace identity, který nakonfiguruje Správce autorizací deklarace identity a zásadu, která se využívá k Prognózování autorizace rozhodnutí. To platí dokonce i ve scénářích, které nejsou pasivní Web scénářích. například aplikace Windows Communication Foundation (WCF) nebo aplikaci, která není založena na Web. Pokud aplikace není pasivní webové aplikace [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) – element (a jeho podřízených elementů zásad, pokud jsou k dispozici) z konfigurace identity odkazuje `<federationConfiguration>` – element platí pouze nastavení. Případné další se ignorují.  
  
 Modul runtime bez ohledu na scénář, načte výchozí konfigurace federace. Chování je definovaná následujícím způsobem:  
  
1. Pokud není žádný `<federationConfiguration>` element je k dispozici, modul runtime vytvoří konfigurace federace a naplní se výchozími hodnotami. Výchozí konfigurace federace bude odkazovat na výchozí konfigurace identity.  
  
2. Pokud jeden `<federationConfiguration>` element je k dispozici, je výchozí konfigurace federace bez ohledu na to, zda je název nebo nepojmenované. Pokud jeho `identityConfiguration` zadán atribut konfigurace identity s názvem odkazuje; v opačném případě se odkazuje výchozí konfigurace identity.  
  
3. Pokud nepojmenované `<federationConfiguration>` element je k dispozici, je výchozí konfigurace federace. Pokud jeho `identityConfiguration` zadán atribut konfigurace identity s názvem odkazuje; v opačném případě se odkazuje výchozí konfigurace identity.  
  
4. Pokud název více `<federationConfiguration>` prvky jsou k dispozici a žádné nepojmenované `<federationConfiguration>` element je k dispozici, je vyvolána výjimka.  
  
 Obvykle pouze jeden `<federationConfiguration>` je definován oddíl. Tato část je výchozí konfigurace federace. Můžete zadat více jedinečně pojmenovaná `<federationConfiguration>` prvky, ale v takovém případě Pokud chcete načíst konfiguraci federace, než na kterém nepojmenované, je nutné zadat obslužnou rutinu pro. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> události a nastavte <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> vlastnosti uvnitř obslužné rutiny <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objekt je inicializován s hodnotami z příslušné `<federationConfiguration>` element v konfiguračním souboru.  
  
 `<federationConfiguration>` Prvek je reprezentován <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> třídy. Samotný objekt konfigurace je reprezentována <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> třídy. Jediný <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance je nastavena na <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost a poskytuje federované konfiguraci pro danou aplikaci.  
  
## <a name="example"></a>Příklad  
 Následující XML ukazuje `<federationConfiguration>` element, který určuje nastavení WSFAM a určuje, že soubor cookie obslužnou rutinu výchozí (instance <xref:System.IdentityModel.Services.ChunkedCookieHandler> třídy) využívat SAM.  
  
> [!WARNING]
>  V tomto příkladu obslužné rutiny souborů cookie ani WSFAM vyžadovaných pro použití protokolu HTTPS. Důvodem je, že `requireHttps` atribut na `<wsFederation>` elementu a `requireSsl` atribut na `<cookieHandlerElement>` jsou `false`. Tato nastavení se nedoporučuje pro většinu produkčních prostředích, jako, může představovat bezpečnostní riziko.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)

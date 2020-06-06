---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152733"
---
# \<federationConfiguration>
Nakonfiguruje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) při použití federovaného ověřování prostřednictvím protokolu WS-Federation. Konfiguruje <xref:System.Security.Claims.ClaimsAuthorizationManager> při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
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
|name|Název tohoto elementu konfigurace federace Tento atribut primárně poskytuje bod rozšiřitelnosti pro budoucí protokoly. Nepovinný parametr.|  
|identityConfigurationName|Název oddílu konfigurace identity, jak je zadaný v [\<identityConfiguration>](identityconfiguration.md) elementu, který se má použít. Pokud tento atribut nezadáte, použije se výchozí oddíl konfigurace identity. Nepovinný parametr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Konfiguruje popisovač souboru cookie používaný serverem SAM. Nepovinný parametr.|  
|[\<serviceCertificate>](servicecertificate.md)|Nakonfiguruje certifikát, který se používá k šifrování a dešifrování tokenů. Nepovinný parametr.|  
|[\<wsFederation>](wsfederation.md)|Konfiguruje modul WS-Federation Authentication (WSFAM). Nepovinný parametr.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|Konfigurační oddíl pro ověřování pomocí protokolu WS-Federation.|  
  
## <a name="remarks"></a>Poznámky  
 \<federationConfiguration>Element poskytuje nastavení ve dvou různých scénářích:  
  
- Při použití WS-Federation v pasivní webové aplikaci obsahuje element nastavení, které konfiguruje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM). Také odkazuje na konfiguraci identity, která se má použít ke konfiguraci obslužných rutin a certifikátů tokenů zabezpečení a součástí, jako je Správce autorizací deklarací identity a Správce ověřování deklarací identity.  
  
- Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích ve vašem kódu element odkazuje na konfiguraci identity, která konfiguruje správce autorizací deklarací identity a zásadu, která se používá k rozhodování o autorizaci. To platí i ve scénářích, které nejsou pasivními webovými scénáři; například aplikace Windows Communication Foundation (WCF) nebo aplikace, které nejsou založené na webu. Pokud aplikace není pasivní webovou aplikací, použije se pro [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) ni element (a jeho podřízené prvky zásad, pokud jsou k dispozici) konfigurace identity, na kterou se odkazuje `<federationConfiguration>` element, jenom nastavení. Všechny ostatní jsou ignorovány.  
  
 Bez ohledu na to, že modul runtime načte výchozí konfiguraci federace. Chování je definováno následujícím způsobem:  
  
1. Pokud není přítomen žádný `<federationConfiguration>` element, modul runtime vytvoří konfiguraci federace a naplní ji výchozími hodnotami. Tato výchozí konfigurace federace bude odkazovat na výchozí konfiguraci identity.  
  
2. Pokud `<federationConfiguration>` je přítomen jeden prvek, jedná se o výchozí konfiguraci federace bez ohledu na to, zda má název nebo není pojmenován. Je `identityConfiguration` -li zadán jeho atribut, je odkazováno na konfiguraci pojmenované identity. v opačném případě je odkazováno na výchozí konfiguraci identity.  
  
3. Pokud je přítomný nepojmenovaný `<federationConfiguration>` element, je výchozí konfigurace federace. Je `identityConfiguration` -li zadán jeho atribut, je odkazováno na konfiguraci pojmenované identity. v opačném případě je odkazováno na výchozí konfiguraci identity.  
  
4. Pokud je k dispozici více pojmenovaných `<federationConfiguration>` prvků a neexistuje žádný nepojmenovaný `<federationConfiguration>` element, je vyvolána výjimka.  
  
 Obvykle je definován pouze jeden `<federationConfiguration>` oddíl. Tato část je výchozí konfigurací federace. Můžete zadat více, jednoznačně pojmenovaných `<federationConfiguration>` prvků; v takovém případě, pokud chcete načíst konfiguraci federace jinou než s nepojmenovaným, je nutné zadat obslužnou rutinu pro. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>událost a nastavte <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost uvnitř obslužné rutiny na <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objekt inicializovaný s hodnotami z příslušného `<federationConfiguration>` elementu v konfiguračním souboru.  
  
 `<federationConfiguration>`Element je reprezentován <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> třídou. Samotný objekt konfigurace je reprezentován <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> třídou. <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>U vlastnosti je nastavena jedna instance <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> a pro aplikaci je zajištěna federované konfigurace.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje `<federationConfiguration>` prvek, který určuje nastavení pro WSFAM a určuje, že správce Sam používá výchozí obslužnou rutinu souborů cookie (instance <xref:System.IdentityModel.Services.ChunkedCookieHandler> třídy).  
  
> [!WARNING]
> V tomto příkladu není k použití protokolu HTTPS nutná obslužná rutina souborů cookie ani WSFAM. Důvodem je, že `requireHttps` atribut na `<wsFederation>` elementu a `requireSsl` atribut v `<cookieHandlerElement>` jsou `false` . Tato nastavení se nedoporučují pro většinu produkčních prostředí, protože mohou představovat bezpečnostní riziko.  
  
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

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<identityConfiguration>](identityconfiguration.md)

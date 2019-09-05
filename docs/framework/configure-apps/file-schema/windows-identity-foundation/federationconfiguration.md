---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: 148b2f3e12fbfbf85b800f0ca7f5dc7dc1845d24
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252004"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
<xref:System.IdentityModel.Services.SessionAuthenticationModule> Nakonfiguruje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a (SAM) při použití federovaného ověřování prostřednictvím protokolu WS-Federation. Konfiguruje při použití třídy<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> nebo k poskytnutí řízení přístupu založeného na deklaracích. <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.Security.Claims.ClaimsAuthorizationManager>  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<federationConfiguration >**  
  
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
|name|Název tohoto elementu konfigurace federace Tento atribut primárně poskytuje bod rozšiřitelnosti pro budoucí protokoly. Volitelný parametr.|  
|identityConfigurationName|Název oddílu konfigurace identity, jak je zadaný v [ \<identityConfigurationm elementu >](identityconfiguration.md) , který se má použít. Pokud tento atribut nezadáte, použije se výchozí oddíl konfigurace identity. Volitelný parametr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Konfiguruje popisovač souboru cookie používaný serverem SAM. Volitelný parametr.|  
|[\<serviceCertificate>](servicecertificate.md)|Nakonfiguruje certifikát, který se používá k šifrování a dešifrování tokenů. Volitelný parametr.|  
|[\<wsFederation>](wsfederation.md)|Konfiguruje modul WS-Federation Authentication (WSFAM). Volitelný parametr.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|Konfigurační oddíl pro ověřování pomocí protokolu WS-Federation.|  
  
## <a name="remarks"></a>Poznámky  
 Element \<federationConfiguration > poskytuje nastavení ve dvou různých scénářích:  
  
- Při použití WS-Federation v pasivní webové aplikaci obsahuje element nastavení, které konfiguruje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> a (SAM). Také odkazuje na konfiguraci identity, která se má použít ke konfiguraci obslužných rutin a certifikátů tokenů zabezpečení a součástí, jako je Správce autorizací deklarací identity a Správce ověřování deklarací identity.  
  
- Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích ve vašem kódu element odkazuje na konfiguraci identity, která konfiguruje správce autorizací deklarací identity a zásadu, která se používá k provedení autorizace. nález. To platí i ve scénářích, které nejsou pasivními webovými scénáři; například aplikace Windows Communication Foundation (WCF) nebo aplikace, které nejsou založené na webu. Pokud aplikace není pasivní webovou aplikací, `<federationConfiguration>` [ \<](claimsauthorizationmanager.md) je jediným nastavením element claimsAuthorizationManager > (a jeho podřízené prvky zásad, jsou-li k dispozici) konfigurace identity, na kterou je odkazováno pomocí elementu. použitý. Všechny ostatní jsou ignorovány.  
  
 Bez ohledu na to, že modul runtime načte výchozí konfiguraci federace. Chování je definováno následujícím způsobem:  
  
1. Pokud není přítomen žádný `<federationConfiguration>` element, modul runtime vytvoří konfiguraci federace a naplní ji výchozími hodnotami. Tato výchozí konfigurace federace bude odkazovat na výchozí konfiguraci identity.  
  
2. Pokud je přítomen `<federationConfiguration>` jeden prvek, jedná se o výchozí konfiguraci federace bez ohledu na to, zda má název nebo není pojmenován. Je- `identityConfiguration` li zadán jeho atribut, je odkazováno na konfiguraci pojmenované identity. v opačném případě je odkazováno na výchozí konfiguraci identity.  
  
3. Pokud je přítomný nepojmenovaný `<federationConfiguration>` element, je výchozí konfigurace federace. Je- `identityConfiguration` li zadán jeho atribut, je odkazováno na konfiguraci pojmenované identity. v opačném případě je odkazováno na výchozí konfiguraci identity.  
  
4. Pokud je k `<federationConfiguration>` dispozici více pojmenovaných prvků a `<federationConfiguration>` neexistuje žádný nepojmenovaný element, je vyvolána výjimka.  
  
 Obvykle je definován pouze jeden `<federationConfiguration>` oddíl. Tato část je výchozí konfigurací federace. Můžete zadat více, jednoznačně pojmenovaných `<federationConfiguration>` prvků; v takovém případě, pokud chcete načíst konfiguraci federace jinou než s nepojmenovaným, je nutné zadat obslužnou rutinu pro. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>událost a nastavte <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost uvnitř obslužné rutiny <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> na objekt inicializovaný s hodnotami z příslušného `<federationConfiguration>` elementu v konfiguračním souboru.  
  
 Element je reprezentován <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>třídou. `<federationConfiguration>` Samotný objekt konfigurace je reprezentován <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> třídou. U vlastnosti je nastavena jedna <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance a pro aplikaci je zajištěna federované konfigurace. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje `<federationConfiguration>` prvek, který určuje nastavení pro WSFAM a určuje, že správce Sam používá výchozí obslužnou rutinu souborů cookie (instance <xref:System.IdentityModel.Services.ChunkedCookieHandler> třídy).  
  
> [!WARNING]
> V tomto příkladu není k použití protokolu HTTPS nutná obslužná rutina souborů cookie ani WSFAM. Důvodem je, že `requireHttps` atribut `<wsFederation>` na elementu `<cookieHandlerElement>` a `requireSsl` atribut v jsou `false`. Tato nastavení se nedoporučují pro většinu produkčních prostředí, protože mohou představovat bezpečnostní riziko.  
  
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
- [\<identityConfiguration>](identityconfiguration.md)

---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152733"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
Konfiguruje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) při použití federovaného ověřování prostřednictvím protokolu WS-Federation. Konfiguruje <xref:System.Security.Claims.ClaimsAuthorizationManager> <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> při <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> použití třídy nebo k poskytování řízení přístupu založeného na deklaracích identity.  
  
[**\<>konfigurace**](../configuration-element.md)\
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
|jméno|Název tohoto prvku konfigurace federace. Tento atribut poskytuje především bod rozšiřitelnosti pro budoucí protokoly. Nepovinný parametr.|  
|identityConfigurationName|Název oddílu konfigurace identity, jak je uvedeno v [ \<identityConfiguration>](identityconfiguration.md) prvek použít. Pokud tento atribut není zadán, použije se výchozí oddíl konfigurace identity. Nepovinný parametr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>cookieHandler](cookiehandler.md)|Konfiguruje obslužnou rutinu souboru cookie používanou sam. Nepovinný parametr.|  
|[\<serviceCertificate>](servicecertificate.md)|Konfiguruje certifikát, který se používá k šifrování a dešifrování tokenů. Nepovinný parametr.|  
|[\<wsFederation>](wsfederation.md)|Konfiguruje modul ověřování WS-Federation (WSFAM). Nepovinný parametr.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|Konfigurační část pro ověřování pomocí protokolu WS-Federation.|  
  
## <a name="remarks"></a>Poznámky  
 FederationConfiguration \<> element poskytuje nastavení ve dvou různých scénářích:  
  
- Při použití WS-Federation v pasivní webové aplikace, prvek <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> obsahuje nastavení, která <xref:System.IdentityModel.Services.SessionAuthenticationModule> konfigurují (WSFAM) a (SAM). Odkazuje také na konfiguraci identity, která se má použít ke konfiguraci obslužných rutin a certifikátů tokenů zabezpečení, a na součásti, jako je správce autorizací deklarací identity a správce ověřování deklarací identity.  
  
- Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k poskytování řízení přístupu na základě deklarací identity ve vašem kódu, element odkazuje na konfiguraci identity, která konfiguruje správce autorizace deklarací identity a zásady, které se používají k rozhodování o autorizaci. To platí i ve scénářích, které nejsou pasivní webové scénáře; Například aplikace WCF (Windows Communication Foundation) nebo aplikace, která není založena na webu. Pokud aplikace není pasivní webová aplikace, [ \<claimsAuthorizationManager>](claimsauthorizationmanager.md) prvek (a jeho podřízené prvky zásad, `<federationConfiguration>` pokud jsou k dispozici) konfigurace identity odkazuje prvek jsou pouze použitá nastavení. Všechny ostatní jsou ignorovány.  
  
 Bez ohledu na scénář načte runtime výchozí konfiguraci federace. Chování je definováno takto:  
  
1. Pokud není `<federationConfiguration>` k dispozici žádný prvek, runtime vytvoří konfiguraci federace a naplní ji výchozími hodnotami. Tato výchozí konfigurace federace bude odkazovat na výchozí konfiguraci identity.  
  
2. Pokud je `<federationConfiguration>` přítomen jeden prvek, je výchozí konfigurace federace bez ohledu na to, zda je pojmenován nebo nepojmenovaný. Pokud `identityConfiguration` je zadán jeho atribut, odkazuje se na konfiguraci pojmenované identity; v opačném případě je odkazováno na výchozí konfiguraci identity.  
  
3. Pokud je `<federationConfiguration>` přítomen nepojmenovaný prvek, jedná se o výchozí konfiguraci federace. Pokud `identityConfiguration` je zadán jeho atribut, odkazuje se na konfiguraci pojmenované identity; v opačném případě je odkazováno na výchozí konfiguraci identity.  
  
4. Pokud více `<federationConfiguration>` pojmenovaných prvků jsou `<federationConfiguration>` k dispozici a žádný nepojmenovaný prvek je k dispozici, je vyvolána výjimka.  
  
 Obvykle je definován `<federationConfiguration>` pouze jeden oddíl. Tato část je výchozí konfigurace federace. Můžete zadat více, jedinečně `<federationConfiguration>` pojmenované prvky; v tomto případě však pokud chcete načíst konfiguraci federace než nepojmenované, musíte zadat obslužnou rutinu pro. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>událost a <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> nastavte vlastnost uvnitř <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> obslužné rutiny `<federationConfiguration>` na objekt inicializovaný s hodnotami z příslušného prvku v konfiguračním souboru.  
  
 Prvek `<federationConfiguration>` je reprezentován <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> třídou. Samotný objekt konfigurace je <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> reprezentován třídou. Jedna <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance je nastavena <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> na vlastnost a poskytuje federované konfigurace pro aplikaci.  
  
## <a name="example"></a>Příklad  
 Následující jazyk XML `<federationConfiguration>` zobrazuje prvek, který určuje nastavení pro wsfam a určuje, <xref:System.IdentityModel.Services.ChunkedCookieHandler> že výchozí obslužná rutina souboru cookie (instance třídy) bude použita sam.  
  
> [!WARNING]
> V tomto příkladu není vyžadována obslužná rutina souboru cookie ani wsfam k použití protokolu HTTPS. Důvodem je, `requireHttps` že `<wsFederation>` atribut `requireSsl` na prvek `<cookieHandlerElement>` `false`a atribut na jsou . Tato nastavení se nedoporučuje pro většinu produkčních prostředí, protože mohou představovat bezpečnostní riziko.  
  
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
- [\<identityKonfigurace>](identityconfiguration.md)

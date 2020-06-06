---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 0fa8c574fd5663606cf081f1000a24884306edfe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251985"
---
# \<identityConfiguration>

Určuje nastavení identity na úrovni služby.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<identityConfiguration>**  

## <a name="syntax"></a>Syntaxe

```xml
<system.identityModel>
  <identityConfiguration
      name=xs:string
      saveBootstrapContext=xs:boolean>
      maximumClockSkew=TimeSpan >
  </identityConfiguration>
</system.identityModel>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|name|Název oddílu konfigurace identity Tento název můžete použít k odkazování na konkrétní konfigurační oddíl. Pokud `name` není zadán žádný atribut, oddíl definuje výchozí konfiguraci. Výchozí konfigurace se vždycky používá pro scénáře pasivní federace. Další informace naleznete v tématu [\<federationConfiguration>](federationconfiguration.md) elementu.|
|saveBootstrapContext|Určuje, zda mají být do tokenu relace zahrnuty tokeny Bootstrap. Hodnotu lze také nastavit pro kolekci obslužné rutiny tokenů nastavením `saveBootstrapContext` atributu u [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) elementu. Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.|
|maximumClockSkew|A <xref:System.TimeSpan> Určuje maximální povolený časový posun. Určuje maximální povolený časový posun při provádění operací závislých na čase, jako je například ověření doby platnosti přihlašovací relace. Výchozí hodnota je 5 minut, "00:05:00". Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v tématu [hodnoty TimeSpan](../windows-workflow-foundation/index.md). Maximální hodinový posun lze také nastavit pro kolekci obslužných rutin tokenů nastavením `maximumClockSkew` atributu u [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) elementu. Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.|

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Description|
|-------------|-----------------|
|[\<caches>](caches.md)|Registruje mezipaměti používané pro tokeny relací a detekci opětovného přehrání tokenu. Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení. Nepovinný parametr.|
|[\<certificateValidation>](certificatevalidation.md)|Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů. Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení. Nepovinný parametr.|
|[\<claimsAuthenticationManager>](claimsauthenticationmanager.md)|Zaregistruje Správce ověřování deklarací identity pro příchozí deklarace identity. Nepovinný parametr.|
|[\<claimsAuthorizationManager>](claimsauthorizationmanager.md)|Registruje Správce autorizací deklarací identity pro příchozí deklarace identity. Nepovinný parametr.|
|[\<claimTypeRequired>](claimtyperequired.md)|Určuje sadu požadovaných deklarací pro příchozí tokeny zabezpečení. Nepovinný parametr.|
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Určuje kolekci obslužných rutin tokenů zabezpečení. Je možné zadat nula nebo více kolekcí obslužných rutin tokenů zabezpečení. Nepovinný parametr.|
|[\<tokenReplayDetection>](tokenreplaydetection.md)|Umožňuje detekci opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů. Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení. Nepovinný parametr.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|[\<system.identityModel>](system-identitymodel.md)|Poskytuje konfiguraci pro povolení možností Windows Identity Foundation (WIF) v aplikacích.|

## <a name="remarks"></a>Poznámky

Je možné definovat více konfigurací identity, z nichž každý má jedinečný název. Chování je následující:

1. Pokud `<identityConfiguration>` není zadán žádný element. Výchozí konfigurace identity se vytvoří za běhu a naplní se výchozími hodnotami.

2. Je-li `<identityConfiguration>` zadán jeden prvek. Jedná se o výchozí konfiguraci identity. Nezáleží na tom, zda má název nebo není pojmenován.

3. Je-li `<identityConfiguration>` zadáno více prvků. Nepojmenovaný element určuje výchozí konfiguraci identity. Doporučuje se, když zadáte více `<identityConfiguration>` prvků, jeden z nich by měl být nepojmenovaný.

> [!WARNING]
> Pokud zadáte více `<identityConfiguration>` prvků, jeden z nich by měl být nepojmenovaný. Nepojmenovaný prvek bude výchozí konfigurace identity.

 Některá nastavení zadaná v `<identityConfiguration>` elementu lze přepsat nastavením v kolekci obslužných rutin tokenu zabezpečení nebo pomocí nastavení u jednotlivých obslužných rutin tokenů zabezpečení.

> [!IMPORTANT]
> Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích ve vašem kódu, konfigurace identity, na kterou se odkazuje element, `<federationConfiguration>` konfiguruje správce autorizací deklarací identity a zásadu, která se používá k rozhodování o autorizaci. To platí i ve scénářích, které nejsou pasivními webovými scénáři, například v aplikacích Windows Communication Foundation (WCF) nebo v aplikaci, která není založená na webu. Pokud aplikace není pasivní webovou aplikací, použije se pro daný [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) prvek (a jeho podřízené prvky zásad, pokud jsou k dispozici) odkazovaná konfigurace identity pouze nastavení. Všechna ostatní nastavení se ignorují. Další informace naleznete v tématu [\<federationConfiguration>](federationconfiguration.md) elementu.

`<identityConfiguration>`Element je reprezentován <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> třídou. Oddíl konfigurace identity je reprezentovaný <xref:System.IdentityModel.Configuration.IdentityConfiguration> třídou.

> [!IMPORTANT]
> Určení následujících prvků jako podřízených elementů `<identityConfiguration>` elementu je zastaralé, přestože chování je stále podporováno pro zpětnou kompatibilitu. Tyto prvky by měly být místo toho zadány pod [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) prvkem.
>
> - [\<audienceUris>](audienceuris.md)
> - [\<issuerNameRegistry>](issuernameregistry.md)
> - [\<issuerTokenResolver>](issuertokenresolver.md)
> - [\<serviceTokenResolver>](servicetokenresolver.md)

## <a name="example"></a>Příklad

Následující příklad vytvoří konfiguraci identity s názvem "alternateConfiguration". Konfigurace identity určuje výchozí nastavení.

```xml
<system.identityModel>
    <identityConfiguration name="alternateConfiguration"/>
</system.identityModel>
```

## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>

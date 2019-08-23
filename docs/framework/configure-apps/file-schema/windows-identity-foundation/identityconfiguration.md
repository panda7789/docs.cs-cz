---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 9f5e0c5ded3d750a1102492c7a506e6d5643b2d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942753"
---
# <a name="identityconfiguration"></a>\<identityConfiguration>

Určuje nastavení identity na úrovni služby.

 \<system.identityModel>\
\<identityConfiguration>

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
|name|Název oddílu konfigurace identity Tento název můžete použít k odkazování na konkrétní konfigurační oddíl. Pokud není `name` zadán žádný atribut, oddíl definuje výchozí konfiguraci. Výchozí konfigurace se vždycky používá pro scénáře pasivní federace. Další informace naleznete v [ \<tématu federationConfiguration >](federationconfiguration.md) element.|
|saveBootstrapContext|Určuje, zda mají být do tokenu relace zahrnuty tokeny Bootstrap. Hodnotu lze také nastavit pro kolekci obslužných rutin tokenů nastavením `saveBootstrapContext` atributu [ \<v elementu securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) . Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.|
|maximumClockSkew|A <xref:System.TimeSpan> určuje maximální povolený časový posun. Určuje maximální povolený časový posun při provádění operací závislých na čase, jako je například ověření doby platnosti přihlašovací relace. Výchozí hodnota je 5 minut, "00:05:00". Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v tématu [hodnoty TimeSpan](../windows-workflow-foundation/index.md). Maximální hodinový posun lze také nastavit pro kolekci obslužných rutin tokenů nastavením `maximumClockSkew` atributu [ \<u prvku securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) . Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.|

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<caches>](caches.md)|Registruje mezipaměti používané pro tokeny relací a detekci opětovného přehrání tokenu. Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení. Volitelný parametr.|
|[\<certificateValidation>](certificatevalidation.md)|Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů. Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení. Volitelný parametr.|
|[\<claimsAuthenticationManager>](claimsauthenticationmanager.md)|Zaregistruje Správce ověřování deklarací identity pro příchozí deklarace identity. Volitelný parametr.|
|[\<claimsAuthorizationManager>](claimsauthorizationmanager.md)|Registruje Správce autorizací deklarací identity pro příchozí deklarace identity. Volitelný parametr.|
|[\<claimTypeRequired>](claimtyperequired.md)|Určuje sadu požadovaných deklarací pro příchozí tokeny zabezpečení. Volitelný parametr.|
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Určuje kolekci obslužných rutin tokenů zabezpečení. Je možné zadat nula nebo více kolekcí obslužných rutin tokenů zabezpečení. Volitelný parametr.|
|[\<tokenReplayDetection>](tokenreplaydetection.md)|Umožňuje detekci opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů. Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení. Volitelný parametr.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<system.identityModel>](system-identitymodel.md)|Poskytuje konfiguraci pro povolení možností Windows Identity Foundation (WIF) v aplikacích.|

## <a name="remarks"></a>Poznámky

Je možné definovat více konfigurací identity, z nichž každý má jedinečný název. Chování je následující:

1. Pokud není `<identityConfiguration>` zadán žádný element. Výchozí konfigurace identity se vytvoří za běhu a naplní se výchozími hodnotami.

2. Je-li `<identityConfiguration>` zadán jeden prvek. Jedná se o výchozí konfiguraci identity. Nezáleží na tom, zda má název nebo není pojmenován.

3. Je- `<identityConfiguration>` li zadáno více prvků. Nepojmenovaný element určuje výchozí konfiguraci identity. Doporučuje se, když zadáte více `<identityConfiguration>` prvků, jeden z nich by měl být nepojmenovaný.

> [!WARNING]
> Pokud zadáte více `<identityConfiguration>` prvků, jeden z nich by měl být nepojmenovaný. Nepojmenovaný prvek bude výchozí konfigurace identity.

 Některá nastavení zadaná v `<identityConfiguration>` elementu lze přepsat nastavením v kolekci obslužných rutin tokenu zabezpečení nebo pomocí nastavení u jednotlivých obslužných rutin tokenů zabezpečení.

> [!IMPORTANT]
> Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích ve vašem kódu, konfigurace identity `<federationConfiguration>` , na kterou se odkazuje element, konfiguruje správce autorizací deklarací identity a zásadu, která se používá k provedení autorizační rozhodnutí. To platí i ve scénářích, které nejsou pasivními webovými scénáři, například v aplikacích Windows Communication Foundation (WCF) nebo v aplikaci, která není založená na webu. Pokud se nejedná o pasivní webovou aplikaci, [ \<](claimsauthorizationmanager.md) vztahují se pouze na element claimsAuthorizationManager > (a jeho podřízené prvky zásad, jsou-li k dispozici) odkazované konfigurace identity. Všechna ostatní nastavení se ignorují. Další informace naleznete v [ \<tématu federationConfiguration >](federationconfiguration.md) element.

Element je reprezentován <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>třídou. `<identityConfiguration>` Oddíl konfigurace identity je reprezentovaný <xref:System.IdentityModel.Configuration.IdentityConfiguration> třídou.

> [!IMPORTANT]
> Určení následujících prvků jako podřízených elementů `<identityConfiguration>` elementu je zastaralé, přestože chování je stále podporováno pro zpětnou kompatibilitu. Tyto prvky by měly být místo toho zadány pod [ \<prvkem securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) .
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

## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>

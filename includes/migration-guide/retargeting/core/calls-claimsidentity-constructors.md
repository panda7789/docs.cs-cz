---
ms.openlocfilehash: b88f7d4a17f885b687d99ab9410a56039e176080
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614429"
---
### <a name="calls-to-claimsidentity-constructors"></a>Volání konstruktorů hodnota ClaimsIdentity

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.6.2 dojde ke změně v tom, jak <xref:System.Security.Claims.ClaimsIdentity> konstruktory s <xref:System.Security.Principal.IIdentity?displayProperty=fullName> parametrem nastaví <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> vlastnost. Pokud <xref:System.Security.Principal.IIdentity?displayProperty=fullName> je argumentem <xref:System.Security.Claims.ClaimsIdentity> objekt a <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> vlastnost tohoto objektu není, je <xref:System.Security.Claims.ClaimsIdentity> `null` <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> vlastnost připojena pomocí <xref:System.Security.Claims.ClaimsIdentity.Clone> metody. V rozhraní Framework 4.6.1 a starších verzích <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> je vlastnost připojena jako stávající odkaz. Z důvodu této změny, počínaje .NET Framework 4.6.2, není <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> vlastnost nového <xref:System.Security.Claims.ClaimsIdentity> objektu shodná s <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> vlastností <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argumentu konstruktoru. V .NET Framework 4.6.1 a dřívějších verzích se rovná.

#### <a name="suggestion"></a>Návrh

Pokud je toto chování nežádoucí, můžete předchozí chování obnovit nastavením `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` přepínače v konfiguračním souboru aplikace na `true` . To vyžaduje, abyste do `<runtime>` oddílu web.config souboru přidali následující:

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />
  </runtime>
</configuration>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)>

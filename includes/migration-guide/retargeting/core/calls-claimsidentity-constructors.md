---
ms.openlocfilehash: c10d617e07ca2fa0239298d449d93cf833b83fce
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274927"
---
### <a name="calls-to-claimsidentity-constructors"></a>Volání konstruktorů ClaimsIdentity

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.6.2 dochází <xref:System.Security.Claims.ClaimsIdentity> ke změně způsobu, jakým konstruktory s parametrem <xref:System.Security.Principal.IIdentity?displayProperty=name> nastavují <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> vlastnost. Pokud <xref:System.Security.Principal.IIdentity?displayProperty=name> je argument <xref:System.Security.Claims.ClaimsIdentity> emitovaný <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> objektem <xref:System.Security.Claims.ClaimsIdentity> a <code>null</code>vlastnost <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> tohoto objektu není <xref:System.Security.Claims.ClaimsIdentity.Clone> , je vlastnost připojena pomocí metody. V rámci 4.6.1 a starší <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> verze vlastnost je připojen jako existující odkaz. Z důvodu této změny počínaje rozhraním .NET Framework <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 4.6.2 se vlastnost <xref:System.Security.Claims.ClaimsIdentity> <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> nového objektu nerovná vlastnosti argumentu konstruktoru. <xref:System.Security.Principal.IIdentity?displayProperty=name> V rozhraní .NET Framework 4.6.1 a starších verzích je stejná.|
|Návrh|Pokud je toto chování nežádoucí, můžete předchozí <code>Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity</code> chování obnovit nastavením <code>true</code>přepínače v konfiguračním souboru aplikace na . To vyžaduje, abyste do <code>&lt;runtime&gt;</code> části souboru web.config přidali následující:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)></li></ul>|

---
ms.openlocfilehash: 6dd7f2a2f6dec306940650beee58104b20788bdb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758334"
---
### <a name="calls-to-claimsidentity-constructors"></a>Volání konstruktorů ClaimsIdentity

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6.2, dojde ke změně v tom <xref:System.Security.Claims.ClaimsIdentity> konstruktory s <xref:System.Security.Principal.IIdentity?displayProperty=name> sada parametrů <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> vlastnost. Pokud <xref:System.Security.Principal.IIdentity?displayProperty=name> argument je <xref:System.Security.Claims.ClaimsIdentity> objektu a <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> vlastnost, která <xref:System.Security.Claims.ClaimsIdentity> objekt není <code>null</code>, <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> vlastnost je připojený prostřednictvím <xref:System.Security.Claims.ClaimsIdentity.Clone> metoda. V rozhraní Framework 4.6.1 a předchozími verzemi <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> vlastnost je připojen jako odkaz na existující. Z důvodu této změny, od verze rozhraní .NET Framework 4.6.2 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> vlastnosti nového <xref:System.Security.Claims.ClaimsIdentity> není roven objektu <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> vlastnost konstruktoru <xref:System.Security.Principal.IIdentity?displayProperty=name> argument. V rozhraní .NET Framework 4.6.1 a dřívějších verzích se rovná.|
|Doporučení|Pokud toto chování nežádoucí, předchozí chování můžete obnovit nastavením <code>Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity</code> přepínače v konfiguračním souboru aplikace do <code>true</code>. K tomu je potřeba přidat následující <code>&lt;runtime&gt;</code> části souboru web.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.6.2|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)?displayProperty=nameWithType></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})?displayProperty=nameWithType></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)?displayProperty=nameWithType></li></ul>|

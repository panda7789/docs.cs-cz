---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394378"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Poštolek: Prázdná sestava HTTPS byla odebrána.

Sestavení <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> bylo odebráno.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="reason-for-change"></a>Důvod změny

V ASP.NET Core 2.1 `Microsoft.AspNetCore.Server.Kestrel.Https` byl obsah <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>přesunut do . Tato změna byla provedena nerozdělitelné `[TypeForwardedTo]` způsobem pomocí atributů.

#### <a name="recommended-action"></a>Doporučená akce

- Knihovny odkazující `Microsoft.AspNetCore.Server.Kestrel.Https` na 2.0 by měly aktualizovat všechny ASP.NET základní závislosti na 2.1 nebo novější. V opačném případě se mohou přerušit při načtení do aplikace core 3.0 ASP.NET.
- Aplikace a knihovny zaměřené ASP.NET Core 2.1 a novější `Microsoft.AspNetCore.Server.Kestrel.Https` by měly odebrat všechny přímé odkazy na balíček NuGet.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

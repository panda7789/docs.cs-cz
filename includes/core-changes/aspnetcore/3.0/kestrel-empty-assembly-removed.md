---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394378"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel: bylo odebráno prázdné sestavení HTTPS.

Bylo odebráno sestavení <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName>.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="reason-for-change"></a>Důvod změny

V ASP.NET Core 2,1 byl obsah `Microsoft.AspNetCore.Server.Kestrel.Https` přesunut do <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>. Tato změna byla provedena neukončujícím způsobem pomocí atributů `[TypeForwardedTo]`.

#### <a name="recommended-action"></a>Doporučená akce

- Knihovny odkazující `Microsoft.AspNetCore.Server.Kestrel.Https` 2,0 by měly aktualizovat všechny závislosti ASP.NET Core na 2,1 nebo novější. V opačném případě mohou při načtení do aplikace ASP.NET Core 3,0 dojít k přerušení.
- Aplikace a knihovny cílené na ASP.NET Core 2,1 a novější by měly odebrat všechny přímé odkazy na balíček NuGet `Microsoft.AspNetCore.Server.Kestrel.Https`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

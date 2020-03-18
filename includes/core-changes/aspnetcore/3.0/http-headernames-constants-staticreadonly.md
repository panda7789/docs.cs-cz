---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901908"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: Konstanty HeaderNames se změnily na statické jen pro čtení.

Počínaje ASP.NET jádrem 3.0 Náhled <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> 5 `const` se `static readonly`pole v polích změnila z na .

Diskuse naleznete [v tématu dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Tato pole bývala `const`.

#### <a name="new-behavior"></a>Nové chování

Tato pole `static readonly`jsou nyní .

#### <a name="reason-for-change"></a>Důvod změny

Změna:

* Zabrání vkládání hodnot přes hranice sestavy, což umožňuje podle potřeby opravy hodnot.
* Umožňuje rychlejší kontroly rovnosti odkazů.

#### <a name="recommended-action"></a>Doporučená akce

Překompilovat proti 3.0. Zdrojový kód používající tato pole následujícími způsoby již nemůže:

* Jako atribut ový argument
* Jako `case` v `switch` prohlášení
* Při definování jiného`const`

Chcete-li obejít narušující změnu, přepněte na použití samodefinovaných konstant názvu záhlaví nebo literál řetězce.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->

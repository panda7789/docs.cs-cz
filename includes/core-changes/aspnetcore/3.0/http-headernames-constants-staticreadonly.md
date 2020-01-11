---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901908"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: HeaderNames konstanty se změnily na static jen pro čtení

Počínaje verzí ASP.NET Core 3,0 Preview 5 se pole v <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> změnila z `const` na `static readonly`.

Diskuzi najdete v tématu [dotnet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Tato pole se používají k `const`.

#### <a name="new-behavior"></a>Nové chování

Tato pole jsou nyní `static readonly`.

#### <a name="reason-for-change"></a>Důvod změny

Změna:

* Zabraňuje vložení hodnoty přes hranice sestavení, což umožňuje opravy hodnot podle potřeby.
* Umožňuje rychlejší kontroly rovnosti odkazů.

#### <a name="recommended-action"></a>Doporučená akce

Znovu kompilovat proti 3,0. Zdrojový kód pomocí těchto polí již neumožňuje následující akce:

* Jako argument atributu
* Jako `case` v příkazu `switch`
* Při definování jiného `const`

Chcete-li obejít zásadní změnu, přepněte na použití vlastní konstanty názvů hlaviček nebo řetězcových literálů.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->

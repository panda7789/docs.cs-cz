---
ms.openlocfilehash: e0d0a680915f14c2d33f1864ad5ad05aff3dde5f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394130"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: HeaderNames konstanty se změnily na static jen pro čtení

Počínaje verzí ASP.NET Core 3,0 Preview 5 se pole v <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> změnila z `const` na `static readonly`.

Diskuzi najdete v tématu [ASPNET/AspNetCore # 9514](https://github.com/aspnet/AspNetCore/issues/9514).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Tato pole se používají `const`.

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

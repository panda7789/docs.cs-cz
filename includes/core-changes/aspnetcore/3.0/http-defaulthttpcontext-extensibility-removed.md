---
ms.openlocfilehash: 7b5ae84d02b83a10a4b9e002fc2ed4ee0833b84c
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198407"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: rozšíření DefaultHttpContext bylo odebráno.

V rámci vylepšení výkonu ASP.NET Core 3,0 se rozšíření `DefaultHttpContext` odebralo. Třída je nyní `sealed`. Další informace najdete v tématu [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504).

Pokud testy jednotek používají `Mock<DefaultHttpContext>`, použijte místo toho `Mock<HttpContext>`.

Diskuzi najdete v tématu [ASPNET/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Třídy mohou odvozovat z `DefaultHttpContext`.

#### <a name="new-behavior"></a>Nové chování

Třídy nemůžou být odvozené od `DefaultHttpContext`.

#### <a name="reason-for-change"></a>Důvod změny

Toto rozšíření bylo zpočátku umožněno sdružování `HttpContext`, ale zavedlo zbytečné složitosti a narušilo další optimalizace.

#### <a name="recommended-action"></a>Doporučená akce

Pokud v testech jednotek používáte `Mock<DefaultHttpContext>`, začněte místo toho použít `Mock<HttpContext>`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->

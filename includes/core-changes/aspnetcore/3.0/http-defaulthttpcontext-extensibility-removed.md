---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290762"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: VýchozíhttpContext rozšiřitelnost odebrána

Jako součást ASP.NET vylepšení výkonu jádra 3.0 `DefaultHttpContext` byla zrušena rozšiřitelnost. Třída je `sealed`nyní . Další informace naleznete [v tématu dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).

Pokud jednotkové `Mock<DefaultHttpContext>`testy `Mock<HttpContext>` používají `new DefaultHttpContext()` , použijte nebo místo.

Diskuse naleznete [v tématu dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Třídy mohou `DefaultHttpContext`být odvozeny z .

#### <a name="new-behavior"></a>Nové chování

Třídy nelze odvodit z `DefaultHttpContext`.

#### <a name="reason-for-change"></a>Důvod změny

Rozšiřitelnost byla poskytnuta zpočátku umožnit `HttpContext`sdružování , ale zavedla zbytečnou složitost a bránila dalším optimalizacím.

#### <a name="recommended-action"></a>Doporučená akce

Pokud používáte `Mock<DefaultHttpContext>` v testování částí, `Mock<HttpContext>` začněte používat místo.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->

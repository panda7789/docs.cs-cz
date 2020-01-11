---
ms.openlocfilehash: 1b4b0aba3ea24682ae972bf283ac387692c83781
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902032"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: rozšíření DefaultHttpContext bylo odebráno.

V rámci vylepšení výkonu ASP.NET Core 3,0 se rozšíření `DefaultHttpContext` odebralo. Třída je nyní `sealed`. Další informace naleznete v tématu [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504).

Pokud testy jednotek používají `Mock<DefaultHttpContext>`, použijte místo toho `Mock<HttpContext>`.

Diskuzi najdete v tématu [dotnet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Třídy mohou odvozovat z `DefaultHttpContext`.

#### <a name="new-behavior"></a>Nové chování

Třídy nelze odvodit z `DefaultHttpContext`.

#### <a name="reason-for-change"></a>Důvod změny

Tato rozšiřitelná služba byla zpočátku k dispozici, aby umožňovala sdružování `HttpContext`, ale zavedla zbytečné složitosti a bránila jiným optimalizacím.

#### <a name="recommended-action"></a>Doporučená akce

Pokud používáte `Mock<DefaultHttpContext>` při testování částí, začněte místo toho používat `Mock<HttpContext>`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->

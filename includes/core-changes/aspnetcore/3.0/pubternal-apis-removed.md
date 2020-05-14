---
ms.openlocfilehash: 52b9caf2d5b3d44c0c6349501dafc371541fdd70
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396364"
---
### <a name="pubternal-apis-removed"></a>Odebrána rozhraní API "Pubternal"

Aby se lépe zachovala veřejná plocha rozhraní API ASP.NET Core, většina typů v `*.Internal` oborech názvů (označovaných jako :::no-loc text="\"pubternal\""::: rozhraní API) se stane skutečně interní. U členů v těchto oborech názvů nikdy nechtěla být podporovaná jako veřejná rozhraní API. Rozhraní API se můžou v podverzích poškodit a často se jedná o. Kód, který závisí na těchto rozhraních API, se při aktualizaci na ASP.NET Core 3,0 přeruší.

Další informace naleznete v tématech [dotnet/aspnetcore # 4932](https://github.com/dotnet/aspnetcore/issues/4932) a [dotnet/aspnetcore # 11312](https://github.com/dotnet/aspnetcore/issues/11312).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Ovlivněná rozhraní API jsou označená `public` modifikátorem přístupu a existují v `*.Internal` oborech názvů.

#### <a name="new-behavior"></a>Nové chování

Ovlivněná rozhraní API jsou označena modifikátorem přístupu [Internal (~/docs/CSharp/Language-Reference/Keywords/Internal.MD) a nemohou být nadále používána kódem mimo toto sestavení.

#### <a name="reason-for-change"></a>Důvod změny

Pokyny pro tato :::no-loc text="\"pubternal\""::: rozhraní API:

* Může se změnit bez předchozího upozornění.
* Nevedly se zásady rozhraní .NET, aby se zabránilo zásadním změnám.

Ukončení rozhraní API `public` (dokonce i v `*.Internal` oborech názvů) bylo matoucí pro zákazníky.

#### <a name="recommended-action"></a>Doporučená akce

Ukončete používání těchto :::no-loc text="\"pubternal\""::: rozhraní API. Pokud máte dotazy týkající se alternativních rozhraní API, otevřete problém v úložišti [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) .

Zvažte například následující kód pro ukládání požadavků HTTP do vyrovnávací paměti v projektu ASP.NET Core 2,2. `EnableRewind`Metoda rozšíření existuje v `Microsoft.AspNetCore.Http.Internal` oboru názvů.

```csharp
HttpContext.Request.EnableRewind();
```

V projektu ASP.NET Core 3,0 nahraďte `EnableRewind` volání voláním `EnableBuffering` metody rozšíření. Funkce ukládání požadavků do vyrovnávací paměti funguje stejně jako v minulosti. `EnableBuffering`volá `internal` rozhraní API Now.

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Všechna rozhraní API v `Microsoft.AspNetCore.*` `Microsoft.Extensions.*` oborech názvů a, která mají `Internal` segment v názvu oboru názvů. Příklad:

- `Microsoft.AspNetCore.Authentication.Internal`
- `Microsoft.AspNetCore.Builder.Internal`
- `Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `Microsoft.AspNetCore.DataProtection.Internal`
- `Microsoft.AspNetCore.Hosting.Internal`
- `Microsoft.AspNetCore.Http.Internal`
- `Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `Microsoft.AspNetCore.Mvc.Core.Internal`
- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `Microsoft.AspNetCore.Rewrite.Internal`
- `Microsoft.AspNetCore.Routing.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Internal`
- `N:Microsoft.AspNetCore.Builder.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Internal`
- `N:Microsoft.AspNetCore.Hosting.Internal`
- `N:Microsoft.AspNetCore.Http.Internal`
- `N:Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `N:Microsoft.AspNetCore.Mvc.Core.Internal`
- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `N:Microsoft.AspNetCore.Rewrite.Internal`
- `N:Microsoft.AspNetCore.Routing.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `N:Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

-->

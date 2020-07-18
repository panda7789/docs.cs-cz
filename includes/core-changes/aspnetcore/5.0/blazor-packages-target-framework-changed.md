---
ms.openlocfilehash: 17a167e5245914329195d61ab45ae2d8ecb617d6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416259"
---
### <a name="blazor-target-framework-of-nuget-packages-changed"></a>Blazor: Cílová architektura balíčků NuGet se změnila

Projekty Blazor 3,2 WebAssembly byly zkompilovány do cíle .NET Standard 2,1 ( `<TargetFramework>netstandard2.1</TargetFramework>` ). V ASP.NET Core 5,0 jsou oba projekty Blazor serveru i Blazor pro sestavení na platformě .NET 5,0 ( `<TargetFramework>net5.0</TargetFramework>` ). Pro lepší zarovnání s cílovým rozhraním se změna v následujících balíčcích Blazor už necílí .NET Standard 2,1:

* [Microsoft. AspNetCore. Components](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [Microsoft. AspNetCore. Components. Authorization](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [Microsoft. AspNetCore. Components. Forms](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [Microsoft. AspNetCore. Components. Web](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [Microsoft. AspNetCore. Components. WebAssembly](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [Microsoft. AspNetCore. Components. WebAssembly. Authentication](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [Microsoft.JSspolupráce](https://www.nuget.org/packages/Microsoft.JSInterop)
* [Microsoft.JSInterop. WebAssembly](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [Microsoft. Authentication. WebAssembly. Msal](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

Diskuzi najdete v tématu problém GitHubu [dotnet/aspnetcore # 23424](https://github.com/dotnet/aspnetcore/issues/23424).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 7

#### <a name="old-behavior"></a>Staré chování

V Blazor 3,1 a 3,2 jsou cílové balíčky .NET Standard 2,1 a .NET Core 3,1.

#### <a name="new-behavior"></a>Nové chování

V ASP.NET Core 5,0 balíčky cílí na rozhraní .NET 5,0.

#### <a name="reason-for-change"></a>Důvod změny

Změna byla provedena pro lepší zarovnání s požadavky rozhraní .NET Target Framework.

#### <a name="recommended-action"></a>Doporučená akce

Projekty Blazor 3,2 WebAssembly by měly cílit na .NET 5,0 jako součást aktualizace odkazů na balíčky na 5. x.x. Knihovny, které odkazují na jeden z těchto balíčků, mohou cílit buď na rozhraní .NET 5,0, nebo na více cílů v závislosti na jejich požadavcích.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!--

#### Affected APIs

Not detectable via API analysis

-->

---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901990"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Hostování: obecný hostitel omezuje úvodní vkládání spouštěcího konstruktoru.

Jediný typ, který je podporován pro vkládání konstruktoru `Startup` třídy, je `IHostEnvironment`, `IWebHostEnvironment`a `IConfiguration`. Aplikace používající `WebHost` nejsou nijak ovlivněny.

#### <a name="change-description"></a>Popis změny

Před ASP.NET Core 3,0 lze vložení konstruktoru použít pro libovolný typ v konstruktoru třídy `Startup`. V ASP.NET Core 3,0 byl webový zásobník znovu založen na obecné knihovně hostitelů. Můžete zobrazit změnu v souboru *program.cs* šablony:

**ASP.NET Core 2. x:**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3,0:**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host` používá k sestavení aplikace jeden kontejner vkládání závislostí (DI). `WebHost` používá dva kontejnery: jeden pro hostitele a jeden pro aplikaci. V důsledku toho konstruktor `Startup` již nepodporuje vlastní vkládání služeb. Vložit lze pouze `IHostEnvironment`, `IWebHostEnvironment`a `IConfiguration`. Tato změna zabraňuje chybám typu DI, jako je vytváření duplicitních služeb typu singleton.

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="reason-for-change"></a>Důvod změny

Tato změna je v důsledku opětovného hostování webového zásobníku do obecné knihovny hostitelů.

#### <a name="recommended-action"></a>Doporučená akce

Vloží služby do signatury `Startup.Configure` metody. Příklad:

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

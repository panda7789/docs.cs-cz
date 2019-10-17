---
ms.openlocfilehash: be9a79f6ead3e72d7ffaade758704f0c1e2477f0
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394029"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Hostování: obecný hostitel omezuje úvodní vkládání spouštěcího konstruktoru.

Jediné typy, které podporuje obecný hostitel, pro vkládání konstruktoru třídy `Startup` jsou `IHostEnvironment`, `IWebHostEnvironment` a `IConfiguration`. Aplikace používající `WebHost` nejsou ovlivněny.

#### <a name="change-description"></a>Změnit popis

Před ASP.NET Core 3,0 lze injektáže konstruktoru použít pro libovolný typ v konstruktoru třídy `Startup`. V ASP.NET Core 3,0 byl webový zásobník znovu založen na obecné knihovně hostitelů. Můžete zobrazit změnu v souboru *program.cs* šablony:

**ASP.NET Core 2. x:**

<https://github.com/aspnet/AspNetCore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3,0:**

<https://github.com/aspnet/AspNetCore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host` používá k sestavení aplikace jeden kontejner vkládání závislostí (DI). `WebHost` používá dva kontejnery: jeden pro hostitele a jeden pro aplikaci. V důsledku toho konstruktor `Startup` již nepodporuje vlastní vkládání služeb. Vložit lze pouze `IHostEnvironment`, `IWebHostEnvironment` a `IConfiguration`. Tato změna zabraňuje chybám typu DI, jako je vytváření duplicitních služeb typu singleton.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="reason-for-change"></a>Důvod změny

Tato změna je v důsledku opětovného hostování webového zásobníku do obecné knihovny hostitelů.

#### <a name="recommended-action"></a>Doporučená akce

Vloží služby do signatury metody `Startup.Configure`. Příklad:

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

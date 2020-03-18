---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901990"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Hostování: Obecný hostitel omezuje injekci konstruktoru spuštění

Jediné typy, které obecný `Startup` hostitel podporuje `IHostEnvironment`pro `IWebHostEnvironment`vstřikování konstruktoru třídy, jsou , , a `IConfiguration`. Aplikace, `WebHost` které používají, nejsou ovlivněny.

#### <a name="change-description"></a>Popis změny

Před ASP.NET Core 3.0, vstřikování konstruktoru `Startup` lze použít pro libovolné typy v konstruktoru třídy. V ASP.NET Core 3.0 byl webový zásobník přepojován do obecné hostitelské knihovny. Můžete vidět změnu v *souboru Program.cs* šablon:

**ASP.NET Jádro 2.x:**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET jádro 3.0:**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host`používá jeden kontejner vkládání závislostí (DI) k vytvoření aplikace. `WebHost`používá dva kontejnery: jeden pro hostitele a jeden pro aplikaci. V důsledku toho `Startup` konstruktor již podporuje vlastní injektáž služby. Pouze `IHostEnvironment` `IWebHostEnvironment`, `IConfiguration` , a může být aplikován. Tato změna zabraňuje di problémy, jako je například duplicitní vytvoření služby singleton.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="reason-for-change"></a>Důvod změny

Tato změna je důsledkem replatforming webovézásobníku do obecné knihovny hostitelů.

#### <a name="recommended-action"></a>Doporučená akce

Vložte služby do podpisu `Startup.Configure` metody. Například:

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

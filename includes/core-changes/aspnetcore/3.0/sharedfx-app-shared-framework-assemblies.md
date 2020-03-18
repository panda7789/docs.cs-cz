---
ms.openlocfilehash: a8146db1fb54d63d4716b879ce793f7d817cef59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937303"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Sdílený rámec: Sestavení odebraná z microsoft.aspNetCore.App

Počínaje ASP.NET jádrem 3.0 obsahuje sdílený`Microsoft.AspNetCore.App`rámec ASP.NET Core ( ) pouze sestavení první strany, která jsou plně vyvinutá, podporovaná a opravitelná společností Microsoft.

#### <a name="change-description"></a>Popis změny

Představte si změnu jako předefinování hranic pro ASP.NET "platformu Core". Sdílený rámec bude [vytvářet kdokoli prostřednictvím GitHubu](https://github.com/dotnet/source-build) a bude i nadále nabízet existující výhody sdílených rozhraní .NET Core vašim aplikacím. Mezi výhody patří menší velikost nasazení, centralizované opravy a rychlejší spuštění.

Jako součást změny, některé pozoruhodné lámání změny `Microsoft.AspNetCore.App`jsou zavedeny v .

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Projekty `Microsoft.AspNetCore.App` odkazované `<PackageReference>` prostřednictvím prvku v souboru projektu.

Kromě toho `Microsoft.AspNetCore.App` obsahuje následující dílčí součásti:

- Json.NET`Newtonsoft.Json`( )
- Core frameworku entity (sestavy `Microsoft.EntityFrameworkCore.`s předponou )
- Roslyn`Microsoft.CodeAnalysis`( )

#### <a name="new-behavior"></a>Nové chování

Odkaz na `Microsoft.AspNetCore.App` již nevyžaduje `<PackageReference>` prvek v souboru projektu. Sada .NET Core SDK podporuje `<FrameworkReference>`nový prvek s `<PackageReference>`názvem , který nahrazuje použití .

Další informace naleznete [v tématu dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).

Entity Framework Core dodává jako balíčky NuGet. Tato změna zarovná model expedice se všemi ostatními knihovnami přístupu k datům v rozhraní .NET. Poskytuje entity Framework Core nejjednodušší cestu k pokračování inovace při podpoře různých platforem .NET. Přesunutí jádra entity frameworku ze sdíleného rozhraní nemá žádný vliv na jeho stav jako knihovny vyvinuté společností Microsoft, podporované a opravitelné. [Zásady podpory .NET Core](https://www.microsoft.com/net/platform/support-policy) nadále pokrývají.

Json.NET a Core entity nadále pracují s ASP.NET Core. Nebudou však zahrnuty do sdíleného rámce.

Další informace naleznete [v tématu Budoucnost JSON v .NET Core 3.0](https://github.com/dotnet/announcements/issues/90). Podívejte se také [na úplný seznam binárních souborů](https://github.com/dotnet/aspnetcore/issues/3755) odebraných ze sdíleného rozhraní.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna zjednodušuje `Microsoft.AspNetCore.App` spotřebu a snižuje duplicitu mezi balíčky NuGet a sdílené architektury.

Další informace o motivaci k této změně naleznete v [tomto příspěvku blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="recommended-action"></a>Doporučená akce

Nebude nutné pro projekty využívat sestavení `Microsoft.AspNetCore.App` jako balíčky NuGet. Pro zjednodušení cílení a využití sdíleného rozhraní ASP.NET Core se již nevyrábí mnoho balíčků NuGet dodávaných od ASP.NET Core 1.0. Rozhraní API, která tyto balíčky poskytují, `<FrameworkReference>` `Microsoft.AspNetCore.App`jsou stále k dispozici aplikacím pomocí a to . Běžné příklady rozhraní API zahrnují Kestrel, MVC a Razor.

Tato změna se nevztahuje na všechny `Microsoft.AspNetCore.App` binární soubory, na které odkazuje v ASP.NET Jádrem 2.x. Mezi významné výjimky patří:

- `Microsoft.Extensions`knihovny, které budou i nadále cílit na https://github.com/dotnet/extensions)standard .NET, budou k dispozici jako balíčky NuGet (viz .
- API vytvořená týmem ASP.NET Core, která `Microsoft.AspNetCore.App`nejsou součástí aplikace . Například následující součásti jsou k dispozici jako balíčky NuGet:
  - Entity Framework Core
  - API, která poskytují integraci třetích stran
  - Experimentální funkce
  - Rozhraní API se závislostmi, které [nemohly splnit požadavky na být ve sdíleném rámci](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)
- Rozšíření MVC, které udržují podporu pro Json.NET. Rozhraní API bude k dispozici jako balíček NuGet pro podporu pomocí Json.NET a MVC.
- Klient SignalR .NET bude nadále podporovat standard .NET a doručovat jako balíček NuGet. Je určen pro použití v mnoha runčasech .NET, jako je Například Xamarin a UPW.

Další informace naleznete [v tématu Stop vyrábějící balíčky pro sestavení sdílené architektury v 3.0](https://github.com/dotnet/aspnetcore/issues/3756). Diskuse naleznete [v tématu dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->

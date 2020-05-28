---
ms.openlocfilehash: d598d8d3203e804e5e935c3564b0053f9fc2e9a6
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84145006"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Sdílené rozhraní: sestavení byla z Microsoft. AspNetCore. app odebrána.

Počínaje ASP.NET Core 3,0 obsahuje ASP.NET Core Shared Framework ( `Microsoft.AspNetCore.App` ) pouze sestavení First stran, která jsou plně vyvinutá, podporovaná a obsluhovaná společností Microsoft.

#### <a name="change-description"></a>Popis změny

Tuto změnu si můžete představit jako předefinování hranic pro ASP.NET Core platformu. Sdílená architektura bude [sestavená na zdrojovém sestavení prostřednictvím GitHubu](https://github.com/dotnet/source-build) a bude dál nabízet stávající výhody sdílených rozhraní .NET Core pro vaše aplikace. Mezi výhody patří menší velikost nasazení, centralizované opravy a rychlejší doba spuštění.

V rámci změny jsou v nástroji představeny některé významné změny `Microsoft.AspNetCore.App` .

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Projekty, na které se odkazuje `Microsoft.AspNetCore.App` prostřednictvím `<PackageReference>` elementu v souboru projektu.

Kromě toho `Microsoft.AspNetCore.App` obsahoval následující podsoučásti:

- Json.NET ( `Newtonsoft.Json` )
- Entity Framework Core (sestavení s předponou `Microsoft.EntityFrameworkCore.` )
- Roslyn ( `Microsoft.CodeAnalysis` )

#### <a name="new-behavior"></a>Nové chování

Odkaz, který `Microsoft.AspNetCore.App` již vyžaduje `<PackageReference>` prvek v souboru projektu. .NET Core SDK podporuje nový element s názvem `<FrameworkReference>` , který nahrazuje použití `<PackageReference>` .

Další informace naleznete v tématu [dotnet/aspnetcore # 3612](https://github.com/dotnet/aspnetcore/issues/3612).

Entity Framework Core se dodává jako balíčky NuGet. Tato změna zarovnává přepravní model se všemi ostatními knihovnami přístupu k datům v .NET. Poskytuje Entity Framework Core nejjednodušší cestu pro pokračování v inovacích a zároveň podporuje různé platformy .NET. Přesunutí Entity Framework Core ze sdíleného rozhraní nemá žádný vliv na svůj stav jako rozvinuté a podporované knihovny Microsoftu. [Zásady podpory .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) se budou i nadále pokrývat.

Json.NET a Entity Framework Core nadále pracují s ASP.NET Core. Nebudou ale zahrnuty do sdíleného rozhraní.

Další informace najdete [v budoucnosti JSON v .NET Core 3,0](https://github.com/dotnet/announcements/issues/90). Také [se zobrazí úplný seznam binárních souborů](https://github.com/dotnet/aspnetcore/issues/3755) odebraných ze sdíleného rozhraní.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna zjednodušuje spotřebu `Microsoft.AspNetCore.App` a snižuje duplicity mezi balíčky NuGet a sdílenými rozhraními.

Další informace o motivaci této změny najdete v [tomto blogovém příspěvku](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="recommended-action"></a>Doporučená akce

Nebude nutné, aby projekty pro využívání sestavení v nástroji `Microsoft.AspNetCore.App` jako balíčky NuGet. Aby se zjednodušilo cílení a použití ASP.NET Core sdílené architektury, mnoho balíčků NuGet dodaných od ASP.NET Core 1,0 se už nevyrábí. Rozhraní API, která tyto balíčky poskytují, jsou stále k dispozici aplikacím pomocí a `<FrameworkReference>` `Microsoft.AspNetCore.App` . Mezi běžné příklady rozhraní API patří Kestrel, MVC a Razor.

Tato změna se nevztahuje na všechny binární soubory `Microsoft.AspNetCore.App` , na které se odkazuje pomocí ASP.NET Core 2. x. Mezi významné výjimky patří:

- `Microsoft.Extensions`knihovny, které pokračují na cílovém .NET Standard, budou k dispozici jako balíčky NuGet (viz <https://github.com/dotnet/extensions> ).
- Rozhraní API vytvořená ASP.NET Core týmem, která nejsou součástí `Microsoft.AspNetCore.App` . Například následující komponenty jsou k dispozici jako balíčky NuGet:
  - Entity Framework Core
  - Rozhraní API, která poskytují integraci třetí strany
  - Experimentální funkce
  - Rozhraní API se závislostmi, které nemohly [splnit požadavky na sdílené rozhraní](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)
- Rozšíření pro MVC, která udržují podporu pro Json.NET. Rozhraní API se poskytne jako balíček NuGet, který podporuje používání Json.NET a MVC.
- Klient rozhraní .NET pro signalizaci bude nadále podporovat .NET Standard a dodávat jako balíček NuGet. Je určený pro použití v mnoha modulech runtime .NET, jako je například Xamarin nebo UWP.

Další informace naleznete v tématu [zastavení výroby balíčků pro sestavení sdílených rozhraní v 3,0](https://github.com/dotnet/aspnetcore/issues/3756). Diskuzi najdete v tématu [dotnet/aspnetcore # 3757](https://github.com/dotnet/aspnetcore/issues/3757).

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

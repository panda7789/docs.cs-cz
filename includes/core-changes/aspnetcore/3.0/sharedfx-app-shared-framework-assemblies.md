---
ms.openlocfilehash: a8146db1fb54d63d4716b879ce793f7d817cef59
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937303"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Shared framework: Assemblies removed from Microsoft.AspNetCore.App

Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.

#### <a name="change-description"></a>Popis změny

Think of the change as the redefining of boundaries for the ASP.NET Core "platform." The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps. Some benefits include smaller deployment size, centralized patching, and faster startup time.

As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.

#### <a name="version-introduced"></a>Version introduced

3,0

#### <a name="old-behavior"></a>Old behavior

Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.

Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:

- Json.NET (`Newtonsoft.Json`)
- Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)
- Roslyn (`Microsoft.CodeAnalysis`)

#### <a name="new-behavior"></a>New behavior

A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file. The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.

For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).

Entity Framework Core ships as NuGet packages. This change aligns the shipping model with all other data access libraries on .NET. It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms. The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library. The [.NET Core support policy](https://www.microsoft.com/net/platform/support-policy) continues to cover it.

Json.NET and Entity Framework Core continue to work with ASP.NET Core. They won't, however, be included in the shared framework.

For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90). Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.

#### <a name="reason-for-change"></a>Reason for change

This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.

For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="recommended-action"></a>Doporučená akce

It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages. Aby se zjednodušilo cílení a použití ASP.NET Core sdílené architektury, mnoho balíčků NuGet dodaných od ASP.NET Core 1,0 se už nevyrábí. Rozhraní API, která tyto balíčky poskytují, jsou stále k dispozici aplikacím pomocí `<FrameworkReference>` k `Microsoft.AspNetCore.App`. Mezi běžné příklady rozhraní API patří Kestrel, MVC a Razor.

Tato změna se nevztahuje na všechny binární soubory, na které se odkazuje pomocí `Microsoft.AspNetCore.App` v ASP.NET Core 2. x. Mezi významné výjimky patří:

- `Microsoft.Extensions` knihovny, které pokračují v cíli .NET Standard, budou k dispozici jako balíčky NuGet (viz https://github.com/dotnet/extensions).
- Rozhraní API vytvořená ASP.NET Core týmem, která nejsou součástí `Microsoft.AspNetCore.App`. Například následující komponenty jsou k dispozici jako balíčky NuGet:
  - Entity Framework Core
  - Rozhraní API, která poskytují integraci třetí strany
  - Experimentální funkce
  - Rozhraní API se závislostmi, které nemohly [splnit požadavky na sdílené rozhraní](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)
- Rozšíření pro MVC, která udržují podporu pro Json.NET. Rozhraní API se poskytne jako balíček NuGet, který podporuje používání Json.NET a MVC.
- Klient rozhraní .NET pro signalizaci bude nadále podporovat .NET Standard a dodávat jako balíček NuGet. Je určený pro použití v mnoha modulech runtime .NET, jako je například Xamarin nebo UWP.

Další informace naleznete v tématu [zastavení výroby balíčků pro sestavení sdílených rozhraní v 3,0](https://github.com/dotnet/aspnetcore/issues/3756). Diskuzi najdete v tématu [dotnet/aspnetcore # 3757](https://github.com/dotnet/aspnetcore/issues/3757).

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->

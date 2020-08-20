---
ms.openlocfilehash: 6deeb7debce9b731f3871b7de0ad8df8a8cdafea
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728300"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a>Lokalizace: odebral se člen rozhraní třídy ResourceManagerWithCultureStringLocalizer a WithCulture.

Metoda třídy [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) a [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) byla odebrána v rozhraní .NET 5,0 Preview 1.

Kontext najdete v tématu [ASPNET/oznámení # 346](https://github.com/aspnet/Announcements/issues/346) a [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Diskuzi o této změně najdete v tématu [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 1

#### <a name="old-behavior"></a>Staré chování

`ResourceManagerWithCultureStringLocalizer`Třída a `ResourceManagerStringLocalizer.WithCulture` Metoda jsou [zastaralé v rozhraní .NET Core 3,0 Preview 3 a novější](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).

#### <a name="new-behavior"></a>Nové chování

`ResourceManagerWithCultureStringLocalizer`Třída a `ResourceManagerStringLocalizer.WithCulture` metoda byly odebrány v rozhraní .NET 5,0 Preview 1. Inventář provedených změn najdete v žádosti o získání dat v [dotnet/rozšířeních # 2562](https://github.com/dotnet/extensions/pull/2562/files).

#### <a name="reason-for-change"></a>Důvod změny

Metoda [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) a [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) byla často zdrojem nejasností pro uživatele lokalizace. Při vytváření vlastní implementace byla obzvláště vysoká nejasnost <xref:Microsoft.Extensions.Localization.IStringLocalizer> . Tato třída a metoda dává spotřebitelům dojem, že se očekává, že `IStringLocalizer` instance bude "na jazyk, podle prostředků". Ve skutečnosti by instance měla být pouze "za prostředek". V době běhu <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> Určuje vlastnost jazyk, který se má použít.

#### <a name="recommended-action"></a>Doporučená akce

Ukončete používání `ResourceManagerWithCultureStringLocalizer` třídy a `ResourceManagerStringLocalizer.WithCulture` metody.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->

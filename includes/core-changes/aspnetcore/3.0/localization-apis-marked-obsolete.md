---
ms.openlocfilehash: d70a8d2a3031a5b3d47ab3fb7f40193dce6e311e
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728337"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Lokalizace: ResourceManagerWithCultureStringLocalizer a WithCulture označené jako zastaralé

Člen třídy [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) a rozhraní [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) jsou často zdrojem nejasností pro uživatele lokalizace, zejména při vytváření vlastní `IStringLocalizer` implementace. Tyto položky přidávají uživateli dojem, že je `IStringLocalizer` instance "na jazyk, podle prostředků". Ve skutečnosti by měly být instance pouze "za prostředek". Hledaný jazyk je určen `CultureInfo.CurrentUICulture` v době spuštění. Aby se vyloučil zdroj nejasností, rozhraní API byla v ASP.NET Core 3,0 Preview 3 označená jako zastaralá. Rozhraní API se v budoucí verzi odeberou.

Pro kontext viz [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Diskuzi najdete v tématu [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Metody nebyly označeny jako `Obsolete`.

#### <a name="new-behavior"></a>Nové chování

Metody jsou označeny `Obsolete`.

#### <a name="reason-for-change"></a>Důvod změny

Rozhraní API představovaly případ použití, který se nedoporučuje. Při návrhu lokalizace došlo k nejasnostem.

#### <a name="recommended-action"></a>Doporučená akce

Doporučujeme místo toho použít `ResourceManagerStringLocalizer` . Povolit jazykovou verzi nastavením `CurrentCulture`. Pokud to není možnost, vytvořte a použijte kopii [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.0)
- [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.0)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->

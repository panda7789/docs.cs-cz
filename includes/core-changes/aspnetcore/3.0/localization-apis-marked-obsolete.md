---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901940"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Lokalizace: ResourceManagerWithCultureStringLocalizer a WithCulture označené jako zastaralé

[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) třídy a [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) člen rozhraní jsou často zdrojem nejasností `IStringLocalizer` pro uživatele lokalizace, zejména při vytváření vlastní implementace. Tyto položky dávají uživateli `IStringLocalizer` dojem, že instance je "podle jazyka, podle prostředku". Ve skutečnosti by instance měly být pouze "na prostředek". Vyhledávaný jazyk je `CultureInfo.CurrentUICulture` určen časem spuštění. Chcete-li odstranit zdroj nejasností, byla v ASP.NET core 3.0 Preview 3 označena jako zastaralá. Api budou odebrány v budoucí verzi.

Kontext naleznete [v tématu dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324). Diskuse naleznete [v tématu dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Metody nebyly označeny `Obsolete`jako .

#### <a name="new-behavior"></a>Nové chování

Metody jsou `Obsolete`označeny .

#### <a name="reason-for-change"></a>Důvod změny

Api představovalpřípad použití, který není doporučeno. Tam byl zmatek o návrhu lokalizace.

#### <a name="recommended-action"></a>Doporučená akce

Doporučení je použít `ResourceManagerStringLocalizer` místo. Nechť je jazyková verze nastavena souborem `CurrentCulture`. Pokud to není možnost, vytvořte a použijte kopii [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->

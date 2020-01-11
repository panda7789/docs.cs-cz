---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901940"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Lokalizace: ResourceManagerWithCultureStringLocalizer a WithCulture označené jako zastaralé

Člen třídy [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) a rozhraní [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) jsou často zdrojem nejasností pro uživatele lokalizace, zejména při vytváření vlastní `IStringLocalizer` implementace. Tyto položky přidávají uživateli dojem, že instance `IStringLocalizer` je "pro jednotlivé jazyky" podle prostředků ". Ve skutečnosti by měly být instance pouze "za prostředek". Hledaný jazyk je určen `CultureInfo.CurrentUICulture` v době spuštění. Aby se vyloučil zdroj nejasností, rozhraní API byla v ASP.NET Core 3,0 Preview 3 označená jako zastaralá. Rozhraní API se v budoucí verzi odeberou.

Pro kontext viz [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Diskuzi najdete v tématu [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Metody nebyly označeny jako `Obsolete`.

#### <a name="new-behavior"></a>Nové chování

Metody jsou označeny `Obsolete`.

#### <a name="reason-for-change"></a>Důvod změny

Rozhraní API představovaly případ použití, který se nedoporučuje. Při návrhu lokalizace došlo k nejasnostem.

#### <a name="recommended-action"></a>Doporučená akce

Doporučujeme místo toho použít `ResourceManagerStringLocalizer`. Nechte tuto jazykovou verzi nastavit pomocí `CurrentCulture`. Pokud to není možnost, vytvořte a použijte kopii [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->

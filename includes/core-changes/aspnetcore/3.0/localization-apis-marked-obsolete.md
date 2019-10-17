---
ms.openlocfilehash: da1ec7908b3082fc61313cb805773aa600bc1b5d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393977"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Lokalizace: ResourceManagerWithCultureStringLocalizer a WithCulture označené jako zastaralé

Člen třídy [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) a rozhraní [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) jsou často zdrojem nejasností pro uživatele lokalizace, zejména při vytváření vlastní implementace `IStringLocalizer`. Tyto položky dávají uživateli dojem, že instance `IStringLocalizer` je "na jazyk", podle prostředků ". Ve skutečnosti by měly být instance pouze "za prostředek". Hledaný jazyk je určen `CultureInfo.CurrentUICulture` v době spuštění. Aby se vyloučil zdroj nejasností, rozhraní API byla v ASP.NET Core 3,0 Preview 3 označená jako zastaralá. Rozhraní API se v budoucí verzi odeberou.

Pro kontext naleznete informace v tématu [ASPNET/AspNetCore # 3324](https://github.com/aspnet/AspNetCore/issues/3324). Diskuzi najdete v tématu [ASPNET/AspNetCore # 7756](https://github.com/aspnet/AspNetCore/issues/7756).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Metody nebyly označeny jako `Obsolete`.

#### <a name="new-behavior"></a>Nové chování

Metody jsou označeny `Obsolete`.

#### <a name="reason-for-change"></a>Důvod změny

Rozhraní API představovaly případ použití, který se nedoporučuje. Při návrhu lokalizace došlo k nejasnostem.

#### <a name="recommended-action"></a>Doporučená akce

Doporučení je místo toho použít `ResourceManagerStringLocalizer`. Nechte tuto jazykovou verzi nastavit pomocí `CurrentCulture`. Pokud to není možnost, vytvořte a použijte kopii [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

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

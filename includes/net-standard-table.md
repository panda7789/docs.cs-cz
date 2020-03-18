---
ms.openlocfilehash: 9e95db8a1530fabd30b5344c87728b9210c0ad69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802839"
---
| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1,5]              | [1.6]              | [2.0]               | [2.1] |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|---------------------
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2.0                 | 3.0 |
| Rozhraní .NET Framework <sup>1</sup>| 4.5    | 4.5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  | Není k<sup>md: 3</sup> |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5.4                 | 6.4 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10.14               | 12.16 |
| Xamarin.Mac                | 3.0    | 3.0    | 3.0   | 3.0   | 3.0   | 3.0                | 3.0                | 3.8                 | 5.16 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 | 10.0 |
| Univerzální platforma Windows | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          | Bude doplněno |
| Unity                      | 2018.1 | 2018.1 | 2018.1| 2018.1| 2018.1| 2018.1             |  2018.1            | 2018.1              | Bude doplněno |

<sup>1 Verze uvedené pro rozhraní .NET Framework se vztahují na sadu .NET Core 2.0 SDK a novější verze nástrojů. Starší verze používaly jiné mapování pro standard .NET Standard 1.5 a vyšší. Pokud nemůžete upgradovat na Visual Studio 2017 nebo novější verzi, můžete [si stáhnout nástroje pro nástroje .NET Core pro Visual Studio 2015.](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)</sup>

<sup>2 Zde uvedené verze představují pravidla, která nuget používá k určení, zda je daná knihovna .NET Standard použitelná. Zatímco NuGet považuje rozhraní .NET Framework 4.6.1 za podporu standardu .NET Standard 1.5 až 2.0, existuje několik problémů se spotřebovávajícími knihovnami .NET Standard, které byly vytvořeny pro tyto verze z projektů rozhraní .NET Framework 4.6.1. Pro projekty rozhraní .NET Framework, které je potřeba použít tyto knihovny, doporučujeme upgradovat projekt na cíl .NET Framework 4.7.2 nebo vyšší.</sup>

<sup>3 Rozhraní .NET Framework nebude podporovat rozhraní .NET Standard 2.1 nebo novější verze. Další podrobnosti naleznete v [oznámení standardu .NET Standard 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/).</sup>

- Sloupce představují verze .NET Standard. Každá buňka záhlaví je odkaz na dokument, který ukazuje, která rozhraní API byla přidána v této verzi standardu .NET.
- Řádky představují různé implementace rozhraní .NET.
- Číslo verze v každé buňce označuje *minimální* verzi implementace, kterou budete potřebovat, abyste mohli cílit na tuto verzi .NET Standard.
- Interaktivní tabulku naleznete v tématu [verze .NET Standard](https://dotnet.microsoft.com/platform/dotnet-standard#versions).

[1.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.0.md
[1.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.1.md
[1.2]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.2.md
[1.3]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.3.md
[1.4]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.4.md
[1,5]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.5.md
[1.6]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.6.md
[2.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md
[2.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.1.md

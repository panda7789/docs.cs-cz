---
ms.openlocfilehash: 9e95db8a1530fabd30b5344c87728b9210c0ad69
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802839"
---
| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1,5]              | [1.6]              | [2.0]               | [2,1] |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|---------------------
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2.0                 | 3,0 |
| .NET Framework <sup>1</sup>| 4,5    | 4,5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  | Není k dispozici<sup>3</sup> |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5.4                 | 6.4 |
| Xamarin.iOS                | 10,0   | 10,0   | 10,0  | 10,0  | 10,0  | 10,0               | 10,0               | 10,14               | 12,16 |
| Xamarin.Mac                | 3,0    | 3,0    | 3,0   | 3,0   | 3,0   | 3,0                | 3,0                | 3.8                 | 5,16 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 | 10,0 |
| Univerzální platforma pro Windows | 10,0   | 10,0   | 10,0  | 10,0  | 10,0  | 10.0.16299         | 10.0.16299         | 10.0.16299          | Bude určeno později |
| Unity                      | 2018,1 | 2018,1 | 2018,1| 2018,1| 2018,1| 2018,1             |  2018,1            | 2018,1              | Bude určeno později |

<sup>1 verze uvedené pro .NET Framework platí pro .NET Core 2,0 SDK a novější verze nástrojů. Starší verze používaly jiné mapování pro .NET Standard 1,5 a vyšší. [Nástroje pro nástroje .NET Core pro Visual studio 2015](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md) si můžete stáhnout, pokud nemůžete upgradovat na Visual Studio 2017 nebo novější verzi.</sup>

<sup>2 níže uvedené verze reprezentují pravidla, která nástroj NuGet používá k určení, jestli se konkrétní knihovna .NET Standard použít. I když NuGet vychází z .NET Framework 4.6.1 jako podpora .NET Standard 1,5 až 2,0, je k dispozici několik problémů se zachováním knihoven .NET Standard, které byly vytvořeny pro tyto verze z .NET Framework projektů 4.6.1. Pro .NET Framework projekty, které potřebují používat takové knihovny, doporučujeme upgradovat projekt na cílovou .NET Framework 4.7.2 nebo vyšší.</sup>

<sup>3 .NET Framework nepodporují .NET Standard 2,1 nebo novější verze. Další podrobnosti najdete v [oznámení o .NET Standard 2,1](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/).</sup>

- Sloupce reprezentují .NET Standard verze. Každá buňka záhlaví je odkaz na dokument, který zobrazuje rozhraní API přidaná v této verzi .NET Standard.
- Řádky reprezentují různé implementace rozhraní .NET.
- Číslo verze v každé buňce určuje *minimální* verzi implementace, kterou budete potřebovat, aby bylo možné cílit na verzi .NET Standard.
- Interaktivní tabulku najdete v tématu [.NET Standard verze](https://dotnet.microsoft.com/platform/dotnet-standard#versions).

[1.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.0.md
[1.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.1.md
[1.2]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.2.md
[1.3]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.3.md
[1.4]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.4.md
[1,5]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.5.md
[1.6]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.6.md
[2.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md
[2,1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.1.md

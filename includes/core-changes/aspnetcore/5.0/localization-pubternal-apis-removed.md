---
ms.openlocfilehash: 2094da7ec94028c112d6683620ac1146a1544dab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446966"
---
### <a name="localization-pubternal-apis-removed"></a>Lokalizace: rozhraní API "Pubternal" byla odebrána

Aby se lépe zachovala veřejná plocha rozhraní API ASP.NET Core, :::no-loc text="\"pubternal\""::: odstranila se některá rozhraní API lokalizace. :::no-loc text="\"pubternal\"":::Rozhraní API má `public` modifikátor přístupu a je definováno v oboru názvů, který implikuje [vnitřní](/dotnet/csharp/language-reference/keywords/internal) záměr.

Diskuzi najdete v tématu [dotnet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 6

#### <a name="old-behavior"></a>Staré chování

Následující rozhraní API `public` :

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer`přetížení konstruktoru přijímají některý z následujících typů parametrů:
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a>Nové chování

Následující seznam popisuje změny:

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`stalo `Microsoft.Extensions.Localization.AssemblyWrapper` a je nyní `internal` .
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`stalo `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` a je nyní `internal` .
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer`přetížení konstruktoru, který přijímá některý z následujících typů parametrů, jsou nyní `internal` :
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a>Důvod změny

Je vysvětleno podrobnější informace na [ASPNET/oznámeních # hodnoty 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: typy byly odebrány z `public` povrchu rozhraní API. Tyto změny přizpůsobují více tříd k tomuto rozhodnutí o návrhu. Příslušné třídy byly určeny jako body rozšíření pro interní testování týmu.

#### <a name="recommended-action"></a>Doporučená akce

I když je pravděpodobné, že některé aplikace můžou být úmyslně nebo náhodně závislé na :::no-loc text="\"pubternal\""::: typech. Informace o tom, jak migrovat z typů, najdete v oddílech [nového chování](#new-behavior) .

Pokud jste identifikovali scénář, který povoluje veřejné rozhraní API před touto změnou, ale ne teď, zapište problém v [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->

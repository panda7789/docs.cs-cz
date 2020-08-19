---
ms.openlocfilehash: a635e2ed6a735b5234c92fd8f5ffa1685fe9373e
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558169"
---
### <a name="microsoftdotnetplatformabstractions-package-removed"></a>Balíček Microsoft. DotNet. PlatformAbstractions se odebral.

Nebudou se vytvářet žádné nové verze [balíčku NuGet Microsoft. dotnet. PlatformAbstractions](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) .

#### <a name="change-description"></a>Popis změny

Dříve byly nové verze <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> knihovny vyprodukovány spolu s novými verzemi .NET Core. Až do knihovny nebudou přidány žádné nové funkce a nebudou zveřejněny žádné nové hlavní verze. Stávající verze knihovny ale budou i nadále fungovat a budou se obsluhovat.

<xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName>Knihovna se překrývá s rozhraními API, která jsou již vytvořena v \* oboru názvů System. Namespaces. Některá <xref:Microsoft.DotNet.PlatformAbstractions> rozhraní API se navíc nenavrhla se stejnou úrovní kontroly a dlouhodobou podporou jako zbytek systému. \* Třídy. Například <xref:Microsoft.DotNet.PlatformAbstractions> používá `Platform` výčet k popisu aktuální platformy operačního systému. Tento návrh výčtu byl explicitně odmítnut, když <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> bylo navrženo rozhraní API, aby bylo možné nové platformy a budoucí flexibilitu.

Scénáře, které knihovna povoluje, <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> jsou teď možné bez ní. Stávající verze budou fungovat i dál, i v .NET 5,0 a novějších a budou se obsluhovat spolu s předchozími verzemi .NET Core. Nové funkce však nebudou přidány do knihovny. Místo toho se nové funkce přidají do jiných knihoven a rozhraní API.

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 6

#### <a name="recommended-action"></a>Doporučená akce

- Pokud splňuje vaše požadavky, můžete i nadále používat starší verze knihovny.

- Pokud starší verze nevyhovují vašim požadavkům, nahraďte použití `PlatformAbstractions` rozhraní API doporučenými nahrazeními.

  | `PlatformAbstractions` API | Doporučená náhrada |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> a <xref:System.Environment.OSVersion?displayProperty=nameWithType> |

  > [!NOTE]
  > Většina případů použití pro `RuntimeEnvironment.OperatingSystem` a `RuntimeEnvironment.OperatingSystemVersion` se zobrazuje pro účely zobrazení, například zobrazení pro uživatele, protokolování a telemetrie. V závislosti na verzi operačního systému (OS) se nedoporučuje provádět rozhodnutí za běhu. <xref:System.Environment.OSVersion?displayProperty=nameWithType> nyní [vrátí správnou verzi](../../../../docs/core/compatibility/corefx.md#environmentosversion-returns-the-correct-operating-system-version) operačních systémů Windows a MacOS. U většiny distribucí systému UNIX, co se považuje za "verzi operačního systému", ale není tak jasné. Může to být třeba verze jádra operačního systému Linux, nebo se může jednat o verzi distribuce. Pro většinu platforem UNIX <xref:System.Environment.OSVersion?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> vrátí verzi, kterou vrátí `uname` . Chcete-li získat název a informace o verzi pro Linux distribuce, je doporučeným přístupem čtení souboru */etc/OS-Release* .

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- `Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner?displayProperty=fullName>
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier()`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

<!--

#### Affected APIs

- `P:Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- `T:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner`
- `M:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

-->

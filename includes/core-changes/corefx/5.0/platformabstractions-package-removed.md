---
ms.openlocfilehash: a635e2ed6a735b5234c92fd8f5ffa1685fe9373e
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558169"
---
### <a name="microsoftdotnetplatformabstractions-package-removed"></a><span data-ttu-id="00107-101">Balíček Microsoft. DotNet. PlatformAbstractions se odebral.</span><span class="sxs-lookup"><span data-stu-id="00107-101">Microsoft.DotNet.PlatformAbstractions package removed</span></span>

<span data-ttu-id="00107-102">Nebudou se vytvářet žádné nové verze [balíčku NuGet Microsoft. dotnet. PlatformAbstractions](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) .</span><span class="sxs-lookup"><span data-stu-id="00107-102">No new versions of the [Microsoft.DotNet.PlatformAbstractions NuGet package](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) will be produced.</span></span>

#### <a name="change-description"></a><span data-ttu-id="00107-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="00107-103">Change description</span></span>

<span data-ttu-id="00107-104">Dříve byly nové verze <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> knihovny vyprodukovány spolu s novými verzemi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="00107-104">Previously, new versions of the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library were produced alongside new versions of .NET Core.</span></span> <span data-ttu-id="00107-105">Až do knihovny nebudou přidány žádné nové funkce a nebudou zveřejněny žádné nové hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="00107-105">Going forward, no new functionality will be added to the library, and no new major versions will be released.</span></span> <span data-ttu-id="00107-106">Stávající verze knihovny ale budou i nadále fungovat a budou se obsluhovat.</span><span class="sxs-lookup"><span data-stu-id="00107-106">However, existing versions of the library will continue to work and be serviced.</span></span>

<span data-ttu-id="00107-107"><xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName>Knihovna se překrývá s rozhraními API, která jsou již vytvořena v \* oboru názvů System. Namespaces.</span><span class="sxs-lookup"><span data-stu-id="00107-107">The <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library overlaps with APIs that are already established in the System.\* namespaces.</span></span> <span data-ttu-id="00107-108">Některá <xref:Microsoft.DotNet.PlatformAbstractions> rozhraní API se navíc nenavrhla se stejnou úrovní kontroly a dlouhodobou podporou jako zbytek systému. \* Třídy.</span><span class="sxs-lookup"><span data-stu-id="00107-108">Also, some <xref:Microsoft.DotNet.PlatformAbstractions> APIs weren't designed with the same level of scrutiny and long-term supportability as the rest of the System.\* APIs.</span></span> <span data-ttu-id="00107-109">Například <xref:Microsoft.DotNet.PlatformAbstractions> používá `Platform` výčet k popisu aktuální platformy operačního systému.</span><span class="sxs-lookup"><span data-stu-id="00107-109">For example, <xref:Microsoft.DotNet.PlatformAbstractions> uses the `Platform` enumeration to describe the current operating system platform.</span></span> <span data-ttu-id="00107-110">Tento návrh výčtu byl explicitně odmítnut, když <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> bylo navrženo rozhraní API, aby bylo možné nové platformy a budoucí flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="00107-110">This enumeration design was explicitly rejected when the <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> API was designed, to allow for new platforms and future flexibility.</span></span>

<span data-ttu-id="00107-111">Scénáře, které knihovna povoluje, <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> jsou teď možné bez ní.</span><span class="sxs-lookup"><span data-stu-id="00107-111">The scenarios enabled by the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library are now possible without it.</span></span> <span data-ttu-id="00107-112">Stávající verze budou fungovat i dál, i v .NET 5,0 a novějších a budou se obsluhovat spolu s předchozími verzemi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="00107-112">Existing versions will continue to work, even in .NET 5.0 and later, and will be serviced along with previous versions of .NET Core.</span></span> <span data-ttu-id="00107-113">Nové funkce však nebudou přidány do knihovny.</span><span class="sxs-lookup"><span data-stu-id="00107-113">However, new functionality won't be added to the library.</span></span> <span data-ttu-id="00107-114">Místo toho se nové funkce přidají do jiných knihoven a rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="00107-114">Instead, new functionality will be added to other libraries and APIs.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="00107-115">Představená verze</span><span class="sxs-lookup"><span data-stu-id="00107-115">Version introduced</span></span>

<span data-ttu-id="00107-116">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="00107-116">5.0 Preview 6</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="00107-117">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="00107-117">Recommended action</span></span>

- <span data-ttu-id="00107-118">Pokud splňuje vaše požadavky, můžete i nadále používat starší verze knihovny.</span><span class="sxs-lookup"><span data-stu-id="00107-118">You can continue to use older versions of the library if they meet your requirements.</span></span>

- <span data-ttu-id="00107-119">Pokud starší verze nevyhovují vašim požadavkům, nahraďte použití `PlatformAbstractions` rozhraní API doporučenými nahrazeními.</span><span class="sxs-lookup"><span data-stu-id="00107-119">If the older versions don't meet your requirements, replace usages of the `PlatformAbstractions` APIs with the recommended replacements.</span></span>

  | <span data-ttu-id="00107-120">`PlatformAbstractions` API</span><span class="sxs-lookup"><span data-stu-id="00107-120">`PlatformAbstractions` API</span></span> | <span data-ttu-id="00107-121">Doporučená náhrada</span><span class="sxs-lookup"><span data-stu-id="00107-121">Recommended replacement</span></span> |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <span data-ttu-id="00107-122"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> a <xref:System.Environment.OSVersion?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="00107-122"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> and <xref:System.Environment.OSVersion?displayProperty=nameWithType></span></span> |

  > [!NOTE]
  > <span data-ttu-id="00107-123">Většina případů použití pro `RuntimeEnvironment.OperatingSystem` a `RuntimeEnvironment.OperatingSystemVersion` se zobrazuje pro účely zobrazení, například zobrazení pro uživatele, protokolování a telemetrie.</span><span class="sxs-lookup"><span data-stu-id="00107-123">Most use cases for `RuntimeEnvironment.OperatingSystem` and `RuntimeEnvironment.OperatingSystemVersion` are for display purposes, for example, displaying to a user, logging, and telemetry.</span></span> <span data-ttu-id="00107-124">V závislosti na verzi operačního systému (OS) se nedoporučuje provádět rozhodnutí za běhu.</span><span class="sxs-lookup"><span data-stu-id="00107-124">It's not recommended to make run-time decisions based on an operating system (OS) version.</span></span> <span data-ttu-id="00107-125"><xref:System.Environment.OSVersion?displayProperty=nameWithType> nyní [vrátí správnou verzi](../../../../docs/core/compatibility/corefx.md#environmentosversion-returns-the-correct-operating-system-version) operačních systémů Windows a MacOS.</span><span class="sxs-lookup"><span data-stu-id="00107-125"><xref:System.Environment.OSVersion?displayProperty=nameWithType> now [returns the correct version](../../../../docs/core/compatibility/corefx.md#environmentosversion-returns-the-correct-operating-system-version) for Windows and macOS operating systems.</span></span> <span data-ttu-id="00107-126">U většiny distribucí systému UNIX, co se považuje za "verzi operačního systému", ale není tak jasné.</span><span class="sxs-lookup"><span data-stu-id="00107-126">However, for most Unix distributions, what is considered to be the "OS version" is not as straightforward.</span></span> <span data-ttu-id="00107-127">Může to být třeba verze jádra operačního systému Linux, nebo se může jednat o verzi distribuce.</span><span class="sxs-lookup"><span data-stu-id="00107-127">For example, it could be the Linux kernel version, or it could be the distro version.</span></span> <span data-ttu-id="00107-128">Pro většinu platforem UNIX <xref:System.Environment.OSVersion?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> vrátí verzi, kterou vrátí `uname` .</span><span class="sxs-lookup"><span data-stu-id="00107-128">For most Unix platforms, <xref:System.Environment.OSVersion?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> return the version that's returned by `uname`.</span></span> <span data-ttu-id="00107-129">Chcete-li získat název a informace o verzi pro Linux distribuce, je doporučeným přístupem čtení souboru */etc/OS-Release* .</span><span class="sxs-lookup"><span data-stu-id="00107-129">To get the Linux distro name and version information, the recommended approach is to read the */etc/os-release* file.</span></span>

#### <a name="category"></a><span data-ttu-id="00107-130">Kategorie</span><span class="sxs-lookup"><span data-stu-id="00107-130">Category</span></span>

<span data-ttu-id="00107-131">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="00107-131">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="00107-132">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="00107-132">Affected APIs</span></span>

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

---
title: Analyzátor rozhraní .NET API
description: Přečtěte si, jak může analyzátor rozhraní .NET API pomáhat detekovat zastaralá rozhraní API a problémy s kompatibilitou platforem.
author: oliag
ms.date: 04/26/2019
ms.technology: dotnet-standard
ms.openlocfilehash: efbfa89f431bd02cdf86b8eff8704aec63a29b6c
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124244"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="90ef9-103">Analyzátor rozhraní .NET API</span><span class="sxs-lookup"><span data-stu-id="90ef9-103">.NET API analyzer</span></span>

<span data-ttu-id="90ef9-104">Analyzátor rozhraní .NET API je nástroj Roslyn Analyzer, který zjišťuje potenciální rizika kompatibility pro C# rozhraní API na různých platformách a detekuje volání zastaralých rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="90ef9-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="90ef9-105">Může být užitečné pro všechny C# vývojáře v jakékoli fázi vývoje.</span><span class="sxs-lookup"><span data-stu-id="90ef9-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="90ef9-106">Analyzátor API se dodává jako balíček NuGet [Microsoft. dotnet. analyzers. Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span><span class="sxs-lookup"><span data-stu-id="90ef9-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="90ef9-107">Poté, co na něj odkazujete v projektu, automaticky monitoruje kód a indikuje problematické využití rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="90ef9-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="90ef9-108">Kliknutím na žárovku můžete také získat návrhy na možné opravy.</span><span class="sxs-lookup"><span data-stu-id="90ef9-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="90ef9-109">Rozevírací nabídka obsahuje možnost pro potlačení upozornění.</span><span class="sxs-lookup"><span data-stu-id="90ef9-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="90ef9-110">Analyzátor rozhraní .NET API je stále předběžnou verzí.</span><span class="sxs-lookup"><span data-stu-id="90ef9-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="90ef9-111">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="90ef9-111">Prerequisites</span></span>

- <span data-ttu-id="90ef9-112">Visual Studio 2017 a novější verze nebo Visual Studio pro Mac (všechny verze).</span><span class="sxs-lookup"><span data-stu-id="90ef9-112">Visual Studio 2017 and later versions, or Visual Studio for Mac (all versions).</span></span>

## <a name="discovering-deprecated-apis"></a><span data-ttu-id="90ef9-113">Zjišťují se zastaralá rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="90ef9-113">Discovering deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="90ef9-114">Co jsou zastaralá rozhraní API?</span><span class="sxs-lookup"><span data-stu-id="90ef9-114">What are deprecated APIs?</span></span>

<span data-ttu-id="90ef9-115">Rodina .NET je sada velkých produktů, které se neustále upgradují tak, aby lépe vyhovovaly potřebám zákazníků.</span><span class="sxs-lookup"><span data-stu-id="90ef9-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="90ef9-116">Je přirozené zastaralá některá rozhraní API a nahrazovat je novými.</span><span class="sxs-lookup"><span data-stu-id="90ef9-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="90ef9-117">Rozhraní API se považuje za zastaralé, pokud existuje lepší alternativa.</span><span class="sxs-lookup"><span data-stu-id="90ef9-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="90ef9-118">Jedním ze způsobů, jak informovat o tom, že rozhraní API je zastaralé a nemělo by se používat, je označit ho pomocí atributu <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="90ef9-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="90ef9-119">Nevýhodou tohoto přístupu je, že existuje jenom jedno ID diagnostiky pro všechna zastaralá C#rozhraní API (pro, [CS0612](../../csharp/misc/cs0612.md)).</span><span class="sxs-lookup"><span data-stu-id="90ef9-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="90ef9-120">To znamená, že:</span><span class="sxs-lookup"><span data-stu-id="90ef9-120">This means that:</span></span>

- <span data-ttu-id="90ef9-121">U každého případu není možné mít vyhrazené dokumenty.</span><span class="sxs-lookup"><span data-stu-id="90ef9-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="90ef9-122">Není možné potlačit určitou kategorii upozornění.</span><span class="sxs-lookup"><span data-stu-id="90ef9-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="90ef9-123">Můžete potlačit buď všechny, nebo žádné z nich.</span><span class="sxs-lookup"><span data-stu-id="90ef9-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="90ef9-124">Chcete-li informovat uživatele o nové zastaralosti, je nutné aktualizovat odkazované sestavení nebo balíček cílení.</span><span class="sxs-lookup"><span data-stu-id="90ef9-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="90ef9-125">Analyzátor API používá kódy chyb specifické pro rozhraní API, které začínají na DE (což představuje chybu při vyřazení), která umožňuje kontrolu nad zobrazením jednotlivých upozornění.</span><span class="sxs-lookup"><span data-stu-id="90ef9-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="90ef9-126">Zastaralá rozhraní API identifikovaná analyzátorem jsou definována v úložišti [dotnet/Platform-kompatibility](https://github.com/dotnet/platform-compat) .</span><span class="sxs-lookup"><span data-stu-id="90ef9-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="using-the-api-analyzer"></a><span data-ttu-id="90ef9-127">Použití analyzátoru rozhraní API</span><span class="sxs-lookup"><span data-stu-id="90ef9-127">Using the API Analyzer</span></span>

<span data-ttu-id="90ef9-128">V případě, že se v kódu používá zastaralé rozhraní API, jako je například <xref:System.Net.WebClient>, analyzátor rozhraní API ho zvýrazní zelenou vlnovkou.</span><span class="sxs-lookup"><span data-stu-id="90ef9-128">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="90ef9-129">Když najedete myší na volání rozhraní API, zobrazí se žárovka s informacemi o zastaralém rozhraní API, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90ef9-129">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

![Snímek obrazovky rozhraní API pro WebClient se zelenou vlnovkou a žárovkou na levé straně](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="90ef9-131">Okno **Seznam chyb** obsahuje upozornění s jedinečným ID na zastaralé rozhraní API, jak je znázorněno v následujícím příkladu (`DE004`):</span><span class="sxs-lookup"><span data-stu-id="90ef9-131">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span> 

<span data-ttu-id="90ef9-132">![Snímek obrazovky okna Seznam chyb zobrazující ID a popis upozornění](media/api-analyzer/warnings-id-and-descriptions.jpg "Seznam chyb okno, které obsahuje upozornění.")</span><span class="sxs-lookup"><span data-stu-id="90ef9-132">!["Screenshot of the Error List window showing warning's ID and description"](media/api-analyzer/warnings-id-and-descriptions.jpg "Error List window that includes warnings.")</span></span>

<span data-ttu-id="90ef9-133">Kliknutím na ID přejdete na webovou stránku s podrobnými informacemi o tom, proč se rozhraní API zastaralo, a návrhy týkající se alternativních rozhraní API, která se dají použít.</span><span class="sxs-lookup"><span data-stu-id="90ef9-133">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="90ef9-134">Všechna upozornění lze potlačit kliknutím pravým tlačítkem na zvýrazněný člen a výběrem možnosti **potlačit \<ID diagnostiky >** .</span><span class="sxs-lookup"><span data-stu-id="90ef9-134">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="90ef9-135">Existují dva způsoby, jak potlačit upozornění:</span><span class="sxs-lookup"><span data-stu-id="90ef9-135">There are two ways to suppress warnings:</span></span> 

- [<span data-ttu-id="90ef9-136">místně (ve zdroji)</span><span class="sxs-lookup"><span data-stu-id="90ef9-136">locally (in source)</span></span>](#suppressing-warnings-locally)
- <span data-ttu-id="90ef9-137">[globálně (v souboru potlačení)](#suppressing-warnings-globally) – doporučeno</span><span class="sxs-lookup"><span data-stu-id="90ef9-137">[globally (in a suppression file)](#suppressing-warnings-globally) - recommended</span></span>

### <a name="suppressing-warnings-locally"></a><span data-ttu-id="90ef9-138">Místní potlačení upozornění</span><span class="sxs-lookup"><span data-stu-id="90ef9-138">Suppressing warnings locally</span></span>

<span data-ttu-id="90ef9-139">Chcete-li potlačit upozornění místně, klikněte pravým tlačítkem na člen, pro který chcete potlačit upozornění, a pak vyberte **rychlé akce a refaktoring** > **potlačit *ID diagnostiky*\<ID diagnostiky >**  > **ve zdroji**.</span><span class="sxs-lookup"><span data-stu-id="90ef9-139">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="90ef9-140">Do zdrojového kódu je v definovaném oboru přidána direktiva preprocesoru upozornění [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) : !["snímek obrazovky s kódem s rámcem #pragma vypnutí upozornění" disable "](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="90ef9-140">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppressing-warnings-globally"></a><span data-ttu-id="90ef9-141">Globální potlačení upozornění</span><span class="sxs-lookup"><span data-stu-id="90ef9-141">Suppressing warnings globally</span></span>

<span data-ttu-id="90ef9-142">Chcete-li potlačit upozornění globálně, klikněte pravým tlačítkem na člen, pro který chcete potlačit upozornění, a pak vyberte **rychlé akce a refaktoring** > **potlačit *ID diagnostiky*\<ID diagnostiky >**  > **v souboru potlačení**.</span><span class="sxs-lookup"><span data-stu-id="90ef9-142">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

![Snímek obrazovky rozhraní API pro WebClient se zelenou vlnovkou a žárovkou na levé straně](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="90ef9-144">Po prvním potlačení se do projektu přidá soubor *GlobalSuppressions.cs* .</span><span class="sxs-lookup"><span data-stu-id="90ef9-144">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="90ef9-145">K tomuto souboru se připojí nová globální potlačení.</span><span class="sxs-lookup"><span data-stu-id="90ef9-145">New global suppressions are appended to this file.</span></span>

![Snímek obrazovky rozhraní API pro WebClient se zelenou vlnovkou a žárovkou na levé straně](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="90ef9-147">Globální potlačení je doporučený způsob, jak zajistit konzistenci využití rozhraní API napříč projekty.</span><span class="sxs-lookup"><span data-stu-id="90ef9-147">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discovering-cross-platform-issues"></a><span data-ttu-id="90ef9-148">Zjišťování problémů s více platformami</span><span class="sxs-lookup"><span data-stu-id="90ef9-148">Discovering cross-platform issues</span></span>

<span data-ttu-id="90ef9-149">Podobně jako zastaralá rozhraní API nástroj Analyzer identifikuje všechna rozhraní API, která nejsou pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="90ef9-149">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="90ef9-150"><xref:System.Console.WindowWidth?displayProperty=nameWithType> například funguje v systému Windows, ale ne v systémech Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="90ef9-150">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="90ef9-151">ID diagnostiky se zobrazí v okně **Seznam chyb** .</span><span class="sxs-lookup"><span data-stu-id="90ef9-151">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="90ef9-152">Toto upozornění můžete potlačit tak, že kliknete pravým tlačítkem a vyberete **rychlé akce a refaktoringy**.</span><span class="sxs-lookup"><span data-stu-id="90ef9-152">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="90ef9-153">Na rozdíl od zastaralých případů, kde máte dvě možnosti (můžete buď dál používat zastaralé členy a potlačit upozornění, nebo je nepoužívat vůbec), pokud vyvíjíte kód jenom pro určité platformy, můžete potlačit všechna upozornění pro všechny ostatní platformy, které nepoužíváte. Naplánujte spuštění kódu v.</span><span class="sxs-lookup"><span data-stu-id="90ef9-153">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="90ef9-154">Chcete-li to provést, stačí upravit soubor projektu a přidat vlastnost `PlatformCompatIgnore`, která obsahuje seznam všech platforem, které mají být ignorovány.</span><span class="sxs-lookup"><span data-stu-id="90ef9-154">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="90ef9-155">Přípustné hodnoty jsou: `Linux`, `macOS`a `Windows`.</span><span class="sxs-lookup"><span data-stu-id="90ef9-155">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="90ef9-156">Pokud váš kód cílí na více platforem a chcete využít výhod rozhraní API, které není na některých z nich podporováno, můžete tuto část kódu chránit pomocí příkazu `if`:</span><span class="sxs-lookup"><span data-stu-id="90ef9-156">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="90ef9-157">Můžete také podmíněně kompilovat na cílové rozhraní nebo operační systém, ale v tuto chvíli je nutné provést [ručně](../frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="90ef9-157">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="90ef9-158">Podporovaná Diagnostika</span><span class="sxs-lookup"><span data-stu-id="90ef9-158">Supported diagnostics</span></span>

<span data-ttu-id="90ef9-159">Analyzátor v současné době zpracovává následující případy:</span><span class="sxs-lookup"><span data-stu-id="90ef9-159">Currently, the analyzer handles the following cases:</span></span>

- <span data-ttu-id="90ef9-160">Využití rozhraní .NET Standard API, které vyvolá <xref:System.PlatformNotSupportedException> (PC001).</span><span class="sxs-lookup"><span data-stu-id="90ef9-160">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
- <span data-ttu-id="90ef9-161">Použití rozhraní .NET Standard API, které není k dispozici v .NET Framework 4.6.1 (PC002).</span><span class="sxs-lookup"><span data-stu-id="90ef9-161">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
- <span data-ttu-id="90ef9-162">Použití nativního rozhraní API, které neexistuje v UWP (PC003).</span><span class="sxs-lookup"><span data-stu-id="90ef9-162">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
- <span data-ttu-id="90ef9-163">Použití rozhraní API Delegate. BeginInvoke a EndInvoke u delegujících (PC004).</span><span class="sxs-lookup"><span data-stu-id="90ef9-163">Usage of Delegate.BeginInvoke and EndInvoke APIs (PC004).</span></span>
- <span data-ttu-id="90ef9-164">Použití rozhraní API, které je označeno jako zastaralé (pro odstranění XXXX).</span><span class="sxs-lookup"><span data-stu-id="90ef9-164">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="90ef9-165">Počítač CI</span><span class="sxs-lookup"><span data-stu-id="90ef9-165">CI machine</span></span>

<span data-ttu-id="90ef9-166">Všechna tato diagnostika jsou k dispozici nejen v integrovaném vývojovém prostředí (IDE), ale také na příkazovém řádku jako součást sestavení projektu, který zahrnuje server CI.</span><span class="sxs-lookup"><span data-stu-id="90ef9-166">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="90ef9-167">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="90ef9-167">Configuration</span></span>

<span data-ttu-id="90ef9-168">Uživatel rozhodne, jak by měla být Diagnostika zpracována: jako upozornění, chyby, návrhy nebo je vypnuto.</span><span class="sxs-lookup"><span data-stu-id="90ef9-168">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="90ef9-169">Například jako architekt se můžete rozhodnout, že problémy s kompatibilitou by měly být považovány za chyby, volání některých zastaralých rozhraní API generují upozornění, zatímco ostatní generují pouze návrhy.</span><span class="sxs-lookup"><span data-stu-id="90ef9-169">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="90ef9-170">Můžete ji nakonfigurovat samostatně podle ID diagnostiky a podle projektu.</span><span class="sxs-lookup"><span data-stu-id="90ef9-170">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="90ef9-171">Provedete to tak, že v **Průzkumník řešení**přejdete do uzlu **závislosti** v projektu.</span><span class="sxs-lookup"><span data-stu-id="90ef9-171">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="90ef9-172">Rozbalte uzel **závislosti** > **analyzátory** > **Microsoft. dotnet. analyzers. Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="90ef9-172">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="90ef9-173">Klikněte pravým tlačítkem na ID diagnostiky, vyberte **nastavit závažnost sady pravidel** a vyberte požadovanou možnost.</span><span class="sxs-lookup"><span data-stu-id="90ef9-173">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

![Snímek obrazovky Průzkumník řešení znázorňující diagnostiku a automaticky otevírané okno se závažností sady pravidel "](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="90ef9-175">Viz také</span><span class="sxs-lookup"><span data-stu-id="90ef9-175">See also</span></span>

- <span data-ttu-id="90ef9-176">Představujeme Blogový příspěvek k [analyzátoru API](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) .</span><span class="sxs-lookup"><span data-stu-id="90ef9-176">[Introducing API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blog post.</span></span>
- <span data-ttu-id="90ef9-177">Ukázkové video [analyzátoru API](https://youtu.be/eeBEahYXGd0) na YouTube</span><span class="sxs-lookup"><span data-stu-id="90ef9-177">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>

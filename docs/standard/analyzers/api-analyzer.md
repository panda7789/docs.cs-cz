---
title: Analyzátor rozhraní .NET API
description: Zjistěte, jak může nástroj .NET API Analyzer pomoci rozpoznat zastaralá rozhraní API a problémy s kompatibilitou platformy.
author: oliag
ms.date: 02/20/2020
ms.technology: dotnet-standard
ms.openlocfilehash: e214c91f2beebc7f3b3324f4879deba9a5623f86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156131"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="8aef0-103">Analyzátor rozhraní .NET API</span><span class="sxs-lookup"><span data-stu-id="8aef0-103">.NET API analyzer</span></span>

<span data-ttu-id="8aef0-104">Analyzátor rozhraní .NET API je analyzátor Roslyn, který zjišťuje potenciální rizika kompatibility rozhraní API jazyka C# na různých platformách a zjišťuje volání již nepřístupných rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8aef0-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="8aef0-105">To může být užitečné pro všechny vývojáře Jazyka C# v jakékoli fázi vývoje.</span><span class="sxs-lookup"><span data-stu-id="8aef0-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="8aef0-106">Analyzátor rozhraní API je dodáván jako balíček NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span><span class="sxs-lookup"><span data-stu-id="8aef0-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="8aef0-107">Po odkazu v projektu automaticky sleduje kód a označuje problematické využití rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8aef0-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="8aef0-108">Můžete také získat návrhy na možné opravy kliknutím na žárovku.</span><span class="sxs-lookup"><span data-stu-id="8aef0-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="8aef0-109">Rozevírací nabídka obsahuje možnost potlačit upozornění.</span><span class="sxs-lookup"><span data-stu-id="8aef0-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="8aef0-110">Analyzátor rozhraní .NET API je stále předběžnou verzí.</span><span class="sxs-lookup"><span data-stu-id="8aef0-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8aef0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8aef0-111">Prerequisites</span></span>

- <span data-ttu-id="8aef0-112">Visual Studio 2017 a novější verze nebo Visual Studio pro Mac (všechny verze).</span><span class="sxs-lookup"><span data-stu-id="8aef0-112">Visual Studio 2017 and later versions, or Visual Studio for Mac (all versions).</span></span>

## <a name="discover-deprecated-apis"></a><span data-ttu-id="8aef0-113">Zjišťování zastaralá api</span><span class="sxs-lookup"><span data-stu-id="8aef0-113">Discover deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="8aef0-114">Co jsou zastaralá api?</span><span class="sxs-lookup"><span data-stu-id="8aef0-114">What are deprecated APIs?</span></span>

<span data-ttu-id="8aef0-115">Řada .NET je sada velkých produktů, které jsou neustále upgradovány tak, aby lépe sloužily potřebám zákazníků.</span><span class="sxs-lookup"><span data-stu-id="8aef0-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="8aef0-116">Je přirozené odsuzovat některá api a nahradit je novými.</span><span class="sxs-lookup"><span data-stu-id="8aef0-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="8aef0-117">Rozhraní API se považuje za zastaralé, pokud existuje lepší alternativa.</span><span class="sxs-lookup"><span data-stu-id="8aef0-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="8aef0-118">Jedním ze způsobů, jak informovat, že rozhraní API je zastaralé a <xref:System.ObsoleteAttribute> nemělo by být použito, je označit jej atributem.</span><span class="sxs-lookup"><span data-stu-id="8aef0-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="8aef0-119">Nevýhodou tohoto přístupu je, že existuje pouze jedno id diagnostiky pro všechna zastaralá nastavení API (pro C#, [CS0612).](../../csharp/misc/cs0612.md)</span><span class="sxs-lookup"><span data-stu-id="8aef0-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="8aef0-120">To znamená, že:</span><span class="sxs-lookup"><span data-stu-id="8aef0-120">This means that:</span></span>

- <span data-ttu-id="8aef0-121">Je nemožné mít vyhrazené dokumenty pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="8aef0-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="8aef0-122">Je nemožné potlačit určitou kategorii varování.</span><span class="sxs-lookup"><span data-stu-id="8aef0-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="8aef0-123">Můžete potlačit buď všechny nebo žádný z nich.</span><span class="sxs-lookup"><span data-stu-id="8aef0-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="8aef0-124">Chcete-li informovat uživatele o novém vyřazení, je třeba aktualizovat odkazované sestavení nebo balíček cílení.</span><span class="sxs-lookup"><span data-stu-id="8aef0-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="8aef0-125">Analyzátor rozhraní API používá kódy chyb specifické pro rozhraní API, které začínají de (což je zkratka pro chyba vyřazení), což umožňuje kontrolu nad zobrazením jednotlivých upozornění.</span><span class="sxs-lookup"><span data-stu-id="8aef0-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="8aef0-126">Zastaralá rozhraní API identifikovaná analyzátorem jsou definována v repo [dotnet/platform-compat.](https://github.com/dotnet/platform-compat)</span><span class="sxs-lookup"><span data-stu-id="8aef0-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="add-the-api-analyzer-to-your-project"></a><span data-ttu-id="8aef0-127">Přidání analyzátoru rozhraní API do projektu</span><span class="sxs-lookup"><span data-stu-id="8aef0-127">Add the API Analyzer to your project</span></span>

1. <span data-ttu-id="8aef0-128">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8aef0-128">Open Visual Studio.</span></span>
2. <span data-ttu-id="8aef0-129">Otevřete projekt, na kterém chcete spustit analyzátor.</span><span class="sxs-lookup"><span data-stu-id="8aef0-129">Open the project you want to run the analyzer on.</span></span>
3. <span data-ttu-id="8aef0-130">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a zvolte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8aef0-130">In **Solution Explorer**, right-click on your project and choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="8aef0-131">(Tato možnost je k dispozici také v nabídce **Projekt.)**</span><span class="sxs-lookup"><span data-stu-id="8aef0-131">(This option is also available from the **Project** menu.)</span></span>
4. <span data-ttu-id="8aef0-132">Na kartě NuGet Package Manager:</span><span class="sxs-lookup"><span data-stu-id="8aef0-132">On the NuGet Package Manager tab:</span></span>
   1. <span data-ttu-id="8aef0-133">Jako zdroj balíčku vyberte "nuget.org".</span><span class="sxs-lookup"><span data-stu-id="8aef0-133">Select "nuget.org" as the Package source.</span></span>
   2. <span data-ttu-id="8aef0-134">Přejděte na kartu **Procházet.**</span><span class="sxs-lookup"><span data-stu-id="8aef0-134">Go to the **Browse** tab.</span></span>
   3. <span data-ttu-id="8aef0-135">Vyberte **Zahrnout předběžnou verzi**.</span><span class="sxs-lookup"><span data-stu-id="8aef0-135">Select **Include prerelease**.</span></span>
   4. <span data-ttu-id="8aef0-136">Vyhledejte **soubor Microsoft.DotNet.Analyzers.Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="8aef0-136">Search for **Microsoft.DotNet.Analyzers.Compatibility**.</span></span>
   5. <span data-ttu-id="8aef0-137">Vyberte tento balíček v seznamu.</span><span class="sxs-lookup"><span data-stu-id="8aef0-137">Select that package in the list.</span></span>
   6. <span data-ttu-id="8aef0-138">Vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="8aef0-138">Select the **Install** button.</span></span>
   7. <span data-ttu-id="8aef0-139">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="8aef0-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="use-the-api-analyzer"></a><span data-ttu-id="8aef0-140">Použití analyzátoru rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8aef0-140">Use the API Analyzer</span></span>

<span data-ttu-id="8aef0-141">Když zastaralé rozhraní API, například <xref:System.Net.WebClient>, se používá v kódu, analyzátor rozhraní API zvýrazní ji zelenou klikatou čárou.</span><span class="sxs-lookup"><span data-stu-id="8aef0-141">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="8aef0-142">Když najedete ukazatel na volání rozhraní API, zobrazí se žárovka s informacemi o vyřazení rozhraní API, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8aef0-142">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

!["Snímek obrazovky s rozhraním API webového klienta se zelenou klikatou čárou a žárovkou vlevo"](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="8aef0-144">Okno **Seznam chyb** obsahuje upozornění s jedinečným ID na zastaralé rozhraní API, jak je znázorněno v následujícím příkladu (`DE004`):</span><span class="sxs-lookup"><span data-stu-id="8aef0-144">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span>

<span data-ttu-id="8aef0-145">!["Snímek obrazovky okna Seznam chyb zobrazující iD a popis upozornění"](media/api-analyzer/warnings-id-and-descriptions.jpg "Okno seznamu chyb, které obsahuje upozornění.")</span><span class="sxs-lookup"><span data-stu-id="8aef0-145">!["Screenshot of the Error List window showing warning's ID and description"](media/api-analyzer/warnings-id-and-descriptions.jpg "Error List window that includes warnings.")</span></span>

<span data-ttu-id="8aef0-146">Kliknutím na ID přejdete na webovou stránku s podrobnými informacemi o tom, proč bylo rozhraní API zastaralé, a návrhy týkajícími se alternativních rozhraní API, která lze použít.</span><span class="sxs-lookup"><span data-stu-id="8aef0-146">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="8aef0-147">Všechna upozornění lze potlačit kliknutím pravým tlačítkem myši na zvýrazněný člen a výběrem **možnosti Potlačit \<id diagnostiky>**.</span><span class="sxs-lookup"><span data-stu-id="8aef0-147">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="8aef0-148">Upozornění lze potlačit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="8aef0-148">There are two ways to suppress warnings:</span></span>

- [<span data-ttu-id="8aef0-149">lokálně (ve zdroji)</span><span class="sxs-lookup"><span data-stu-id="8aef0-149">locally (in source)</span></span>](#suppress-warnings-locally)
- <span data-ttu-id="8aef0-150">[globálně (v odrušovacím souboru)](#suppress-warnings-globally) - doporučeno</span><span class="sxs-lookup"><span data-stu-id="8aef0-150">[globally (in a suppression file)](#suppress-warnings-globally) - recommended</span></span>

### <a name="suppress-warnings-locally"></a><span data-ttu-id="8aef0-151">Potlačit upozornění místně</span><span class="sxs-lookup"><span data-stu-id="8aef0-151">Suppress warnings locally</span></span>

<span data-ttu-id="8aef0-152">Chcete-li potlačit upozornění místně, klepněte pravým tlačítkem myši na člen, pro který chcete potlačit upozornění, a pak vyberte **možnost Rychlé akce a Refaktoringy** > **potlačit id *diagnostic ID*\<diagnostiky diagnostiky>**  > ve **zdroji**.</span><span class="sxs-lookup"><span data-stu-id="8aef0-152">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="8aef0-153">[Direktiva](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) preprocesoru #pragma upozornění je přidána do zdrojového kódu v definovaném oboru: !["Snímek obrazovky kódu zarámovaný #pragma upozornění zakázat"](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="8aef0-153">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppress-warnings-globally"></a><span data-ttu-id="8aef0-154">Potlačit varování globálně</span><span class="sxs-lookup"><span data-stu-id="8aef0-154">Suppress warnings globally</span></span>

<span data-ttu-id="8aef0-155">Chcete-li potlačit upozornění globálně, klepněte pravým tlačítkem myši na člen, pro který chcete potlačit upozornění, a pak vyberte **možnost Rychlé akce a Refaktoringy** > \*\*potlačit id *diagnostic ID*\<diagnostiky \*\*diagnostiky> >  **v souboru potlačení**.</span><span class="sxs-lookup"><span data-stu-id="8aef0-155">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

!["Snímek obrazovky s rozhraním API webového klienta se zelenou klikatou čárou a žárovkou vlevo"](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="8aef0-157">Po prvním potlačení je do projektu přidán *soubor GlobalSuppressions.cs.*</span><span class="sxs-lookup"><span data-stu-id="8aef0-157">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="8aef0-158">K tomuto souboru jsou připojena nová globální potlačení.</span><span class="sxs-lookup"><span data-stu-id="8aef0-158">New global suppressions are appended to this file.</span></span>

!["Snímek obrazovky s rozhraním API webového klienta se zelenou klikatou čárou a žárovkou vlevo"](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="8aef0-160">Globální potlačení je doporučený způsob, jak zajistit konzistenci využití rozhraní API napříč projekty.</span><span class="sxs-lookup"><span data-stu-id="8aef0-160">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discover-cross-platform-issues"></a><span data-ttu-id="8aef0-161">Objevte problémy s více platformami</span><span class="sxs-lookup"><span data-stu-id="8aef0-161">Discover cross-platform issues</span></span>

<span data-ttu-id="8aef0-162">Podobně jako zastaralá api, analyzátor identifikuje všechna api, která nejsou napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="8aef0-162">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="8aef0-163">Například <xref:System.Console.WindowWidth?displayProperty=nameWithType> funguje na Windows, ale ne na Linuxu a macOS.</span><span class="sxs-lookup"><span data-stu-id="8aef0-163">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="8aef0-164">ID diagnostiky se zobrazí v okně **Seznam chyb.**</span><span class="sxs-lookup"><span data-stu-id="8aef0-164">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="8aef0-165">Toto upozornění můžete potlačit klepnutím pravým tlačítkem myši a výběrem **rychlých akcí a refaktoringů**.</span><span class="sxs-lookup"><span data-stu-id="8aef0-165">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="8aef0-166">Na rozdíl od případů vyřazení, kdy máte dvě možnosti (buď nadále používat zastaralá člen a potlačit varování nebo nepoužívat vůbec), zde, pokud vyvíjíte kód pouze pro určité platformy, můžete potlačit všechna upozornění pro všechny ostatní platformy, které nemáte naplánujte spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="8aef0-166">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="8aef0-167">Chcete-li tak učinit, stačí upravit soubor `PlatformCompatIgnore` projektu a přidat vlastnost, která obsahuje seznam všech platforem, které mají být ignorovány.</span><span class="sxs-lookup"><span data-stu-id="8aef0-167">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="8aef0-168">Přijaté hodnoty `Linux`jsou: `macOS`, `Windows`, a .</span><span class="sxs-lookup"><span data-stu-id="8aef0-168">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="8aef0-169">Pokud váš kód cílí na více platforem a chcete využít rozhraní API, které není u `if` některých z nich podporováno, můžete tuto část kódu chránit pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="8aef0-169">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="8aef0-170">Můžete také podmíněně zkompilovat podle cílového rozhraní nebo operačního systému, ale v současné době je třeba provést [ručně](../frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="8aef0-170">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="8aef0-171">Podporovaná diagnostika</span><span class="sxs-lookup"><span data-stu-id="8aef0-171">Supported diagnostics</span></span>

<span data-ttu-id="8aef0-172">V současné době analyzátor zpracovává následující případy:</span><span class="sxs-lookup"><span data-stu-id="8aef0-172">Currently, the analyzer handles the following cases:</span></span>

- <span data-ttu-id="8aef0-173">Použití rozhraní .NET Standard API, které vyvolá <xref:System.PlatformNotSupportedException> (PC001).</span><span class="sxs-lookup"><span data-stu-id="8aef0-173">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
- <span data-ttu-id="8aef0-174">Použití rozhraní .NET Standard API, které není k dispozici v rozhraní .NET Framework 4.6.1 (PC002).</span><span class="sxs-lookup"><span data-stu-id="8aef0-174">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
- <span data-ttu-id="8aef0-175">Použití nativní rozhraní API, které neexistuje v UPW (PC003).</span><span class="sxs-lookup"><span data-stu-id="8aef0-175">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
- <span data-ttu-id="8aef0-176">Použití Delegate.BeginInvoke a EndInvoke API (PC004).</span><span class="sxs-lookup"><span data-stu-id="8aef0-176">Usage of Delegate.BeginInvoke and EndInvoke APIs (PC004).</span></span>
- <span data-ttu-id="8aef0-177">Použití rozhraní API, které je označeno jako zastaralé (DEXXXX).</span><span class="sxs-lookup"><span data-stu-id="8aef0-177">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="8aef0-178">Ci stroj</span><span class="sxs-lookup"><span data-stu-id="8aef0-178">CI machine</span></span>

<span data-ttu-id="8aef0-179">Všechny tyto diagnostiky jsou k dispozici nejen v rozhraní IDE, ale také na příkazovém řádku jako součást vytváření projektu, který zahrnuje server CI.</span><span class="sxs-lookup"><span data-stu-id="8aef0-179">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="8aef0-180">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8aef0-180">Configuration</span></span>

<span data-ttu-id="8aef0-181">Uživatel rozhodne, jak má být diagnostika považována za: jako upozornění, chyby, návrhy nebo vypnutí.</span><span class="sxs-lookup"><span data-stu-id="8aef0-181">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="8aef0-182">Například jako architekt můžete rozhodnout, že problémy s kompatibilitou by měly být považovány za chyby, volání některých zastaralá řešení API generovat upozornění, zatímco jiní pouze generovat návrhy.</span><span class="sxs-lookup"><span data-stu-id="8aef0-182">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="8aef0-183">Můžete nakonfigurovat samostatně pomocí ID diagnostiky a podle projektu.</span><span class="sxs-lookup"><span data-stu-id="8aef0-183">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="8aef0-184">Chcete-li tak učinit v **Průzkumníku řešení**, přejděte do uzlu **Závislosti** v rámci projektu.</span><span class="sxs-lookup"><span data-stu-id="8aef0-184">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="8aef0-185">Rozbalte**analyzátory** >  **závislostí** > uzlů**Microsoft.DotNet.Analyzers.Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="8aef0-185">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="8aef0-186">Klikněte pravým tlačítkem myši na ID diagnostiky, vyberte **nastavit závažnost sady pravidel** a vyberte požadovanou možnost.</span><span class="sxs-lookup"><span data-stu-id="8aef0-186">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

!["Snímek obrazovky Průzkumníka řešení zobrazujícího diagnostiku a automaticky otevíraný dialog se závažností sady pravidel](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="8aef0-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="8aef0-188">See also</span></span>

- <span data-ttu-id="8aef0-189">[Představujeme blogu ANALYZátoru rozhraní API.](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/)</span><span class="sxs-lookup"><span data-stu-id="8aef0-189">[Introducing API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blog post.</span></span>
- <span data-ttu-id="8aef0-190">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video na YouTube.</span><span class="sxs-lookup"><span data-stu-id="8aef0-190">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>

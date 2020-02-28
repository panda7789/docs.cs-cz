---
title: Analyzátor rozhraní .NET API
description: Přečtěte si, jak může analyzátor rozhraní .NET API pomáhat detekovat zastaralá rozhraní API a problémy s kompatibilitou platforem.
author: oliag
ms.date: 02/20/2020
ms.technology: dotnet-standard
ms.openlocfilehash: e214c91f2beebc7f3b3324f4879deba9a5623f86
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156131"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="ce6de-103">Analyzátor rozhraní .NET API</span><span class="sxs-lookup"><span data-stu-id="ce6de-103">.NET API analyzer</span></span>

<span data-ttu-id="ce6de-104">Analyzátor rozhraní .NET API je nástroj Roslyn Analyzer, který zjišťuje potenciální rizika kompatibility pro C# rozhraní API na různých platformách a detekuje volání zastaralých rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ce6de-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="ce6de-105">Může být užitečné pro všechny C# vývojáře v jakékoli fázi vývoje.</span><span class="sxs-lookup"><span data-stu-id="ce6de-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="ce6de-106">Analyzátor API se dodává jako balíček NuGet [Microsoft. dotnet. analyzers. Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span><span class="sxs-lookup"><span data-stu-id="ce6de-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="ce6de-107">Poté, co na něj odkazujete v projektu, automaticky monitoruje kód a indikuje problematické využití rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ce6de-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="ce6de-108">Kliknutím na žárovku můžete také získat návrhy na možné opravy.</span><span class="sxs-lookup"><span data-stu-id="ce6de-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="ce6de-109">Rozevírací nabídka obsahuje možnost pro potlačení upozornění.</span><span class="sxs-lookup"><span data-stu-id="ce6de-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="ce6de-110">Analyzátor rozhraní .NET API je stále předběžnou verzí.</span><span class="sxs-lookup"><span data-stu-id="ce6de-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce6de-111">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="ce6de-111">Prerequisites</span></span>

- <span data-ttu-id="ce6de-112">Visual Studio 2017 a novější verze nebo Visual Studio pro Mac (všechny verze).</span><span class="sxs-lookup"><span data-stu-id="ce6de-112">Visual Studio 2017 and later versions, or Visual Studio for Mac (all versions).</span></span>

## <a name="discover-deprecated-apis"></a><span data-ttu-id="ce6de-113">Zjistit zastaralá rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ce6de-113">Discover deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="ce6de-114">Co jsou zastaralá rozhraní API?</span><span class="sxs-lookup"><span data-stu-id="ce6de-114">What are deprecated APIs?</span></span>

<span data-ttu-id="ce6de-115">Rodina .NET je sada velkých produktů, které se neustále upgradují tak, aby lépe vyhovovaly potřebám zákazníků.</span><span class="sxs-lookup"><span data-stu-id="ce6de-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="ce6de-116">Je přirozené zastaralá některá rozhraní API a nahrazovat je novými.</span><span class="sxs-lookup"><span data-stu-id="ce6de-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="ce6de-117">Rozhraní API se považuje za zastaralé, pokud existuje lepší alternativa.</span><span class="sxs-lookup"><span data-stu-id="ce6de-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="ce6de-118">Jedním ze způsobů, jak informovat o tom, že rozhraní API je zastaralé a nemělo by se používat, je označit ho pomocí atributu <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ce6de-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="ce6de-119">Nevýhodou tohoto přístupu je, že existuje jenom jedno ID diagnostiky pro všechna zastaralá C#rozhraní API (pro, [CS0612](../../csharp/misc/cs0612.md)).</span><span class="sxs-lookup"><span data-stu-id="ce6de-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="ce6de-120">To znamená, že:</span><span class="sxs-lookup"><span data-stu-id="ce6de-120">This means that:</span></span>

- <span data-ttu-id="ce6de-121">U každého případu není možné mít vyhrazené dokumenty.</span><span class="sxs-lookup"><span data-stu-id="ce6de-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="ce6de-122">Není možné potlačit určitou kategorii upozornění.</span><span class="sxs-lookup"><span data-stu-id="ce6de-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="ce6de-123">Můžete potlačit buď všechny, nebo žádné z nich.</span><span class="sxs-lookup"><span data-stu-id="ce6de-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="ce6de-124">Chcete-li informovat uživatele o nové zastaralosti, je nutné aktualizovat odkazované sestavení nebo balíček cílení.</span><span class="sxs-lookup"><span data-stu-id="ce6de-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="ce6de-125">Analyzátor API používá kódy chyb specifické pro rozhraní API, které začínají na DE (což představuje chybu při vyřazení), která umožňuje kontrolu nad zobrazením jednotlivých upozornění.</span><span class="sxs-lookup"><span data-stu-id="ce6de-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="ce6de-126">Zastaralá rozhraní API identifikovaná analyzátorem jsou definována v úložišti [dotnet/Platform-kompatibility](https://github.com/dotnet/platform-compat) .</span><span class="sxs-lookup"><span data-stu-id="ce6de-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="add-the-api-analyzer-to-your-project"></a><span data-ttu-id="ce6de-127">Přidání analyzátoru rozhraní API do projektu</span><span class="sxs-lookup"><span data-stu-id="ce6de-127">Add the API Analyzer to your project</span></span>

1. <span data-ttu-id="ce6de-128">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ce6de-128">Open Visual Studio.</span></span>
2. <span data-ttu-id="ce6de-129">Otevřete projekt, na kterém chcete spustit analyzátor.</span><span class="sxs-lookup"><span data-stu-id="ce6de-129">Open the project you want to run the analyzer on.</span></span>
3. <span data-ttu-id="ce6de-130">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ce6de-130">In **Solution Explorer**, right-click on your project and choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="ce6de-131">(Tato možnost je k dispozici také z nabídky **projekt** .)</span><span class="sxs-lookup"><span data-stu-id="ce6de-131">(This option is also available from the **Project** menu.)</span></span>
4. <span data-ttu-id="ce6de-132">Na kartě Správce balíčků NuGet:</span><span class="sxs-lookup"><span data-stu-id="ce6de-132">On the NuGet Package Manager tab:</span></span>
   1. <span data-ttu-id="ce6de-133">Jako zdroj balíčku vyberte "nuget.org".</span><span class="sxs-lookup"><span data-stu-id="ce6de-133">Select "nuget.org" as the Package source.</span></span>
   2. <span data-ttu-id="ce6de-134">Přejděte na kartu **Procházet** .</span><span class="sxs-lookup"><span data-stu-id="ce6de-134">Go to the **Browse** tab.</span></span>
   3. <span data-ttu-id="ce6de-135">Vyberte možnost **Zahrnout předprodejní verze**.</span><span class="sxs-lookup"><span data-stu-id="ce6de-135">Select **Include prerelease**.</span></span>
   4. <span data-ttu-id="ce6de-136">Vyhledejte **Microsoft. dotnet. analyzers. Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="ce6de-136">Search for **Microsoft.DotNet.Analyzers.Compatibility**.</span></span>
   5. <span data-ttu-id="ce6de-137">Vyberte tento balíček v seznamu.</span><span class="sxs-lookup"><span data-stu-id="ce6de-137">Select that package in the list.</span></span>
   6. <span data-ttu-id="ce6de-138">Vyberte tlačítko **instalovat** .</span><span class="sxs-lookup"><span data-stu-id="ce6de-138">Select the **Install** button.</span></span>
   7. <span data-ttu-id="ce6de-139">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="ce6de-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="use-the-api-analyzer"></a><span data-ttu-id="ce6de-140">Použití analyzátoru rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ce6de-140">Use the API Analyzer</span></span>

<span data-ttu-id="ce6de-141">V případě, že se v kódu používá zastaralé rozhraní API, jako je například <xref:System.Net.WebClient>, analyzátor rozhraní API ho zvýrazní zelenou vlnovkou.</span><span class="sxs-lookup"><span data-stu-id="ce6de-141">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="ce6de-142">Když najedete myší na volání rozhraní API, zobrazí se žárovka s informacemi o zastaralém rozhraní API, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ce6de-142">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

![Snímek obrazovky rozhraní API pro WebClient se zelenou vlnovkou a žárovkou na levé straně](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="ce6de-144">Okno **Seznam chyb** obsahuje upozornění s jedinečným ID na zastaralé rozhraní API, jak je znázorněno v následujícím příkladu (`DE004`):</span><span class="sxs-lookup"><span data-stu-id="ce6de-144">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span>

<span data-ttu-id="ce6de-145">![Snímek obrazovky okna Seznam chyb zobrazující ID a popis upozornění](media/api-analyzer/warnings-id-and-descriptions.jpg "Seznam chyb okno, které obsahuje upozornění.")</span><span class="sxs-lookup"><span data-stu-id="ce6de-145">!["Screenshot of the Error List window showing warning's ID and description"](media/api-analyzer/warnings-id-and-descriptions.jpg "Error List window that includes warnings.")</span></span>

<span data-ttu-id="ce6de-146">Kliknutím na ID přejdete na webovou stránku s podrobnými informacemi o tom, proč se rozhraní API zastaralo, a návrhy týkající se alternativních rozhraní API, která se dají použít.</span><span class="sxs-lookup"><span data-stu-id="ce6de-146">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="ce6de-147">Všechna upozornění lze potlačit kliknutím pravým tlačítkem na zvýrazněný člen a výběrem možnosti **potlačit \<ID diagnostiky >** .</span><span class="sxs-lookup"><span data-stu-id="ce6de-147">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="ce6de-148">Existují dva způsoby, jak potlačit upozornění:</span><span class="sxs-lookup"><span data-stu-id="ce6de-148">There are two ways to suppress warnings:</span></span>

- [<span data-ttu-id="ce6de-149">místně (ve zdroji)</span><span class="sxs-lookup"><span data-stu-id="ce6de-149">locally (in source)</span></span>](#suppress-warnings-locally)
- <span data-ttu-id="ce6de-150">[globálně (v souboru potlačení)](#suppress-warnings-globally) – doporučeno</span><span class="sxs-lookup"><span data-stu-id="ce6de-150">[globally (in a suppression file)](#suppress-warnings-globally) - recommended</span></span>

### <a name="suppress-warnings-locally"></a><span data-ttu-id="ce6de-151">Potlačit upozornění místně</span><span class="sxs-lookup"><span data-stu-id="ce6de-151">Suppress warnings locally</span></span>

<span data-ttu-id="ce6de-152">Chcete-li potlačit upozornění místně, klikněte pravým tlačítkem na člen, pro který chcete potlačit upozornění, a pak vyberte **rychlé akce a refaktoring** > **potlačit *ID diagnostiky*\<ID diagnostiky >**  > **ve zdroji**.</span><span class="sxs-lookup"><span data-stu-id="ce6de-152">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="ce6de-153">Do zdrojového kódu je v definovaném oboru přidána direktiva preprocesoru upozornění [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) : !["snímek obrazovky s kódem s rámcem #pragma vypnutí upozornění" disable "](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="ce6de-153">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppress-warnings-globally"></a><span data-ttu-id="ce6de-154">Potlačit upozornění globálně</span><span class="sxs-lookup"><span data-stu-id="ce6de-154">Suppress warnings globally</span></span>

<span data-ttu-id="ce6de-155">Chcete-li potlačit upozornění globálně, klikněte pravým tlačítkem na člen, pro který chcete potlačit upozornění, a pak vyberte **rychlé akce a refaktoring** > **potlačit *ID diagnostiky*\<ID diagnostiky >**  > **v souboru potlačení**.</span><span class="sxs-lookup"><span data-stu-id="ce6de-155">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

![Snímek obrazovky rozhraní API pro WebClient se zelenou vlnovkou a žárovkou na levé straně](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="ce6de-157">Po prvním potlačení se do projektu přidá soubor *GlobalSuppressions.cs* .</span><span class="sxs-lookup"><span data-stu-id="ce6de-157">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="ce6de-158">K tomuto souboru se připojí nová globální potlačení.</span><span class="sxs-lookup"><span data-stu-id="ce6de-158">New global suppressions are appended to this file.</span></span>

![Snímek obrazovky rozhraní API pro WebClient se zelenou vlnovkou a žárovkou na levé straně](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="ce6de-160">Globální potlačení je doporučený způsob, jak zajistit konzistenci využití rozhraní API napříč projekty.</span><span class="sxs-lookup"><span data-stu-id="ce6de-160">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discover-cross-platform-issues"></a><span data-ttu-id="ce6de-161">Objevte problémy s více platformami</span><span class="sxs-lookup"><span data-stu-id="ce6de-161">Discover cross-platform issues</span></span>

<span data-ttu-id="ce6de-162">Podobně jako zastaralá rozhraní API nástroj Analyzer identifikuje všechna rozhraní API, která nejsou pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="ce6de-162">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="ce6de-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> například funguje v systému Windows, ale ne v systémech Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="ce6de-163">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="ce6de-164">ID diagnostiky se zobrazí v okně **Seznam chyb** .</span><span class="sxs-lookup"><span data-stu-id="ce6de-164">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="ce6de-165">Toto upozornění můžete potlačit tak, že kliknete pravým tlačítkem a vyberete **rychlé akce a refaktoringy**.</span><span class="sxs-lookup"><span data-stu-id="ce6de-165">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="ce6de-166">Na rozdíl od zastaralých případů, kde máte dvě možnosti (můžete buď dál používat zastaralé členy a potlačit upozornění, nebo je nepoužívat vůbec), pokud vyvíjíte kód jenom pro určité platformy, můžete potlačit všechna upozornění pro všechny ostatní platformy, které nepoužíváte. Naplánujte spuštění kódu v.</span><span class="sxs-lookup"><span data-stu-id="ce6de-166">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="ce6de-167">Chcete-li to provést, stačí upravit soubor projektu a přidat vlastnost `PlatformCompatIgnore`, která obsahuje seznam všech platforem, které mají být ignorovány.</span><span class="sxs-lookup"><span data-stu-id="ce6de-167">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="ce6de-168">Přípustné hodnoty jsou: `Linux`, `macOS`a `Windows`.</span><span class="sxs-lookup"><span data-stu-id="ce6de-168">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="ce6de-169">Pokud váš kód cílí na více platforem a chcete využít výhod rozhraní API, které není na některých z nich podporováno, můžete tuto část kódu chránit pomocí příkazu `if`:</span><span class="sxs-lookup"><span data-stu-id="ce6de-169">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="ce6de-170">Můžete také podmíněně kompilovat na cílové rozhraní nebo operační systém, ale v tuto chvíli je nutné provést [ručně](../frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="ce6de-170">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="ce6de-171">Podporovaná Diagnostika</span><span class="sxs-lookup"><span data-stu-id="ce6de-171">Supported diagnostics</span></span>

<span data-ttu-id="ce6de-172">Analyzátor v současné době zpracovává následující případy:</span><span class="sxs-lookup"><span data-stu-id="ce6de-172">Currently, the analyzer handles the following cases:</span></span>

- <span data-ttu-id="ce6de-173">Využití rozhraní .NET Standard API, které vyvolá <xref:System.PlatformNotSupportedException> (PC001).</span><span class="sxs-lookup"><span data-stu-id="ce6de-173">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
- <span data-ttu-id="ce6de-174">Použití rozhraní .NET Standard API, které není k dispozici v .NET Framework 4.6.1 (PC002).</span><span class="sxs-lookup"><span data-stu-id="ce6de-174">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
- <span data-ttu-id="ce6de-175">Použití nativního rozhraní API, které neexistuje v UWP (PC003).</span><span class="sxs-lookup"><span data-stu-id="ce6de-175">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
- <span data-ttu-id="ce6de-176">Použití rozhraní API Delegate. BeginInvoke a EndInvoke u delegujících (PC004).</span><span class="sxs-lookup"><span data-stu-id="ce6de-176">Usage of Delegate.BeginInvoke and EndInvoke APIs (PC004).</span></span>
- <span data-ttu-id="ce6de-177">Použití rozhraní API, které je označeno jako zastaralé (pro odstranění XXXX).</span><span class="sxs-lookup"><span data-stu-id="ce6de-177">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="ce6de-178">Počítač CI</span><span class="sxs-lookup"><span data-stu-id="ce6de-178">CI machine</span></span>

<span data-ttu-id="ce6de-179">Všechna tato diagnostika jsou k dispozici nejen v integrovaném vývojovém prostředí (IDE), ale také na příkazovém řádku jako součást sestavení projektu, který zahrnuje server CI.</span><span class="sxs-lookup"><span data-stu-id="ce6de-179">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="ce6de-180">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ce6de-180">Configuration</span></span>

<span data-ttu-id="ce6de-181">Uživatel rozhodne, jak by měla být Diagnostika zpracována: jako upozornění, chyby, návrhy nebo je vypnuto.</span><span class="sxs-lookup"><span data-stu-id="ce6de-181">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="ce6de-182">Například jako architekt se můžete rozhodnout, že problémy s kompatibilitou by měly být považovány za chyby, volání některých zastaralých rozhraní API generují upozornění, zatímco ostatní generují pouze návrhy.</span><span class="sxs-lookup"><span data-stu-id="ce6de-182">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="ce6de-183">Můžete ji nakonfigurovat samostatně podle ID diagnostiky a podle projektu.</span><span class="sxs-lookup"><span data-stu-id="ce6de-183">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="ce6de-184">Provedete to tak, že v **Průzkumník řešení**přejdete do uzlu **závislosti** v projektu.</span><span class="sxs-lookup"><span data-stu-id="ce6de-184">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="ce6de-185">Rozbalte uzel **závislosti** > **analyzátory** > **Microsoft. dotnet. analyzers. Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="ce6de-185">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="ce6de-186">Klikněte pravým tlačítkem na ID diagnostiky, vyberte **nastavit závažnost sady pravidel** a vyberte požadovanou možnost.</span><span class="sxs-lookup"><span data-stu-id="ce6de-186">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

![Snímek obrazovky Průzkumník řešení znázorňující diagnostiku a automaticky otevírané okno se závažností sady pravidel "](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="ce6de-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce6de-188">See also</span></span>

- <span data-ttu-id="ce6de-189">Představujeme Blogový příspěvek k [analyzátoru API](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) .</span><span class="sxs-lookup"><span data-stu-id="ce6de-189">[Introducing API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blog post.</span></span>
- <span data-ttu-id="ce6de-190">Ukázkové video [analyzátoru API](https://youtu.be/eeBEahYXGd0) na YouTube</span><span class="sxs-lookup"><span data-stu-id="ce6de-190">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>

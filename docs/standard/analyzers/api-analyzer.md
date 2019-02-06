---
title: Analyzátor rozhraní API .NET
description: Zjistěte, jak analyzátor rozhraní API .NET vám může pomoct detekovat zastaralé rozhraní API a problémy s kompatibilitou platformy.
author: oliag
ms.author: mairaw
ms.date: 05/31/2018
ms.technology: dotnet-standard
ms.openlocfilehash: d27e5299ad9b1a3dcd89d5a947d91f06a54549e2
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759129"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="0f30b-103">Analyzátor rozhraní API .NET</span><span class="sxs-lookup"><span data-stu-id="0f30b-103">.NET API analyzer</span></span>

<span data-ttu-id="0f30b-104">Analyzátor rozhraní API .NET je Roslyn analyzátor, který zjišťuje potenciální rizika kompatibility pro C# rozhraní API na různých platformách a detekuje volání rozhraní API nepoužívané.</span><span class="sxs-lookup"><span data-stu-id="0f30b-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="0f30b-105">Může být užitečné pro všechny C# vývojáři v jakékoli fázi vývoje.</span><span class="sxs-lookup"><span data-stu-id="0f30b-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="0f30b-106">Analyzátor rozhraní API se dodává jako balíček NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span><span class="sxs-lookup"><span data-stu-id="0f30b-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="0f30b-107">Po odkazovat v projektu, automaticky sleduje kód a určuje problematických použití rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="0f30b-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="0f30b-108">Kliknutím na žárovku můžete také získat návrhy na možné opravy.</span><span class="sxs-lookup"><span data-stu-id="0f30b-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="0f30b-109">V rozevírací nabídce zahrnuje možnost potlačit upozornění.</span><span class="sxs-lookup"><span data-stu-id="0f30b-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="0f30b-110">Analyzátor rozhraní .NET API je stále o předběžnou verzi.</span><span class="sxs-lookup"><span data-stu-id="0f30b-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0f30b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f30b-111">Prerequisites</span></span>

* <span data-ttu-id="0f30b-112">Visual Studio 2017 nebo Visual Studio pro Mac (všechny verze).</span><span class="sxs-lookup"><span data-stu-id="0f30b-112">Visual Studio 2017 or Visual Studio for Mac (all versions).</span></span>

## <a name="discovering-deprecated-apis"></a><span data-ttu-id="0f30b-113">Zjišťování zastaralá rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0f30b-113">Discovering deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="0f30b-114">Co jsou zastaralé rozhraní API?</span><span class="sxs-lookup"><span data-stu-id="0f30b-114">What are deprecated APIs?</span></span>

<span data-ttu-id="0f30b-115">Řada .NET je sada velké produkty, které jsou neustále aktualizovány na dokázaly lépe vyhovět potřebám zákazníků.</span><span class="sxs-lookup"><span data-stu-id="0f30b-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="0f30b-116">Je přirozené přestat používat některá rozhraní API a je nahradit za nové.</span><span class="sxs-lookup"><span data-stu-id="0f30b-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="0f30b-117">Rozhraní API se považuje za zastaralý, lepší alternativou existuje.</span><span class="sxs-lookup"><span data-stu-id="0f30b-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="0f30b-118">Jedním ze způsobů informovat, že rozhraní API je zastaralý a neměl by se používat je označit pomocí <xref:System.ObsoleteAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="0f30b-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="0f30b-119">Nevýhody tohoto přístupu je, že existuje pouze jedno ID diagnostiky pro všechny zastaralé rozhraní API (pro C#, [CS0612](../../csharp/misc/cs0612.md)).</span><span class="sxs-lookup"><span data-stu-id="0f30b-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="0f30b-120">To znamená, že:</span><span class="sxs-lookup"><span data-stu-id="0f30b-120">This means that:</span></span>
- <span data-ttu-id="0f30b-121">Není možné mít vyhrazené dokumenty pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="0f30b-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="0f30b-122">Není možné potlačit určité upozornění.</span><span class="sxs-lookup"><span data-stu-id="0f30b-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="0f30b-123">Můžete potlačit všech nebo žádných z nich.</span><span class="sxs-lookup"><span data-stu-id="0f30b-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="0f30b-124">Pokud chcete informovat uživatele o nové vyřazení odkazované sestavení nebo cílení balíčku musí být aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="0f30b-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="0f30b-125">Analyzátor rozhraní API používá rozhraní API specifické chybové kódy, které začínají s DE (což je zkratka pro vyřazení chyba), která umožňuje ovládat zobrazení jednotlivých upozornění.</span><span class="sxs-lookup"><span data-stu-id="0f30b-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="0f30b-126">Zastaralé rozhraní API identifikovat analyzátor jsou definovány v [dotnet/platform – compat](https://github.com/dotnet/platform-compat) úložiště.</span><span class="sxs-lookup"><span data-stu-id="0f30b-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="using-the-api-analyzer"></a><span data-ttu-id="0f30b-127">Analyzátor rozhraní API pomocí</span><span class="sxs-lookup"><span data-stu-id="0f30b-127">Using the API Analyzer</span></span>

<span data-ttu-id="0f30b-128">Když zastaralé rozhraní API, například <xref:System.Net.WebClient>, se používá v kódu, analyzátor rozhraní API zvýrazní ho s řádkem zelenou vlnovkou.</span><span class="sxs-lookup"><span data-stu-id="0f30b-128">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="0f30b-129">Při najetí myší na volání rozhraní API, zobrazí se žárovka s informacemi o vyřazení podpory rozhraní API, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0f30b-129">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

!["Snímek obrazovky WebClient rozhraní API s zelenou vlnovkou čáru a návrhy na levé straně"](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="0f30b-131">**Seznam chyb** okno obsahuje upozornění s jedinečným ID rozhraní API nepoužívané, jak je znázorněno v následujícím příkladu (`DE004`):</span><span class="sxs-lookup"><span data-stu-id="0f30b-131">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span> 

!["Snímek obrazovky okna Seznam chyb, které se zobrazují upozornění na ID a description"](media/api-analyzer/warnings.jpg)

<span data-ttu-id="0f30b-133">Po kliknutí na ID, přejděte na webové stránce s podrobnými informacemi o Proč se přestala nabízet rozhraní API a návrhy týkající se alternativní rozhraní API, která lze použít.</span><span class="sxs-lookup"><span data-stu-id="0f30b-133">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="0f30b-134">Všechna upozornění můžete potlačit pomocí pravým tlačítkem na zvýrazněné člena a výběrem **potlačit \<ID diagnostiky >**.</span><span class="sxs-lookup"><span data-stu-id="0f30b-134">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="0f30b-135">Existují dva způsoby, jak potlačit upozornění:</span><span class="sxs-lookup"><span data-stu-id="0f30b-135">There are two ways to suppress warnings:</span></span> 

* [<span data-ttu-id="0f30b-136">místně (ve zdroji)</span><span class="sxs-lookup"><span data-stu-id="0f30b-136">locally (in source)</span></span>](#suppressing-warnings-locally)
* <span data-ttu-id="0f30b-137">[(v souboru potlačení)](#suppressing-warnings-globally) – doporučené</span><span class="sxs-lookup"><span data-stu-id="0f30b-137">[globally (in a suppression file)](#suppressing-warnings-globally) - recommended</span></span>

### <a name="suppressing-warnings-locally"></a><span data-ttu-id="0f30b-138">Potlačení upozornění místně</span><span class="sxs-lookup"><span data-stu-id="0f30b-138">Suppressing warnings locally</span></span>

<span data-ttu-id="0f30b-139">Potlačení upozornění místně, klikněte pravým tlačítkem na člena chcete potlačit upozornění pro a pak vyberte **rychlé akce a Refaktoringy** > **potlačit *ID diagnostiky* \<ID diagnostiky >** > **ve zdroji**.</span><span class="sxs-lookup"><span data-stu-id="0f30b-139">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="0f30b-140">[#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) upozornění direktivy preprocesoru je přidán do zdrojového kódu v rámci definice: !["Snímek kódu, které jsou uvedeny s zakázat varování #pragma"](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f30b-140">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppressing-warnings-globally"></a><span data-ttu-id="0f30b-141">Potlačení upozornění globálně</span><span class="sxs-lookup"><span data-stu-id="0f30b-141">Suppressing warnings globally</span></span>

<span data-ttu-id="0f30b-142">Potlačit upozornění globálně, klikněte pravým tlačítkem na člena chcete potlačit upozornění pro a pak vyberte **rychlé akce a Refaktoringy** > **potlačit *ID diagnostiky* \<ID diagnostiky >** > **v souboru potlačení**.</span><span class="sxs-lookup"><span data-stu-id="0f30b-142">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

!["Snímek obrazovky WebClient rozhraní API s zelenou vlnovkou čáru a návrhy na levé straně"](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="0f30b-144">A *GlobalSuppressions.cs* přidá soubor do projektu po první potlačení.</span><span class="sxs-lookup"><span data-stu-id="0f30b-144">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="0f30b-145">Nové globální potlačení se připojují k tomuto souboru.</span><span class="sxs-lookup"><span data-stu-id="0f30b-145">New global suppressions are appended to this file.</span></span>

!["Snímek obrazovky WebClient rozhraní API s zelenou vlnovkou čáru a návrhy na levé straně"](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="0f30b-147">Globální potlačení je doporučeným způsobem, jak zajistit konzistenci použití rozhraní API napříč projekty.</span><span class="sxs-lookup"><span data-stu-id="0f30b-147">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discovering-cross-platform-issues"></a><span data-ttu-id="0f30b-148">Zjišťování problémů napříč platformami</span><span class="sxs-lookup"><span data-stu-id="0f30b-148">Discovering cross-platform issues</span></span>

<span data-ttu-id="0f30b-149">Podobně jako zastaralé rozhraní API, analyzátor identifikuje všechna rozhraní API, které nejsou napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="0f30b-149">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="0f30b-150">Například <xref:System.Console.WindowWidth?displayProperty=nameWithType> funguje na Windows, ale není v Linuxu a macOS.</span><span class="sxs-lookup"><span data-stu-id="0f30b-150">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="0f30b-151">ID diagnostiky se zobrazí v **seznam chyb** okna.</span><span class="sxs-lookup"><span data-stu-id="0f30b-151">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="0f30b-152">Že upozornění můžete potlačit kliknutím pravým tlačítkem myši a vyberete **rychlé akce a Refaktoringy**.</span><span class="sxs-lookup"><span data-stu-id="0f30b-152">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="0f30b-153">Na rozdíl od vyřazení případy, které mají dvě možnosti (nadále používat zastaralé člena a potlačit upozornění nebo není vůbec používat), zde vyvíjíte kódu pouze pro určité platformy, můžete potlačit všechna upozornění pro jiné platformy, ne plán pro spouštění vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="0f30b-153">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="0f30b-154">K tomu stačí úpravou souboru projektu a přidejte `PlatformCompatIgnore` vlastnost, která obsahuje seznam všech platformách se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="0f30b-154">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="0f30b-155">Přípustné hodnoty jsou: `Linux`, `macOS`, a `Windows`.</span><span class="sxs-lookup"><span data-stu-id="0f30b-155">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="0f30b-156">Pokud váš kód cílí na různé platformy a chcete využít rozhraní API není podporována na některé z nich, můžete chránit tuto část kódu pomocí `if` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="0f30b-156">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="0f30b-157">Můžete také podmíněné kompilaci na cílové rozhraní framework nebo operační systém, ale aktuálně je potřeba udělat [ručně](../frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="0f30b-157">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="0f30b-158">Podporované diagnostiky</span><span class="sxs-lookup"><span data-stu-id="0f30b-158">Supported diagnostics</span></span>

<span data-ttu-id="0f30b-159">V současné době analyzátor zpracovává následujících případech:</span><span class="sxs-lookup"><span data-stu-id="0f30b-159">Currently, the analyzer handles the following cases:</span></span>

* <span data-ttu-id="0f30b-160">Použití standardních rozhraní API .NET, která vyvolá <xref:System.PlatformNotSupportedException> (PC001).</span><span class="sxs-lookup"><span data-stu-id="0f30b-160">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
* <span data-ttu-id="0f30b-161">Použití standardních rozhraní API .NET, která není k dispozici v rozhraní .NET Framework 4.6.1 (PC002).</span><span class="sxs-lookup"><span data-stu-id="0f30b-161">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
* <span data-ttu-id="0f30b-162">Použití nativních rozhraní API, která neexistuje v UPW (PC003).</span><span class="sxs-lookup"><span data-stu-id="0f30b-162">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
* <span data-ttu-id="0f30b-163">Využití rozhraní API, která je označena jako zastaralá (DEXXXX).</span><span class="sxs-lookup"><span data-stu-id="0f30b-163">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="0f30b-164">Položky konfigurace počítače</span><span class="sxs-lookup"><span data-stu-id="0f30b-164">CI machine</span></span>

<span data-ttu-id="0f30b-165">Všechny tyto Diagnostika je k dispozici pouze v rozhraní IDE, ale také v příkazovém řádku jako část sestavení vašeho projektu, která obsahuje CI server.</span><span class="sxs-lookup"><span data-stu-id="0f30b-165">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="0f30b-166">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="0f30b-166">Configuration</span></span>

<span data-ttu-id="0f30b-167">Uživatel rozhodne, jak by měly být považovány Diagnostika: jako upozornění, chyby, návrhy nebo jej nejprve vypnout.</span><span class="sxs-lookup"><span data-stu-id="0f30b-167">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="0f30b-168">Například jako architekt, se můžete rozhodnout, že problémy s kompatibilitou by měla být považována za chyby, volání některá rozhraní API nepoužívané vygenerovat upozornění, zatímco ostatní návrhy generovat jenom.</span><span class="sxs-lookup"><span data-stu-id="0f30b-168">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="0f30b-169">To můžete nakonfigurovat samostatně podle ID diagnostiky a projektu.</span><span class="sxs-lookup"><span data-stu-id="0f30b-169">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="0f30b-170">Provedete to tak v **Průzkumníku řešení**, přejděte **závislosti** uzlu projektu.</span><span class="sxs-lookup"><span data-stu-id="0f30b-170">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="0f30b-171">Rozbalte uzly **závislosti** > **analyzátory** > **Microsoft.DotNet.Analyzers.Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="0f30b-171">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="0f30b-172">Klikněte pravým tlačítkem na ID diagnostiky, vyberte **nastavit závažnost pravidla nastavit** a vyberte požadovanou možnost.</span><span class="sxs-lookup"><span data-stu-id="0f30b-172">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

!["Snímek Průzkumník řešení zobrazující diagnostiky a zobrazení dialogu se nastavit závažnost pravidla"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="0f30b-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f30b-174">See also</span></span>

- <span data-ttu-id="0f30b-175">[Úvod do rozhraní API analyzátor](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) blogový příspěvek.</span><span class="sxs-lookup"><span data-stu-id="0f30b-175">[Introducing API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) blog post.</span></span>
- <span data-ttu-id="0f30b-176">[Analyzátor rozhraní API](https://youtu.be/eeBEahYXGd0) ukázkové video na YouTube.</span><span class="sxs-lookup"><span data-stu-id="0f30b-176">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>

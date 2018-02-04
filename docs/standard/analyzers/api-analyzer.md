---
title: "Analyzátor rozhraní API .NET"
description: "Zjistěte, jak analyzátor rozhraní API .NET vám mohou pomoci rozpoznat nepoužívané rozhraní API a problémy s kompatibilitou platformy."
author: oliag
ms.author: mairaw
ms.date: 01/30/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.openlocfilehash: 81ab7e32b2af6048d822243226f1054ebd1ca419
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="net-api-analyzer"></a><span data-ttu-id="f97f6-103">Analyzátor rozhraní API .NET</span><span class="sxs-lookup"><span data-stu-id="f97f6-103">.NET API analyzer</span></span>

<span data-ttu-id="f97f6-104">Analyzátor rozhraní API .NET je Roslyn analyzátor, který zjistí potenciální kompatibility rizika pro rozhraní API jazyka C# na různých platformách a zjistí volání rozhraní API pro zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f97f6-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="f97f6-105">Může být užitečné pro všechny vývojáře jazyka C# v jakékoli fázi vývoje.</span><span class="sxs-lookup"><span data-stu-id="f97f6-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="f97f6-106">Analyzátor rozhraní API se dodává jako balíčku NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span><span class="sxs-lookup"><span data-stu-id="f97f6-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="f97f6-107">Po jeho odkazujete v projektu, automaticky monitoruje kód a označuje problematické využití rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="f97f6-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="f97f6-108">Kliknutím na žárovky můžete také získat návrhy na možné opravy.</span><span class="sxs-lookup"><span data-stu-id="f97f6-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="f97f6-109">V rozevírací nabídce zahrnuje možnost potlačit upozornění.</span><span class="sxs-lookup"><span data-stu-id="f97f6-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="f97f6-110">Analyzátor .NET API je stále předběžné verze.</span><span class="sxs-lookup"><span data-stu-id="f97f6-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f97f6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f97f6-111">Prerequisites</span></span>

* <span data-ttu-id="f97f6-112">Visual Studio 2017 nebo Visual Studio pro Mac (všechny verze).</span><span class="sxs-lookup"><span data-stu-id="f97f6-112">Visual Studio 2017 or Visual Studio for Mac (all versions).</span></span>

## <a name="discovering-deprecated-apis"></a><span data-ttu-id="f97f6-113">Zjišťování zastaralá rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f97f6-113">Discovering deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="f97f6-114">Co jsou zastaralé rozhraní API?</span><span class="sxs-lookup"><span data-stu-id="f97f6-114">What are deprecated APIs?</span></span>

<span data-ttu-id="f97f6-115">Řada .NET je sada velké produkty, které jsou neustále aktualizovány na verzi lépe obsluhovat požadavky zákazníka.</span><span class="sxs-lookup"><span data-stu-id="f97f6-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="f97f6-116">Je přirozené přestat používat některé rozhraní API a nahradíte je nové.</span><span class="sxs-lookup"><span data-stu-id="f97f6-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="f97f6-117">Rozhraní API považuje za zastaralý lepší alternativou existuje.</span><span class="sxs-lookup"><span data-stu-id="f97f6-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="f97f6-118">Je možné informovat o tom, že rozhraní API je zastaralá a neměl by se používat k označení její <xref:System.ObsoleteAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="f97f6-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="f97f6-119">Nevýhodou tento přístup je, že existuje jenom jeden diagnostiky ID pro všechna rozhraní API zastaralé (C# je [CS0612](../../csharp/misc/cs0612.md)).</span><span class="sxs-lookup"><span data-stu-id="f97f6-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="f97f6-120">To znamená, že:</span><span class="sxs-lookup"><span data-stu-id="f97f6-120">This means that:</span></span>
- <span data-ttu-id="f97f6-121">Je možné mít vyhrazený dokumenty pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="f97f6-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="f97f6-122">Není možné potlačit určité kategorie upozornění.</span><span class="sxs-lookup"><span data-stu-id="f97f6-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="f97f6-123">Můžete potlačit všech nebo žádných z nich.</span><span class="sxs-lookup"><span data-stu-id="f97f6-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="f97f6-124">K informovat uživatele o nové vyřazení, odkazovaná sestavení nebo cílení na balíček musí aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="f97f6-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="f97f6-125">Analyzátor rozhraní API používá rozhraní API specifické chybové kódy, které začít s DE (což znamená vyřazení chyby), což umožňuje kontrolu nad zobrazení jednotlivých upozornění.</span><span class="sxs-lookup"><span data-stu-id="f97f6-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="f97f6-126">Zastaralá rozhraní API identifikovaný nástroje analyzer jsou definovány v [dotnet nebo platformu compat](https://github.com/dotnet/platform-compat) úložišti.</span><span class="sxs-lookup"><span data-stu-id="f97f6-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="using-the-api-analyzer"></a><span data-ttu-id="f97f6-127">Pomocí Analyzéru rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f97f6-127">Using the API Analyzer</span></span>

<span data-ttu-id="f97f6-128">Při nepoužívané rozhraní API, například <xref:System.Net.WebClient>, se používá v kódu, API Analyzer zvýrazní ho s zelenou vlnovkou řádku.</span><span class="sxs-lookup"><span data-stu-id="f97f6-128">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="f97f6-129">Po přesunutí ukazatele myši volání rozhraní API, zobrazí se žárovky s informacemi o vyřazení rozhraní API, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f97f6-129">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

!["Snímek WebClient rozhraní API s zelenou vlnovkou řádku a žárovky na levé straně"](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="f97f6-131">**Seznam chyb** okno obsahuje upozornění s jedinečným ID za zastaralé rozhraní API, jak je znázorněno v následujícím příkladu (`DE004`):</span><span class="sxs-lookup"><span data-stu-id="f97f6-131">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span> 

!["Snímek obrazovky zobrazující upozornění na ID a popis v okně Seznam chyb"](media/api-analyzer/warnings.jpg)

<span data-ttu-id="f97f6-133">Kliknutím na ID, přejděte na webovou stránku s podrobnými informacemi o proč byla zastaralá rozhraní API a návrhy týkající se alternativní rozhraní API, který lze použít.</span><span class="sxs-lookup"><span data-stu-id="f97f6-133">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="f97f6-134">Všechna upozornění, lze potlačit kliknutím pravým tlačítkem na zvýrazněné člen a výběrem **potlačit \<ID diagnostiky >**.</span><span class="sxs-lookup"><span data-stu-id="f97f6-134">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="f97f6-135">Potlačení upozornění dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="f97f6-135">There are two ways to suppress warnings:</span></span> 

* [<span data-ttu-id="f97f6-136">místně (ve zdroji)</span><span class="sxs-lookup"><span data-stu-id="f97f6-136">locally (in source)</span></span>](#suppressing-warnings-locally)
* <span data-ttu-id="f97f6-137">[globálně (v souboru potlačení)](#suppressing-warnings-globally) – doporučené</span><span class="sxs-lookup"><span data-stu-id="f97f6-137">[globally (in a suppression file)](#suppressing-warnings-globally) - recommended</span></span>

### <a name="suppressing-warnings-locally"></a><span data-ttu-id="f97f6-138">Potlačení upozornění místně</span><span class="sxs-lookup"><span data-stu-id="f97f6-138">Suppressing warnings locally</span></span>

<span data-ttu-id="f97f6-139">Potlačit upozornění místně, klikněte pravým tlačítkem na člena chcete potlačení upozornění pro a pak vyberte **rychlé akce a refaktoring** > **potlačit *ID diagnostiky* \<ID diagnostiky >** > **ve zdroji**.</span><span class="sxs-lookup"><span data-stu-id="f97f6-139">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="f97f6-140">[#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) upozornění direktivy preprocesoru se přidá do vašeho zdrojového kódu v oboru definován: !["Snímek obrazovky kódu služby rámcové s #pragma zakáže upozornění"](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="f97f6-140">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppressing-warnings-globally"></a><span data-ttu-id="f97f6-141">Potlačení upozornění globální</span><span class="sxs-lookup"><span data-stu-id="f97f6-141">Suppressing warnings globally</span></span>

<span data-ttu-id="f97f6-142">Potlačit upozornění globálně, klikněte pravým tlačítkem na člena chcete potlačení upozornění pro a pak vyberte **rychlé akce a refaktoring** > **potlačit *ID diagnostiky* \<ID diagnostiky >** > **v souboru potlačení**.</span><span class="sxs-lookup"><span data-stu-id="f97f6-142">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

!["Snímek WebClient rozhraní API s zelenou vlnovkou řádku a žárovky na levé straně"](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="f97f6-144">A *GlobalSuppressions.cs* soubor je přidán do projektu po první potlačení.</span><span class="sxs-lookup"><span data-stu-id="f97f6-144">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="f97f6-145">Nové globální suppressions se připojují k tomuto souboru.</span><span class="sxs-lookup"><span data-stu-id="f97f6-145">New global suppressions are appended to this file.</span></span>

!["Snímek WebClient rozhraní API s zelenou vlnovkou řádku a žárovky na levé straně"](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="f97f6-147">Globální potlačení je doporučeným způsobem, aby byla zaručena konzistence využití rozhraní API napříč projekty.</span><span class="sxs-lookup"><span data-stu-id="f97f6-147">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discovering-cross-platform-issues"></a><span data-ttu-id="f97f6-148">Zjišťování problémů a platformy</span><span class="sxs-lookup"><span data-stu-id="f97f6-148">Discovering cross-platform issues</span></span>

<span data-ttu-id="f97f6-149">Podobně jako zastaralé rozhraní API, nástroje analyzer identifikuje všechna rozhraní API, které nejsou napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="f97f6-149">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="f97f6-150">Například <xref:System.Console.WindowWidth?displayProperty=nameWithType> funguje v systému Windows, ale ne na Linuxu a systému macOS.</span><span class="sxs-lookup"><span data-stu-id="f97f6-150">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="f97f6-151">ID diagnostiky se zobrazí v **seznam chyb** okno.</span><span class="sxs-lookup"><span data-stu-id="f97f6-151">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="f97f6-152">Že upozornění můžete potlačit tím, že kliknete pravým tlačítkem a vyberete **rychlé akce a refaktoring**.</span><span class="sxs-lookup"><span data-stu-id="f97f6-152">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="f97f6-153">Na rozdíl od vyřazení případy, kdy máte dvě možnosti (zachovat pomocí nepoužívané člen a potlačení upozornění nebo ji nepoužívat vůbec), zde Pokud vyvíjíte kódu jenom pro některé platformy, můžete potlačit všech upozornění pro jiné platformy, ne plán pro spouštění vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="f97f6-153">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="f97f6-154">Uděláte to tak, stačí upravit soubor projektu a přidat `PlatformCompatIgnore` vlastnost, která obsahuje seznam všech platformách budou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="f97f6-154">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="f97f6-155">Možné hodnoty jsou: `Linux`, `MacOSX`, a `Windows`.</span><span class="sxs-lookup"><span data-stu-id="f97f6-155">The accepted values are: `Linux`, `MacOSX`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;MacOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="f97f6-156">Pokud váš kód cílem více platforem a chcete využít výhod rozhraní API není podporována u některých z nich, se můžete chránit část kód `if` příkaz:</span><span class="sxs-lookup"><span data-stu-id="f97f6-156">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="f97f6-157">Můžete také podmíněně zkompilovat na cílový framework nebo operační systém, ale je aktuálně potřeba udělat [ručně](../frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="f97f6-157">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="f97f6-158">Podporované diagnostiky</span><span class="sxs-lookup"><span data-stu-id="f97f6-158">Supported diagnostics</span></span>

<span data-ttu-id="f97f6-159">V současné době analyzátor zpracovává v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="f97f6-159">Currently, the analyzer handles the following cases:</span></span>

* <span data-ttu-id="f97f6-160">Využití .NET standardní API, která vyvolává <xref:System.PlatformNotSupportedException> (PC001).</span><span class="sxs-lookup"><span data-stu-id="f97f6-160">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
* <span data-ttu-id="f97f6-161">Využití .NET standardní API, která není k dispozici na rozhraní .NET Framework 4.6.1 (PC002).</span><span class="sxs-lookup"><span data-stu-id="f97f6-161">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
* <span data-ttu-id="f97f6-162">Použití nativních rozhraní API, která neexistuje v UWP (PC003).</span><span class="sxs-lookup"><span data-stu-id="f97f6-162">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
* <span data-ttu-id="f97f6-163">Využití rozhraní API, která je označena jako zastaralé (DEXXXX).</span><span class="sxs-lookup"><span data-stu-id="f97f6-163">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="f97f6-164">Položky konfigurace počítače</span><span class="sxs-lookup"><span data-stu-id="f97f6-164">CI machine</span></span>

<span data-ttu-id="f97f6-165">Všechny tyto diagnostiky jsou k dispozici pouze v prostředí IDE, ale také na příkazovém řádku jako součást sestavení projektu, který zahrnuje server položek konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f97f6-165">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="f97f6-166">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f97f6-166">Configuration</span></span>

<span data-ttu-id="f97f6-167">Uživatel rozhodne, jak by měly být považovány diagnostiku: upozornění, chyby, návrhy nebo vypnout.</span><span class="sxs-lookup"><span data-stu-id="f97f6-167">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="f97f6-168">Například jako na architekt můžete rozhodnout, že problémy s kompatibilitou by měly být považovány za chyby, volání některé nepoužívané rozhraní API vygenerovat upozornění, zatímco ostatní generovat jenom návrhy.</span><span class="sxs-lookup"><span data-stu-id="f97f6-168">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="f97f6-169">To můžete nakonfigurovat samostatně podle ID diagnostiky a projekt.</span><span class="sxs-lookup"><span data-stu-id="f97f6-169">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="f97f6-170">Uděláte to tak v **Průzkumníku řešení**, přejděte na **závislosti** uzel v projektu.</span><span class="sxs-lookup"><span data-stu-id="f97f6-170">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="f97f6-171">Rozbalte uzly **závislosti** > **analyzátorů** > **Microsoft.DotNet.Analyzers.Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="f97f6-171">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="f97f6-172">Klikněte pravým tlačítkem na ID diagnostiky, vyberte **nastavit závažnost nastavit pravidlo** a vyberte požadovanou možnost.</span><span class="sxs-lookup"><span data-stu-id="f97f6-172">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

!["Snímek obrazovky zobrazující diagnostiky a automaticky otevíraný dialog se závažností nastavit pravidlo Průzkumníku řešení"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="f97f6-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="f97f6-174">See also</span></span>

* <span data-ttu-id="f97f6-175">[Úvod do rozhraní API analyzátor](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) příspěvku na blogu.</span><span class="sxs-lookup"><span data-stu-id="f97f6-175">[Introducing API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) blog post.</span></span>
* <span data-ttu-id="f97f6-176">[Rozhraní API analyzátor](https://youtu.be/eeBEahYXGd0) ukázku video na YouTube.</span><span class="sxs-lookup"><span data-stu-id="f97f6-176">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>

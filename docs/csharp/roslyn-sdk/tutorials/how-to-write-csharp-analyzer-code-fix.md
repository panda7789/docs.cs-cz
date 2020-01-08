---
title: 'Kurz: vytvoření prvního analyzátoru a opravy kódu'
description: V tomto kurzu najdete podrobné pokyny k sestavení analyzátoru a opravy kódu pomocí sady .NET Compiler SDK (rozhraní Roslyn API).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: 99401e74588088d56b3fbd916e050f5d468722a1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346942"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="dbcd2-103">Kurz: vytvoření prvního analyzátoru a opravy kódu</span><span class="sxs-lookup"><span data-stu-id="dbcd2-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="dbcd2-104">Sada .NET Compiler Platform SDK poskytuje nástroje, které potřebujete k vytváření vlastních upozornění, která C# cílí na nebo Visual Basic kódu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="dbcd2-105">Váš **analyzátor** obsahuje kód, který rozpoznává porušení vašeho pravidla.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="dbcd2-106">**Oprava kódu** obsahuje kód, který vyřeší porušení.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="dbcd2-107">Pravidla, která implementujete, může být cokoli od struktury kódu až po kódování stylu a vytváření názvů.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="dbcd2-108">.NET Compiler Platform poskytuje rozhraní pro spouštění analýzy, protože vývojáři píší kód a všechny funkce uživatelského rozhraní sady Visual Studio pro úpravu kódu: zobrazení vlnovek v editoru, vyplnění sady Visual Studio Seznam chyb a vytvoření "žárovky". návrhy a zobrazují bohatou verzi Preview navrhovaných oprav.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="dbcd2-109">V tomto kurzu se seznámíte s vytvořením **analyzátoru** a s doprovodnou **opravou kódu** pomocí rozhraní API Roslyn.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="dbcd2-110">Analyzátor je způsob, jak provádět analýzu zdrojového kódu a nahlásit problém uživateli.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="dbcd2-111">V případě potřeby může analyzátor také poskytnout opravu kódu, která představuje úpravu zdrojového kódu uživatele.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="dbcd2-112">V tomto kurzu se vytvoří analyzátor, který najde deklarace místních proměnných, které by mohly být deklarované pomocí modifikátoru `const`, ale ne.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="dbcd2-113">Oprava doprovodného kódu upraví tyto deklarace a přidá modifikátor `const`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dbcd2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbcd2-114">Prerequisites</span></span>

- [<span data-ttu-id="dbcd2-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="dbcd2-115">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [<span data-ttu-id="dbcd2-116">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="dbcd2-116">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="dbcd2-117">**.NET COMPILER Platform SDK** bude nutné nainstalovat pomocí instalační program pro Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-117">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="dbcd2-118">Existuje několik kroků k vytvoření a ověření analyzátoru:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-118">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="dbcd2-119">Vytvořte řešení.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-119">Create the solution.</span></span>
1. <span data-ttu-id="dbcd2-120">Zaregistrujte název a popis analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-120">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="dbcd2-121">Upozornění a doporučení analyzátoru sestav.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-121">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="dbcd2-122">Implementací opravy kódu přijměte doporučení.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-122">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="dbcd2-123">Zlepšete analýzu prostřednictvím jednotkových testů.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-123">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="dbcd2-124">Prozkoumat šablonu analyzátoru</span><span class="sxs-lookup"><span data-stu-id="dbcd2-124">Explore the analyzer template</span></span>

<span data-ttu-id="dbcd2-125">Analyzátor hlásí uživateli všechny deklarace místních proměnných, které lze převést na místní konstanty.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-125">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="dbcd2-126">Zvažte například následující kód:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-126">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="dbcd2-127">Do výše uvedeného kódu `x` je přiřazena konstantní hodnota a nikdy se nemění.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-127">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="dbcd2-128">Dá se deklarovat pomocí modifikátoru `const`:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-128">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="dbcd2-129">Analýza, která určuje, zda může být proměnná vytvořena, je vyžadována syntaktickou analýzou, konstantní analýzou výrazu inicializátoru a analýzou toku dat, aby se zajistilo, že proměnná nebude nikdy zapsána do.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-129">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="dbcd2-130">.NET Compiler Platform poskytuje rozhraní API, která usnadňují provádění této analýzy.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-130">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="dbcd2-131">Prvním krokem je vytvoření nového C# **analyzátoru s projektem opravit kód** .</span><span class="sxs-lookup"><span data-stu-id="dbcd2-131">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

- <span data-ttu-id="dbcd2-132">V aplikaci Visual Studio vyberte **soubor > nový > projekt...** zobrazí se dialogové okno Nový projekt.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-132">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="dbcd2-133">V **části C# rozšiřitelnost vizuálního >** vyberte **analyzátor s opravou kódu (.NET Standard)** .</span><span class="sxs-lookup"><span data-stu-id="dbcd2-133">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="dbcd2-134">Pojmenujte projekt "**MakeConst**" a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-134">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="dbcd2-135">Analyzátor se šablonou opravy kódu vytvoří tři projekty: jeden obsahuje analyzátor a opravu kódu, druhým je projekt testu jednotek a třetí je projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-135">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="dbcd2-136">Výchozí spouštěný projekt je projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-136">The default startup project is the VSIX project.</span></span> <span data-ttu-id="dbcd2-137">Stisknutím klávesy **F5** spusťte projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-137">Press **F5** to start the VSIX project.</span></span> <span data-ttu-id="dbcd2-138">Tím se spustí druhá instance sady Visual Studio, která zavedla nový analyzátor.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-138">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="dbcd2-139">Při spuštění analyzátoru spustíte druhou kopii sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-139">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="dbcd2-140">Tato druhá kopie používá k uložení nastavení jiný podregistr registru.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-140">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="dbcd2-141">To umožňuje odlišit nastavení vizuálu v obou kopiích sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-141">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="dbcd2-142">Můžete vybrat jiný motiv pro experimentální běh sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-142">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="dbcd2-143">Kromě toho nevytvářejte roaming nastavení ani přihlášení k účtu aplikace Visual Studio pomocí experimentálního spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-143">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="dbcd2-144">Který udržuje nastavení odlišně.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-144">That keeps the settings different.</span></span>

<span data-ttu-id="dbcd2-145">Ve druhé instanci sady Visual Studio, kterou jste právě spustili, vytvořte nový C# projekt konzolové aplikace (.NET Core nebo .NET Framework projekt budou fungovat na úrovni zdroje.) Najeďte myší na token podtrženým vlnovkou a zobrazí se text upozornění, který je k dispozici v analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-145">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="dbcd2-146">Šablona vytvoří analyzátor, který ohlásí upozornění na každou deklaraci typu, kde název typu obsahuje malá písmena, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-146">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Upozornění pro generování sestav analyzátoru](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="dbcd2-148">Šablona také poskytuje opravu kódu, která změní jakýkoli název typu obsahující malá písmena na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-148">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="dbcd2-149">Můžete kliknout na žárovku, která se zobrazuje s upozorněním, a zobrazit navrhované změny.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-149">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="dbcd2-150">Přijetí navrhovaných změn aktualizuje název typu a všechny odkazy na daný typ v řešení.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-150">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="dbcd2-151">Teď, když jste viděli počáteční analyzátor v akci, zavřete druhou instanci sady Visual Studio a vraťte se do projektu analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-151">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="dbcd2-152">Nemusíte spouštět druhou kopii sady Visual Studio a vytvořit nový kód pro otestování všech změn v analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-152">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="dbcd2-153">Šablona také vytvoří projekt testu jednotek za vás.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-153">The template also creates a unit test project for you.</span></span> <span data-ttu-id="dbcd2-154">Tento projekt obsahuje dva testy.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-154">That project contains two tests.</span></span> <span data-ttu-id="dbcd2-155">`TestMethod1` zobrazuje typický formát testu, který analyzuje kód bez aktivace diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-155">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="dbcd2-156">`TestMethod2` zobrazuje formát testu, který aktivuje diagnostiku a poté použije navrhovanou opravu kódu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-156">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="dbcd2-157">Při sestavování analyzátoru a opravy kódu budete psát testy pro různé struktury kódu, abyste ověřili svoji práci.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-157">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="dbcd2-158">Testy jednotek pro analyzátory jsou mnohem rychlejší než interaktivní testování pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-158">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="dbcd2-159">Testy jednotek analyzátoru jsou skvělým nástrojem, když víte, které konstrukce kódu by měly a nemají aktivovat analyzátor.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-159">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="dbcd2-160">Načítání analyzátoru v jiné kopii sady Visual Studio je skvělý nástroj pro zkoumání a hledání konstrukcí, na které jste se ještě nemuseli myslet.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-160">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="dbcd2-161">Vytvoření registrací analyzátoru</span><span class="sxs-lookup"><span data-stu-id="dbcd2-161">Create analyzer registrations</span></span>

<span data-ttu-id="dbcd2-162">Šablona vytvoří počáteční třídu `DiagnosticAnalyzer` v souboru **MakeConstAnalyzer.cs** .</span><span class="sxs-lookup"><span data-stu-id="dbcd2-162">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="dbcd2-163">Tento počáteční analyzátor zobrazuje dvě důležité vlastnosti každého analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-163">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="dbcd2-164">Každý diagnostický analyzátor musí poskytovat atribut `[DiagnosticAnalyzer]`, který popisuje jazyk, na kterém pracuje.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-164">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="dbcd2-165">Každý diagnostický analyzátor musí být odvozen od <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> třídy.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-165">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="dbcd2-166">Šablona také zobrazuje základní funkce, které jsou součástí jakéhokoli analyzátoru:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-166">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="dbcd2-167">Proveďte registraci akcí.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-167">Register actions.</span></span> <span data-ttu-id="dbcd2-168">Akce reprezentují změny kódu, které by měly aktivovat analyzátor, aby prozkoumali kód pro porušení.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-168">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="dbcd2-169">Když Visual Studio detekuje úpravy kódu, které odpovídají zaregistrované akci, volá metodu zaregistrovanou analyzátorem.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-169">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="dbcd2-170">Vytvořte diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-170">Create diagnostics.</span></span> <span data-ttu-id="dbcd2-171">Když analyzátor zjistí porušení, vytvoří objekt diagnostiky, který Visual Studio používá k upozorňování uživatele na porušení.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-171">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="dbcd2-172">Akce zaregistrujete do přepsání <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-172">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dbcd2-173">V tomto kurzu navštívíte **uzly syntaxe** , které hledají místní deklarace, a zjistíte, které z nich mají konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-173">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="dbcd2-174">Pokud by deklarace mohla být konstantní, analyzátor vytvoří a nahlásí diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-174">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="dbcd2-175">Prvním krokem je aktualizovat konstanty registru a metodu `Initialize` tak, aby tyto konstanty označovaly analyzátor "Make const".</span><span class="sxs-lookup"><span data-stu-id="dbcd2-175">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="dbcd2-176">Většina řetězcových konstant je definována v souboru prostředků řetězce.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-176">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="dbcd2-177">Pro snazší lokalizaci byste měli postupovat podle tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-177">You should follow that practice for easier localization.</span></span> <span data-ttu-id="dbcd2-178">Otevřete soubor **Resources. resx** pro projekt analyzátoru **MakeConst** .</span><span class="sxs-lookup"><span data-stu-id="dbcd2-178">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="dbcd2-179">Tím se zobrazí editor prostředků.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-179">This displays the resource editor.</span></span> <span data-ttu-id="dbcd2-180">Aktualizujte prostředky řetězce následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-180">Update the string resources as follows:</span></span>

- <span data-ttu-id="dbcd2-181">Změňte `AnalyzerTitle` na "proměnná může být vytvořena konstanta".</span><span class="sxs-lookup"><span data-stu-id="dbcd2-181">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
- <span data-ttu-id="dbcd2-182">Změňte `AnalyzerMessageFormat` na "lze vytvořit konstantu".</span><span class="sxs-lookup"><span data-stu-id="dbcd2-182">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
- <span data-ttu-id="dbcd2-183">Změňte `AnalyzerDescription` na "vytvořit konstantu".</span><span class="sxs-lookup"><span data-stu-id="dbcd2-183">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="dbcd2-184">Změňte také rozevírací seznam **modifikátor přístupu** na `public`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-184">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="dbcd2-185">To usnadňuje používání těchto konstant v testování částí.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-185">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="dbcd2-186">Po dokončení by se měl editor prostředků zobrazit tak, jak ukazuje následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-186">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Aktualizace prostředků řetězců](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="dbcd2-188">Zbývající změny jsou v souboru analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-188">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="dbcd2-189">Otevřete **MakeConstAnalyzer.cs** v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-189">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="dbcd2-190">Změňte zaregistrovanou akci z jedné, která funguje na symbolech, které fungují na syntaxi.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-190">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="dbcd2-191">V metodě `MakeConstAnalyzerAnalyzer.Initialize` Najděte řádek, který zaregistruje akci na symboly:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-191">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="dbcd2-192">Nahraďte ji následujícím řádkem:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-192">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="dbcd2-193">Po této změně můžete metodu `AnalyzeSymbol` odstranit.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-193">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="dbcd2-194">Tento analyzátor prověřuje <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, nikoli příkazy <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-194">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="dbcd2-195">Všimněte si, že `AnalyzeNode` obsahuje červené vlnovky.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-195">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="dbcd2-196">Kód, který jste právě přidali, odkazuje na metodu `AnalyzeNode`, která nebyla deklarována.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-196">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="dbcd2-197">Deklarujte tuto metodu pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-197">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="dbcd2-198">Změňte `Category` na "využití" v **MakeConstAnalyzer.cs** , jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-198">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="dbcd2-199">Najde místní deklarace, které by mohly být const.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-199">Find local declarations that could be const</span></span>

<span data-ttu-id="dbcd2-200">Je čas napsat první verzi metody `AnalyzeNode`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-200">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="dbcd2-201">Měl by hledat jednu místní deklaraci, která by mohla být `const`, ale ne, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-201">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="dbcd2-202">Prvním krokem je najít místní deklarace.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-202">The first step is to find local declarations.</span></span> <span data-ttu-id="dbcd2-203">Do **MakeConstAnalyzer.cs**přidejte následující kód pro `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-203">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="dbcd2-204">Toto přetypování vždy proběhne úspěšně, protože analyzátor zaregistroval pro změny místních deklarací a pouze místní deklarace.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-204">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="dbcd2-205">Žádný jiný typ uzlu neaktivuje volání metody `AnalyzeNode`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-205">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="dbcd2-206">Dále ověřte deklaraci pro všechny modifikátory `const`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-206">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="dbcd2-207">Pokud je najdete, vraťte se hned.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-207">If you find them, return immediately.</span></span> <span data-ttu-id="dbcd2-208">Následující kód vyhledá všechny modifikátory `const` v místní deklaraci:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-208">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="dbcd2-209">Nakonec je třeba ověřit, zda by mohla být proměnná `const`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-209">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="dbcd2-210">To znamená, že se po inicializaci nikdy nepřiřazuje.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-210">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="dbcd2-211">Pomocí <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>provedete určitou sémantickou analýzu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-211">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="dbcd2-212">Pomocí argumentu `context` určíte, zda lze vytvořit deklaraci lokální proměnné `const`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-212">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="dbcd2-213"><xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> představuje všechny sémantické informace v jednom zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-213">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents of all semantic information in a single source file.</span></span> <span data-ttu-id="dbcd2-214">Další informace najdete v článku, který pokrývá [sémantické modely](../work-with-semantics.md).</span><span class="sxs-lookup"><span data-stu-id="dbcd2-214">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="dbcd2-215">Použijete <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> k provedení analýzy toku dat v příkazu místní deklarace.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-215">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="dbcd2-216">Pak použijete výsledky této analýzy toku dat, abyste zajistili, že místní proměnná nebude zapsána novou hodnotou kdekoli jinde.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-216">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="dbcd2-217">Voláním metody rozšíření <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> načtete <xref:Microsoft.CodeAnalysis.ILocalSymbol> proměnné a zkontrolujete, že není obsažena v kolekci <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> analýzy toku dat.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-217">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="dbcd2-218">Na konec `AnalyzeNode` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-218">Add the following code to the end of the `AnalyzeNode` method:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="dbcd2-219">Kód, který jste právě přidali, zajistí, že proměnná nebude změněna a lze ji proto nastavit `const`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-219">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="dbcd2-220">Je čas vyvolat diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-220">It's time to raise the diagnostic.</span></span> <span data-ttu-id="dbcd2-221">Jako poslední řádek v `AnalyzeNode`přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-221">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="dbcd2-222">Svůj průběh můžete zjistit stisknutím klávesy **F5** ke spuštění analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-222">You can check your progress by pressing **F5** to run your analyzer.</span></span> <span data-ttu-id="dbcd2-223">Můžete načíst konzolovou aplikaci, kterou jste vytvořili dříve, a pak přidat následující zkušební kód:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-223">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="dbcd2-224">Měla by se zobrazit žárovka a analyzátor by měl ohlásit diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-224">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="dbcd2-225">Žárovka však stále používá opravu kódu vygenerovanou šablonou a oznamuje vám, že může být proveden na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-225">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="dbcd2-226">V další části se dozvíte, jak napsat opravu kódu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-226">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="dbcd2-227">Zapsat opravu kódu</span><span class="sxs-lookup"><span data-stu-id="dbcd2-227">Write the code fix</span></span>

<span data-ttu-id="dbcd2-228">Analyzátor může poskytovat jednu nebo více oprav kódu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-228">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="dbcd2-229">Oprava kódu definuje úpravu, která řeší nahlášený problém.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-229">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="dbcd2-230">Pro analyzátor, který jste vytvořili, můžete zadat opravu kódu, která vloží klíčové slovo const:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-230">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="dbcd2-231">Uživatel zvolí tuto možnost z uživatelského rozhraní žárovky v editoru a Visual Studio změní kód.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-231">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="dbcd2-232">Otevřete soubor **MakeConstCodeFixProvider.cs** , který šablona přidala.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-232">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="dbcd2-233">Tato oprava kódu je již zapojena do ID diagnostiky vytvořeného analyzátorem diagnostiky, ale ještě neimplementuje správnou transformaci kódu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-233">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="dbcd2-234">Nejprve byste měli odebrat některý kód šablony.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-234">First you should remove some of the template code.</span></span> <span data-ttu-id="dbcd2-235">Změňte řetězec nadpisu na "vytvořit konstantu":</span><span class="sxs-lookup"><span data-stu-id="dbcd2-235">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="dbcd2-236">Dále odstraňte metodu `MakeUppercaseAsync`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-236">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="dbcd2-237">Už se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-237">It no longer applies.</span></span>

<span data-ttu-id="dbcd2-238">Všichni poskytovatelé oprav kódu jsou odvozeni z <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-238">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="dbcd2-239">Všechna <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> přepisují, aby nahlásily dostupné opravy kódu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-239">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="dbcd2-240">V `RegisterCodeFixesAsync`změňte typ nadřazeného uzlu, který hledáte pro <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>, aby odpovídal diagnostice:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-240">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="dbcd2-241">Dále změňte poslední řádek pro registraci opravy kódu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-241">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="dbcd2-242">Vaše oprava vytvoří nový dokument, který bude mít za následek přidání modifikátoru `const` do existující deklarace:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-242">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="dbcd2-243">Všimněte si červené vlnovky v kódu, který jste právě přidali na symbol `MakeConstAsync`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-243">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="dbcd2-244">Přidejte deklaraci pro `MakeConstAsync` jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-244">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="dbcd2-245">Vaše nová metoda `MakeConstAsync` transformuje <xref:Microsoft.CodeAnalysis.Document> reprezentující zdrojový soubor uživatele do nového <xref:Microsoft.CodeAnalysis.Document>, který nyní obsahuje deklaraci `const`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-245">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="dbcd2-246">Vytvoříte nový token klíčového slova `const` pro vložení na začátek prohlášení.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-246">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="dbcd2-247">Buďte opatrní, abyste nejdřív odebrali všechny úvodní minihry z prvního tokenu příkazu deklarace a připojili ho k tokenu `const`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-247">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="dbcd2-248">Do metody `MakeConstAsync` přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-248">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="dbcd2-249">Dále přidejte token `const` k deklaraci pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-249">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="dbcd2-250">Dále naformátujte novou deklaraci tak C# , aby odpovídala pravidlům formátování.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-250">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="dbcd2-251">Formátování změn tak, aby odpovídalo existujícímu kódu, vytvoří lepší prostředí.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-251">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="dbcd2-252">Přidejte následující příkaz hned za existující kód:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-252">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="dbcd2-253">Pro tento kód je vyžadován nový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-253">A new namespace is required for this code.</span></span> <span data-ttu-id="dbcd2-254">Do horní části souboru přidejte následující příkaz `using`:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-254">Add the following `using` statement to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="dbcd2-255">Posledním krokem je provedení úprav.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-255">The final step is to make your edit.</span></span> <span data-ttu-id="dbcd2-256">Tento postup má tři kroky:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-256">There are three steps to this process:</span></span>

1. <span data-ttu-id="dbcd2-257">Získejte popisovač pro existující dokument.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-257">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="dbcd2-258">Vytvořte nový dokument nahrazením existující deklarace novou deklarací.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-258">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="dbcd2-259">Vrátí nový dokument.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-259">Return the new document.</span></span>

<span data-ttu-id="dbcd2-260">Na konec `MakeConstAsync` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-260">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="dbcd2-261">Oprava kódu je připravená k vyzkoušení.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-261">Your code fix is ready to try.</span></span>  <span data-ttu-id="dbcd2-262">Stisknutím klávesy F5 spusťte projekt analyzátoru v druhé instanci aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-262">Press F5 to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="dbcd2-263">Ve druhé instanci sady Visual Studio vytvořte nový C# projekt konzolové aplikace a přidejte několik deklarací místních proměnných inicializovaných s konstantními hodnotami do metody Main.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-263">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="dbcd2-264">Uvidíte, že jsou hlášeny jako upozornění, jak je uvedeno níže.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-264">You'll see that they are reported as warnings as below.</span></span>

![Může vytvořit konstantní upozornění.](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="dbcd2-266">Provedli jste spoustu pokroku.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-266">You've made a lot of progress.</span></span> <span data-ttu-id="dbcd2-267">V deklaracích, které mohou být provedeny `const`, jsou vlnovky.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-267">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="dbcd2-268">I když ale pořád funguje.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-268">But there is still work to do.</span></span> <span data-ttu-id="dbcd2-269">Tato funkce funguje, pokud přidáte `const` k deklaracím počínaje `i`a pak `j` a nakonec `k`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-269">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="dbcd2-270">Pokud však přidáte modifikátor `const` v jiném pořadí, počínaje `k`, analyzátor vytvoří chyby: `k` nelze deklarovat `const`, pokud `i` a `j` oba již `const`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-270">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="dbcd2-271">Máte možnost provést další analýzu, abyste se ujistili, že je možné zpracovat různé způsoby, které lze deklarovat a inicializovat.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-271">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="dbcd2-272">Vytváření testů řízených daty</span><span class="sxs-lookup"><span data-stu-id="dbcd2-272">Build data driven tests</span></span>

<span data-ttu-id="dbcd2-273">Analyzátor a oprava kódu fungují na jednoduchém případu jedné deklarace, která může být vytvořena jako const.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-273">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="dbcd2-274">Existuje mnoho možných příkazů deklarace, kde tato implementace způsobuje chyby.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-274">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="dbcd2-275">Tyto případy se řeší při práci s knihovnou testu jednotek zapsanou šablonou.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-275">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="dbcd2-276">Je mnohem rychlejší než opakované otevření druhé kopie sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-276">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="dbcd2-277">Otevřete soubor **MakeConstUnitTests.cs** v projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-277">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="dbcd2-278">Šablona vytvořila dva testy, které následují dva běžné vzory pro analyzátor a opravu testování částí kódu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-278">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="dbcd2-279">`TestMethod1` zobrazuje vzor testu, který zajišťuje, že analyzátor neohlásí diagnostiku, pokud by neměl.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-279">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="dbcd2-280">`TestMethod2` zobrazuje vzor pro vytváření sestav diagnostiky a spuštění opravy kódu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-280">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="dbcd2-281">Kód pro téměř každý test pro analyzátor následuje po jednom z těchto dvou vzorů.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-281">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="dbcd2-282">V prvním kroku můžete tyto testy přepracovat jako testy řízené daty.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-282">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="dbcd2-283">Pak bude snadné vytvořit nové testy přidáním nových řetězcových konstant pro reprezentaci různých testovacích vstupů.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-283">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="dbcd2-284">V rámci efektivity je prvním krokem refaktorování dvou testů do testů řízených daty.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-284">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="dbcd2-285">Pak stačí definovat několik řetězcových konstant pro každý nový test.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-285">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="dbcd2-286">I když refaktoring, přejmenujte obě metody pro lepší názvy.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-286">While your refactoring, rename both methods to better names.</span></span> <span data-ttu-id="dbcd2-287">Nahraďte `TestMethod1` tímto testem, který zajišťuje, že se neaktivuje žádná diagnostika:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-287">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="dbcd2-288">Můžete vytvořit nový řádek dat pro tento test definováním jakékoli fragmenty kódu, který by neměl způsobit, že diagnostika spustí upozornění.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-288">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="dbcd2-289">Toto přetížení `VerifyCSharpDiagnostic` projde, když nejsou pro fragment zdrojového kódu aktivované žádné diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-289">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="dbcd2-290">Dále nahraďte `TestMethod2` tímto testem, který zajistí vyvolání diagnostiky, a opravu kódu použitou pro fragment zdrojového kódu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-290">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

<span data-ttu-id="dbcd2-291">Předchozí kód také provedl několik změn kódu, který vytváří očekávaný výsledek diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-291">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="dbcd2-292">Používá veřejné konstanty zaregistrované v analyzátoru `MakeConst`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-292">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="dbcd2-293">Kromě toho používá dvě řetězcové konstanty pro vstupní a pevný zdroj.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-293">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="dbcd2-294">Do třídy `UnitTest` přidejte následující řetězcové konstanty:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-294">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="dbcd2-295">Spusťte tyto dva testy, abyste se ujistili, že jsou průchody.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-295">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="dbcd2-296">V aplikaci Visual Studio otevřete **Průzkumníka testů** výběrem možnosti **Test** > **Windows** > **Test Explorer**.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-296">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span>  <span data-ttu-id="dbcd2-297">Stiskněte odkaz **Spustit vše** .</span><span class="sxs-lookup"><span data-stu-id="dbcd2-297">The press the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="dbcd2-298">Vytvořit testy pro platné deklarace</span><span class="sxs-lookup"><span data-stu-id="dbcd2-298">Create tests for valid declarations</span></span>

<span data-ttu-id="dbcd2-299">Obecně platí, že analyzátory by měly skončit co nejrychleji, což má minimální práci.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-299">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="dbcd2-300">Visual Studio volá zaregistrované analyzátory jako kód úprav uživatele.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-300">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="dbcd2-301">Odezva je klíčovým požadavkem.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-301">Responsiveness is a key requirement.</span></span> <span data-ttu-id="dbcd2-302">Existuje několik testovacích případů pro kód, který by neměl vyvolat diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-302">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="dbcd2-303">Analyzátor již zpracovává jeden z těchto testů, případ, kdy je přiřazena proměnná po inicializaci.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-303">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="dbcd2-304">Přidejte následující řetězcovou konstantu do testů pro reprezentaci tohoto případu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-304">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="dbcd2-305">Pak přidejte řádek dat pro tento test, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-305">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="dbcd2-306">Tento test se také projde.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-306">This test passes as well.</span></span> <span data-ttu-id="dbcd2-307">Dále přidejte konstanty pro podmínky, které jste ještě nezpracovali:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-307">Next, add constants for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="dbcd2-308">Deklarace, které jsou již `const`, protože jsou již const:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-308">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="dbcd2-309">Deklarace, které nemají žádný inicializátor, protože neexistuje žádná hodnota, která se má použít:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-309">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="dbcd2-310">Deklarace, kde inicializátor není konstanta, protože nemohou být konstanty v čase kompilace:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-310">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="dbcd2-311">Může být ještě složitější, protože C# umožňuje více deklarací v rámci jednoho příkazu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-311">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="dbcd2-312">Vezměte v úvahu následující řetězcové konstanty testovacího případu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-312">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="dbcd2-313">Proměnná `i` může být vytvořena jako konstanta, ale proměnná `j` nemůže.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-313">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="dbcd2-314">Proto tento příkaz nelze vytvořit jako deklaraci konstanty.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-314">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="dbcd2-315">Přidejte deklarace `DataRow` pro všechny tyto testy:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-315">Add the `DataRow` declarations for all these tests:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="dbcd2-316">Spusťte testy znovu a uvidíte, že tyto nové testovací případy selžou.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-316">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="dbcd2-317">Aktualizace analyzátoru tak, aby ignoroval správné deklarace</span><span class="sxs-lookup"><span data-stu-id="dbcd2-317">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="dbcd2-318">K vyfiltrování kódu, který odpovídá těmto podmínkám, potřebujete některá vylepšení `AnalyzeNode` metody analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-318">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="dbcd2-319">Jsou to všechny související podmínky, takže podobné změny vyřeší všechny tyto podmínky.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-319">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="dbcd2-320">Proveďte následující změny `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-320">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="dbcd2-321">Vaše Sémantická analýza prozkoumala deklaraci jedné proměnné.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-321">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="dbcd2-322">Tento kód musí být ve smyčce `foreach`, která prověřuje všechny proměnné deklarované v rámci stejného příkazu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-322">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="dbcd2-323">Každá deklarovaná proměnná musí mít inicializátor.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-323">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="dbcd2-324">Každý inicializátor deklarované proměnné musí být konstanta v čase kompilace.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-324">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="dbcd2-325">V metodě `AnalyzeNode` nahraďte původní sémantickou analýzu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-325">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="dbcd2-326">s následujícím fragmentem kódu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-326">with the following code snippet:</span></span>

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

<span data-ttu-id="dbcd2-327">První `foreach` smyčka prověřuje každou deklaraci proměnné pomocí syntaktické analýzy.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-327">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="dbcd2-328">První ověření zaručuje, že proměnná má inicializátor.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-328">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="dbcd2-329">Druhá kontrolu garantuje, že inicializátor je konstanta.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-329">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="dbcd2-330">Druhá smyčka má původní sémantickou analýzu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-330">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="dbcd2-331">Sémantické kontroly jsou samostatné smyčky, protože mají větší vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-331">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="dbcd2-332">Spusťte testy znovu a měli byste je vidět, že jsou všechny passované.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-332">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="dbcd2-333">Přidat konečný polský</span><span class="sxs-lookup"><span data-stu-id="dbcd2-333">Add the final polish</span></span>

<span data-ttu-id="dbcd2-334">Už jste téměř hotovi.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-334">You're almost done.</span></span> <span data-ttu-id="dbcd2-335">Analyzátor může zpracovat několik dalších podmínek.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-335">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="dbcd2-336">Visual Studio volá analyzátory, zatímco uživatel píše kód.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-336">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="dbcd2-337">Často se jedná o případ, kdy se analyzátor bude volat pro kód, který se nekompiluje.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-337">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="dbcd2-338">Metoda `AnalyzeNode` analyzátoru diagnostiky nezjistí, zda je konstantní hodnota převoditelná na typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-338">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="dbcd2-339">Aktuální implementace tak bude Happily převést nesprávnou deklaraci, jako je int i = "ABC", na místní konstantu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-339">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="dbcd2-340">Přidat řetězcovou konstantu zdrojového řetězce pro tuto podmínku:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-340">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="dbcd2-341">Odkazové typy se navíc nezpracovávají správně.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-341">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="dbcd2-342">Jediná hodnota konstanty povolená pro typ odkazu je `null`, s výjimkou případu, kdy <xref:System.String?displayProperty=nameWithType>, která umožňuje řetězcové literály.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-342">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="dbcd2-343">Jinými slovy, `const string s = "abc"` je právní, ale `const object s = "abc"` ne.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-343">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="dbcd2-344">Tento fragment kódu ověřuje tuto podmínku:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-344">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="dbcd2-345">Chcete-li být důkladnější, je nutné přidat další test, abyste se ujistili, že můžete vytvořit konstantní deklarace pro řetězec.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-345">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="dbcd2-346">Následující fragment kódu definuje kód, který vyvolává diagnostiku, a kód po použití opravy:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-346">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="dbcd2-347">Nakonec, pokud je proměnná deklarována s klíčovým slovem `var`, oprava kódu nesprávné věci a vygeneruje deklaraci `const var`, která není C# jazykem podporována.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-347">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="dbcd2-348">Chcete-li opravit tuto chybu, oprava kódu musí nahradit klíčové slovo `var` názvem odvozeného typu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-348">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="dbcd2-349">Tyto změny aktualizují deklarace datových řádků pro oba testy.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-349">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="dbcd2-350">Následující kód ukazuje tyto testy se všemi atributy datových řádků:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-350">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="dbcd2-351">Naštěstí můžete všechny výše uvedené chyby vyřešit pomocí stejných technik, které jste právě naučili.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-351">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="dbcd2-352">Chcete-li opravit první chybu, nejprve otevřete **DiagnosticAnalyzer.cs** a vyhledejte smyčku foreach, kde jsou zkontrolovány jednotlivé Inicializátory místní deklarace, aby bylo zajištěno, že jsou přiřazeny pomocí konstantních hodnot.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-352">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="dbcd2-353">Bezprostředně _před_ první smyčkou foreach volejte `context.SemanticModel.GetTypeInfo()`, aby se načetly podrobné informace o deklarovaném typu místní deklarace:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-353">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="dbcd2-354">Potom v rámci smyčky `foreach` zkontrolujte každý inicializátor a ujistěte se, že je převoditelné na typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-354">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="dbcd2-355">Po ověření, že inicializátor je konstanta, přidejte následující kontrolu:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-355">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="dbcd2-356">Další změny se vytvoří po poslední.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-356">The next change builds upon the last one.</span></span> <span data-ttu-id="dbcd2-357">Před pravou složenou závorkou první smyčky foreach přidejte následující kód pro zkontrolování typu místní deklarace, je-li konstanta řetězec nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-357">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

<span data-ttu-id="dbcd2-358">Chcete-li nahradit klíčové slovo var správným názvem typu, je nutné ve svém poskytovateli opravy kódu napsat trochu větší kód.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-358">You must write a bit more code in your code fix provider to replace the var' keyword with the correct type name.</span></span> <span data-ttu-id="dbcd2-359">Vraťte se na **CodeFixProvider.cs**.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-359">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="dbcd2-360">Kód, který přidáte, provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-360">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="dbcd2-361">Ověřte, zda je deklarace deklarace `var` a zda je:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-361">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="dbcd2-362">Vytvoří nový typ pro odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-362">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="dbcd2-363">Ujistěte se, že deklarace typu není alias.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-363">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="dbcd2-364">Pokud ano, je právní `const var`deklarovat.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-364">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="dbcd2-365">Ujistěte se, že v tomto programu `var` není název typu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-365">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="dbcd2-366">(Pokud ano, `const var` je právní).</span><span class="sxs-lookup"><span data-stu-id="dbcd2-366">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="dbcd2-367">Zjednodušit úplný název typu</span><span class="sxs-lookup"><span data-stu-id="dbcd2-367">Simplify the full type name</span></span>

<span data-ttu-id="dbcd2-368">Tyto zvuky jako velké množství kódu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-368">That sounds like a lot of code.</span></span> <span data-ttu-id="dbcd2-369">Není to.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-369">It's not.</span></span> <span data-ttu-id="dbcd2-370">Nahraďte řádek, který deklaruje a inicializuje `newLocal`, pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-370">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="dbcd2-371">Hned po inicializaci `newModifiers`:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-371">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="dbcd2-372">K použití typu <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> budete muset přidat jeden `using` příkaz:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-372">You'll need to add one `using` statement to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="dbcd2-373">Spusťte testy a všechny by měly být passované.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-373">Run your tests, and they should all pass.</span></span> <span data-ttu-id="dbcd2-374">Congratulate se tak, že spustíte kompletní analyzátor.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-374">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="dbcd2-375">Stisknutím kombinace kláves CTRL + F5 spusťte projekt analyzátoru v druhé instanci sady Visual Studio s načteným rozšířením Roslyn Preview.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-375">Press Ctrl+F5 to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="dbcd2-376">Ve druhé instanci sady Visual Studio vytvořte nový C# projekt konzolové aplikace a přidejte `int x = "abc";` do metody Main.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-376">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="dbcd2-377">Děkujeme, že při první opravě chyby by se pro tuto místní proměnnou proměnné nemělo hlásit žádné upozornění (i když dojde k chybě kompilátoru, jak se očekávalo).</span><span class="sxs-lookup"><span data-stu-id="dbcd2-377">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="dbcd2-378">Dále přidejte `object s = "abc";` do metody Main.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-378">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="dbcd2-379">Z důvodu druhé opravy chyby by se nemělo hlásit žádné upozornění.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-379">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="dbcd2-380">Nakonec přidejte další místní proměnnou, která používá klíčové slovo `var`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-380">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="dbcd2-381">Uvidíte, že se nahlásí upozornění a na levé straně se zobrazí návrh.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-381">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="dbcd2-382">Přesuňte kurzor editoru na podtržení vlnovkou a stiskněte kombinaci kláves CTRL +.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-382">Move the editor caret over the squiggly underline and press Ctrl+.</span></span> <span data-ttu-id="dbcd2-383">pro zobrazení navrhované opravy kódu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-383">to display the suggested code fix.</span></span> <span data-ttu-id="dbcd2-384">Po výběru opravy kódu si všimněte, že klíčové slovo var se nyní zpracovává správně.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-384">Upon selecting your code fix, note that the var' keyword is now handled correctly.</span></span>

<span data-ttu-id="dbcd2-385">Nakonec přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="dbcd2-385">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="dbcd2-386">Po těchto změnách získáte červené vlnovky pouze první dvě proměnné.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-386">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="dbcd2-387">Přidejte `const` do `i` i `j`a dostanete nové upozornění na `k`, protože teď může být `const`.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-387">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="dbcd2-388">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="dbcd2-388">Congratulations!</span></span> <span data-ttu-id="dbcd2-389">Vytvořili jste první rozšíření .NET Compiler Platform, které provádí průběžnou analýzu kódu k detekci problému a nabízí rychlou opravu pro její opravu.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-389">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="dbcd2-390">Na cestě jste se naučili mnoho rozhraní API kódu, která jsou součástí sady .NET Compiler Platform SDK (rozhraní API Roslyn).</span><span class="sxs-lookup"><span data-stu-id="dbcd2-390">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="dbcd2-391">Práci s [dokončenou ukázkou](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) najdete v našem úložišti GitHub Samples.</span><span class="sxs-lookup"><span data-stu-id="dbcd2-391">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="dbcd2-392">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="dbcd2-392">Other resources</span></span>

- [<span data-ttu-id="dbcd2-393">Začínáme s analýzou syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbcd2-393">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="dbcd2-394">Začínáme se sémantickou analýzou</span><span class="sxs-lookup"><span data-stu-id="dbcd2-394">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)

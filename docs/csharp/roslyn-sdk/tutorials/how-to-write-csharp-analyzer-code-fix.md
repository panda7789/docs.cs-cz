---
title: 'Kurz: vytvoření prvního analyzátoru a opravy kódu'
description: V tomto kurzu najdete podrobné pokyny k sestavení analyzátoru a opravy kódu pomocí sady .NET Compiler SDK (rozhraní Roslyn API).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: c70fcacc6cb30969e5c69ffd0954ac52e637a915
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100935"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="89514-103">Kurz: vytvoření prvního analyzátoru a opravy kódu</span><span class="sxs-lookup"><span data-stu-id="89514-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="89514-104">Sada .NET Compiler Platform SDK poskytuje nástroje, které potřebujete k vytváření vlastních upozornění, která cílí na kód C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="89514-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="89514-105">Váš **analyzátor** obsahuje kód, který rozpoznává porušení vašeho pravidla.</span><span class="sxs-lookup"><span data-stu-id="89514-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="89514-106">**Oprava kódu** obsahuje kód, který vyřeší porušení.</span><span class="sxs-lookup"><span data-stu-id="89514-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="89514-107">Pravidla, která implementujete, může být cokoli od struktury kódu až po kódování stylu a vytváření názvů.</span><span class="sxs-lookup"><span data-stu-id="89514-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="89514-108">.NET Compiler Platform poskytuje rozhraní pro spouštění analýzy, protože vývojáři píší kód a všechny funkce uživatelského rozhraní sady Visual Studio pro úpravu kódu: zobrazení vlnovek v editoru, naplnění Seznam chyb sady Visual Studio, vytváření návrhů "světlé žárovky" a zobrazení obsáhlé verze Preview navrhovaných oprav.</span><span class="sxs-lookup"><span data-stu-id="89514-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="89514-109">V tomto kurzu se seznámíte s vytvořením **analyzátoru** a s doprovodnou **opravou kódu** pomocí rozhraní API Roslyn.</span><span class="sxs-lookup"><span data-stu-id="89514-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="89514-110">Analyzátor je způsob, jak provádět analýzu zdrojového kódu a nahlásit problém uživateli.</span><span class="sxs-lookup"><span data-stu-id="89514-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="89514-111">V případě potřeby může analyzátor také poskytnout opravu kódu, která představuje úpravu zdrojového kódu uživatele.</span><span class="sxs-lookup"><span data-stu-id="89514-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="89514-112">V tomto kurzu se vytvoří analyzátor, který najde deklarace místních proměnných, které by se daly deklarovat pomocí `const` modifikátoru, ale ne.</span><span class="sxs-lookup"><span data-stu-id="89514-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="89514-113">Oprava doprovodného kódu upraví tyto deklarace a přidá `const` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="89514-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="89514-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89514-114">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="89514-115">Aktuální šablona sady Visual Studio **Analyzer s opravou kódu (.NET Standard)** obsahuje známou chybu a měla by být opravena ve verzi Visual Studio 2019 verze 16,7.</span><span class="sxs-lookup"><span data-stu-id="89514-115">The current Visual Studio **Analyzer with code fix (.NET Standard)** template has a known bug in it and should be fixed in Visual Studio 2019 version 16.7.</span></span> <span data-ttu-id="89514-116">Projekty v šabloně nebudou zkompilovány, pokud nejsou provedeny následující změny:</span><span class="sxs-lookup"><span data-stu-id="89514-116">The projects in the template will not compile unless the following changes are made:</span></span>
>
> 1. <span data-ttu-id="89514-117">Výběr **nástrojů**  >  **Možnosti**nástroje  >  **Správce balíčků NuGet**  >  **zdroje balíčků**</span><span class="sxs-lookup"><span data-stu-id="89514-117">Select **Tools** > **Options** > **NuGet Package Manager** > **Package Sources**</span></span>
>    - <span data-ttu-id="89514-118">Kliknutím na tlačítko plus přidejte nový zdroj:</span><span class="sxs-lookup"><span data-stu-id="89514-118">Select the plus button, to add a new source:</span></span>
>    - <span data-ttu-id="89514-119">Nastavte **zdroj** na `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` a vyberte **aktualizovat** .</span><span class="sxs-lookup"><span data-stu-id="89514-119">Set the **Source** to `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` and select **Update**</span></span>
> 1. <span data-ttu-id="89514-120">Z **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **MakeConst. vsix** a vyberte **Upravit soubor projektu** .</span><span class="sxs-lookup"><span data-stu-id="89514-120">From the **Solution Explorer**, right-click on the **MakeConst.Vsix** project, and select **Edit Project File**</span></span>
>    - <span data-ttu-id="89514-121">Aktualizujte `<AssemblyName>` uzel pro přidání `.Visx` přípony:</span><span class="sxs-lookup"><span data-stu-id="89514-121">Update the `<AssemblyName>` node to add the `.Visx` suffix:</span></span>
>      - `<AssemblyName>MakeConst.Vsix</AssemblyName>`
>    - <span data-ttu-id="89514-122">Aktualizujte `<ProjectReference>` uzel na řádku 41 pro změnu `TargetFramework` hodnoty:</span><span class="sxs-lookup"><span data-stu-id="89514-122">Update the `<ProjectReference>` node on line 41 to alter the `TargetFramework` value:</span></span>
>      - `<ProjectReference Update="@(ProjectReference)" AdditionalProperties="TargetFramework=netstandard2.0" />`
> 1. <span data-ttu-id="89514-123">Aktualizujte soubor *MakeConstUnitTests.cs* v projektu *MakeConst. test* :</span><span class="sxs-lookup"><span data-stu-id="89514-123">Update the *MakeConstUnitTests.cs* file, in the *MakeConst.Test* project:</span></span>
>    - <span data-ttu-id="89514-124">Změňte řádek 9 na následující, Všimněte si změny oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="89514-124">Change line 9 to the following, notice namespace alteration:</span></span>
>      - `using Verify = Microsoft.CodeAnalysis.CSharp.Testing.MSTest.CodeFixVerifier<`
>    - <span data-ttu-id="89514-125">Řádek 24 změňte na následující metodu:</span><span class="sxs-lookup"><span data-stu-id="89514-125">Change line 24 to the following method:</span></span>
>      - `await Verify.VerifyAnalyzerAsync(test);`
>    - <span data-ttu-id="89514-126">Řádek 62 změňte na následující metodu:</span><span class="sxs-lookup"><span data-stu-id="89514-126">Change line 62 to the following method:</span></span>
>      - `await Verify.VerifyCodeFixAsync(test, expected, fixtest);`

- [<span data-ttu-id="89514-127">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="89514-127">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [<span data-ttu-id="89514-128">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="89514-128">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="89514-129">**.NET COMPILER Platform SDK** bude nutné nainstalovat pomocí instalační program pro Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="89514-129">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="89514-130">Existuje několik kroků k vytvoření a ověření analyzátoru:</span><span class="sxs-lookup"><span data-stu-id="89514-130">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="89514-131">Vytvořte řešení.</span><span class="sxs-lookup"><span data-stu-id="89514-131">Create the solution.</span></span>
1. <span data-ttu-id="89514-132">Zaregistrujte název a popis analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="89514-132">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="89514-133">Upozornění a doporučení analyzátoru sestav.</span><span class="sxs-lookup"><span data-stu-id="89514-133">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="89514-134">Implementací opravy kódu přijměte doporučení.</span><span class="sxs-lookup"><span data-stu-id="89514-134">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="89514-135">Zlepšete analýzu prostřednictvím jednotkových testů.</span><span class="sxs-lookup"><span data-stu-id="89514-135">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="89514-136">Prozkoumat šablonu analyzátoru</span><span class="sxs-lookup"><span data-stu-id="89514-136">Explore the analyzer template</span></span>

<span data-ttu-id="89514-137">Analyzátor hlásí uživateli všechny deklarace místních proměnných, které lze převést na místní konstanty.</span><span class="sxs-lookup"><span data-stu-id="89514-137">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="89514-138">Zvažte například následující kód:</span><span class="sxs-lookup"><span data-stu-id="89514-138">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="89514-139">Ve výše uvedeném kódu `x` je přiřazena konstantní hodnota a nikdy se nemění.</span><span class="sxs-lookup"><span data-stu-id="89514-139">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="89514-140">Dá se deklarovat pomocí `const` modifikátoru:</span><span class="sxs-lookup"><span data-stu-id="89514-140">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="89514-141">Analýza, která určuje, zda může být proměnná vytvořena, je vyžadována syntaktickou analýzou, konstantní analýzou výrazu inicializátoru a analýzou toku dat, aby se zajistilo, že proměnná nebude nikdy zapsána do.</span><span class="sxs-lookup"><span data-stu-id="89514-141">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="89514-142">.NET Compiler Platform poskytuje rozhraní API, která usnadňují provádění této analýzy.</span><span class="sxs-lookup"><span data-stu-id="89514-142">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="89514-143">Prvním krokem je vytvoření nového **analyzátoru C# s projektem opravit kód** .</span><span class="sxs-lookup"><span data-stu-id="89514-143">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

- <span data-ttu-id="89514-144">V aplikaci Visual Studio vyberte **soubor > nový > projekt...** zobrazí se dialogové okno Nový projekt.</span><span class="sxs-lookup"><span data-stu-id="89514-144">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="89514-145">V části **Visual C# > rozšiřitelnosti**vyberte možnost **analyzátor s opravou kódu (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="89514-145">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="89514-146">Pojmenujte projekt "**MakeConst**" a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="89514-146">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="89514-147">Analyzátor se šablonou opravy kódu vytvoří tři projekty: jeden obsahuje analyzátor a opravu kódu, druhým je projekt testu jednotek a třetí je projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="89514-147">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="89514-148">Výchozí spouštěný projekt je projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="89514-148">The default startup project is the VSIX project.</span></span> <span data-ttu-id="89514-149">Stisknutím klávesy <kbd>F5</kbd> spusťte projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="89514-149">Press <kbd>F5</kbd> to start the VSIX project.</span></span> <span data-ttu-id="89514-150">Tím se spustí druhá instance sady Visual Studio, která zavedla nový analyzátor.</span><span class="sxs-lookup"><span data-stu-id="89514-150">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="89514-151">Při spuštění analyzátoru spustíte druhou kopii sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89514-151">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="89514-152">Tato druhá kopie používá k uložení nastavení jiný podregistr registru.</span><span class="sxs-lookup"><span data-stu-id="89514-152">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="89514-153">To umožňuje odlišit nastavení vizuálu v obou kopiích sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89514-153">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="89514-154">Můžete vybrat jiný motiv pro experimentální běh sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89514-154">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="89514-155">Kromě toho nevytvářejte roaming nastavení ani přihlášení k účtu aplikace Visual Studio pomocí experimentálního spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89514-155">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="89514-156">Který udržuje nastavení odlišně.</span><span class="sxs-lookup"><span data-stu-id="89514-156">That keeps the settings different.</span></span>

<span data-ttu-id="89514-157">Ve druhé instanci sady Visual Studio, kterou jste právě spustili, vytvořte nový projekt konzolové aplikace v jazyce C# (.NET Core nebo .NET Framework projekt budou fungovat na úrovni zdroje.) Najeďte myší na token podtrženým vlnovkou a zobrazí se text upozornění, který je k dispozici v analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="89514-157">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="89514-158">Šablona vytvoří analyzátor, který ohlásí upozornění na každou deklaraci typu, kde název typu obsahuje malá písmena, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="89514-158">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Upozornění pro generování sestav analyzátoru](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="89514-160">Šablona také poskytuje opravu kódu, která změní jakýkoli název typu obsahující malá písmena na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="89514-160">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="89514-161">Můžete kliknout na žárovku, která se zobrazuje s upozorněním, a zobrazit navrhované změny.</span><span class="sxs-lookup"><span data-stu-id="89514-161">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="89514-162">Přijetí navrhovaných změn aktualizuje název typu a všechny odkazy na daný typ v řešení.</span><span class="sxs-lookup"><span data-stu-id="89514-162">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="89514-163">Teď, když jste viděli počáteční analyzátor v akci, zavřete druhou instanci sady Visual Studio a vraťte se do projektu analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="89514-163">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="89514-164">Nemusíte spouštět druhou kopii sady Visual Studio a vytvořit nový kód pro otestování všech změn v analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="89514-164">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="89514-165">Šablona také vytvoří projekt testu jednotek za vás.</span><span class="sxs-lookup"><span data-stu-id="89514-165">The template also creates a unit test project for you.</span></span> <span data-ttu-id="89514-166">Tento projekt obsahuje dva testy.</span><span class="sxs-lookup"><span data-stu-id="89514-166">That project contains two tests.</span></span> <span data-ttu-id="89514-167">`TestMethod1`zobrazuje typický formát testu, který analyzuje kód bez aktivace diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="89514-167">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="89514-168">`TestMethod2`zobrazuje formát testu, který aktivuje diagnostiku a poté použije navrhovanou opravu kódu.</span><span class="sxs-lookup"><span data-stu-id="89514-168">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="89514-169">Při sestavování analyzátoru a opravy kódu budete psát testy pro různé struktury kódu, abyste ověřili svoji práci.</span><span class="sxs-lookup"><span data-stu-id="89514-169">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="89514-170">Testy jednotek pro analyzátory jsou mnohem rychlejší než interaktivní testování pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89514-170">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="89514-171">Testy jednotek analyzátoru jsou skvělým nástrojem, když víte, které konstrukce kódu by měly a nemají aktivovat analyzátor.</span><span class="sxs-lookup"><span data-stu-id="89514-171">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="89514-172">Načítání analyzátoru v jiné kopii sady Visual Studio je skvělý nástroj pro zkoumání a hledání konstrukcí, na které jste se ještě nemuseli myslet.</span><span class="sxs-lookup"><span data-stu-id="89514-172">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="89514-173">Vytvoření registrací analyzátoru</span><span class="sxs-lookup"><span data-stu-id="89514-173">Create analyzer registrations</span></span>

<span data-ttu-id="89514-174">Šablona vytvoří počáteční `DiagnosticAnalyzer` třídu v souboru **MakeConstAnalyzer.cs** .</span><span class="sxs-lookup"><span data-stu-id="89514-174">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="89514-175">Tento počáteční analyzátor zobrazuje dvě důležité vlastnosti každého analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="89514-175">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="89514-176">Každý diagnostický analyzátor musí poskytovat `[DiagnosticAnalyzer]` atribut, který popisuje jazyk, na kterém pracuje.</span><span class="sxs-lookup"><span data-stu-id="89514-176">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="89514-177">Každý diagnostický analyzátor musí být odvozen od <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> třídy.</span><span class="sxs-lookup"><span data-stu-id="89514-177">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="89514-178">Šablona také zobrazuje základní funkce, které jsou součástí jakéhokoli analyzátoru:</span><span class="sxs-lookup"><span data-stu-id="89514-178">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="89514-179">Proveďte registraci akcí.</span><span class="sxs-lookup"><span data-stu-id="89514-179">Register actions.</span></span> <span data-ttu-id="89514-180">Akce reprezentují změny kódu, které by měly aktivovat analyzátor, aby prozkoumali kód pro porušení.</span><span class="sxs-lookup"><span data-stu-id="89514-180">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="89514-181">Když Visual Studio detekuje úpravy kódu, které odpovídají zaregistrované akci, volá metodu zaregistrovanou analyzátorem.</span><span class="sxs-lookup"><span data-stu-id="89514-181">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="89514-182">Vytvořte diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="89514-182">Create diagnostics.</span></span> <span data-ttu-id="89514-183">Když analyzátor zjistí porušení, vytvoří objekt diagnostiky, který Visual Studio používá k upozorňování uživatele na porušení.</span><span class="sxs-lookup"><span data-stu-id="89514-183">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="89514-184">Akce zaregistrujete v přepsání <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="89514-184">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="89514-185">V tomto kurzu navštívíte **uzly syntaxe** , které hledají místní deklarace, a zjistíte, které z nich mají konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="89514-185">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="89514-186">Pokud by deklarace mohla být konstantní, analyzátor vytvoří a nahlásí diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="89514-186">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="89514-187">Prvním krokem je aktualizovat konstanty a `Initialize` metodu registrace, aby tyto konstanty označovaly analyzátor "Make const".</span><span class="sxs-lookup"><span data-stu-id="89514-187">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="89514-188">Většina řetězcových konstant je definována v souboru prostředků řetězce.</span><span class="sxs-lookup"><span data-stu-id="89514-188">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="89514-189">Pro snazší lokalizaci byste měli postupovat podle tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="89514-189">You should follow that practice for easier localization.</span></span> <span data-ttu-id="89514-190">Otevřete soubor **Resources. resx** pro projekt analyzátoru **MakeConst** .</span><span class="sxs-lookup"><span data-stu-id="89514-190">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="89514-191">Tím se zobrazí editor prostředků.</span><span class="sxs-lookup"><span data-stu-id="89514-191">This displays the resource editor.</span></span> <span data-ttu-id="89514-192">Aktualizujte prostředky řetězce následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="89514-192">Update the string resources as follows:</span></span>

- <span data-ttu-id="89514-193">Možnost změnit `AnalyzerTitle` na proměnnou lze vytvořit jako konstantu.</span><span class="sxs-lookup"><span data-stu-id="89514-193">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
- <span data-ttu-id="89514-194">Možnost změnit `AnalyzerMessageFormat` na lze nastavit jako konstantu.</span><span class="sxs-lookup"><span data-stu-id="89514-194">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
- <span data-ttu-id="89514-195">Změňte `AnalyzerDescription` na "vytvořit konstantu".</span><span class="sxs-lookup"><span data-stu-id="89514-195">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="89514-196">Také změňte rozevírací seznam **modifikátor přístupu** na `public` .</span><span class="sxs-lookup"><span data-stu-id="89514-196">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="89514-197">To usnadňuje používání těchto konstant v testování částí.</span><span class="sxs-lookup"><span data-stu-id="89514-197">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="89514-198">Po dokončení by se měl editor prostředků zobrazit tak, jak ukazuje následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="89514-198">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Aktualizace prostředků řetězců](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="89514-200">Zbývající změny jsou v souboru analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="89514-200">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="89514-201">Otevřete **MakeConstAnalyzer.cs** v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89514-201">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="89514-202">Změňte zaregistrovanou akci z jedné, která funguje na symbolech, které fungují na syntaxi.</span><span class="sxs-lookup"><span data-stu-id="89514-202">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="89514-203">V `MakeConstAnalyzerAnalyzer.Initialize` metodě Najděte řádek, který zaregistruje akci na symboly:</span><span class="sxs-lookup"><span data-stu-id="89514-203">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="89514-204">Nahraďte ji následujícím řádkem:</span><span class="sxs-lookup"><span data-stu-id="89514-204">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="89514-205">Po této změně můžete `AnalyzeSymbol` metodu odstranit.</span><span class="sxs-lookup"><span data-stu-id="89514-205">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="89514-206">Tento analyzátor prověřuje <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType> příkazy, nikoli <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="89514-206">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="89514-207">Všimněte si, že `AnalyzeNode` pod ní jsou červené vlnovky.</span><span class="sxs-lookup"><span data-stu-id="89514-207">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="89514-208">Kód, který jste právě přidali, odkazuje na `AnalyzeNode` metodu, která nebyla deklarována.</span><span class="sxs-lookup"><span data-stu-id="89514-208">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="89514-209">Deklarujte tuto metodu pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="89514-209">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="89514-210">`Category`V **MakeConstAnalyzer.cs** změňte na "využití", jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="89514-210">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="89514-211">Najde místní deklarace, které by mohly být const.</span><span class="sxs-lookup"><span data-stu-id="89514-211">Find local declarations that could be const</span></span>

<span data-ttu-id="89514-212">Je čas zapsat první verzi `AnalyzeNode` metody.</span><span class="sxs-lookup"><span data-stu-id="89514-212">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="89514-213">Měl by hledat jednu místní deklaraci, která by mohla být `const` , ale ne, podobně jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="89514-213">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="89514-214">Prvním krokem je najít místní deklarace.</span><span class="sxs-lookup"><span data-stu-id="89514-214">The first step is to find local declarations.</span></span> <span data-ttu-id="89514-215">Do MakeConstAnalyzer.cs přidejte následující kód `AnalyzeNode` : **MakeConstAnalyzer.cs**</span><span class="sxs-lookup"><span data-stu-id="89514-215">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="89514-216">Toto přetypování vždy proběhne úspěšně, protože analyzátor zaregistroval pro změny místních deklarací a pouze místní deklarace.</span><span class="sxs-lookup"><span data-stu-id="89514-216">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="89514-217">Žádný jiný typ uzlu neaktivuje volání `AnalyzeNode` metody.</span><span class="sxs-lookup"><span data-stu-id="89514-217">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="89514-218">V dalším kroku ověřte deklaraci všech `const` modifikátorů.</span><span class="sxs-lookup"><span data-stu-id="89514-218">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="89514-219">Pokud je najdete, vraťte se hned.</span><span class="sxs-lookup"><span data-stu-id="89514-219">If you find them, return immediately.</span></span> <span data-ttu-id="89514-220">Následující kód vyhledá všechny `const` modifikátory v místní deklaraci:</span><span class="sxs-lookup"><span data-stu-id="89514-220">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="89514-221">Nakonec je nutné ověřit, zda může být proměnná `const` .</span><span class="sxs-lookup"><span data-stu-id="89514-221">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="89514-222">To znamená, že se po inicializaci nikdy nepřiřazuje.</span><span class="sxs-lookup"><span data-stu-id="89514-222">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="89514-223">Pomocí nástroje se provede nějaká Sémantická analýza <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext> .</span><span class="sxs-lookup"><span data-stu-id="89514-223">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="89514-224">Argument můžete použít `context` k určení, zda lze vytvořit deklaraci lokální proměnné `const` .</span><span class="sxs-lookup"><span data-stu-id="89514-224">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="89514-225"><xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType>Představuje všechny sémantické informace v jednom zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="89514-225">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents all of semantic information in a single source file.</span></span> <span data-ttu-id="89514-226">Další informace najdete v článku, který pokrývá [sémantické modely](../work-with-semantics.md).</span><span class="sxs-lookup"><span data-stu-id="89514-226">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="89514-227">Použijete <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> k provedení analýzy toku dat v příkazu místní deklarace.</span><span class="sxs-lookup"><span data-stu-id="89514-227">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="89514-228">Pak použijete výsledky této analýzy toku dat, abyste zajistili, že místní proměnná nebude zapsána novou hodnotou kdekoli jinde.</span><span class="sxs-lookup"><span data-stu-id="89514-228">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="89514-229">Zavolejte <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> metodu rozšíření pro načtení <xref:Microsoft.CodeAnalysis.ILocalSymbol> proměnné a ověřte, že není obsažena v <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> kolekci analýzy toku dat.</span><span class="sxs-lookup"><span data-stu-id="89514-229">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="89514-230">Na konec metody přidejte následující kód `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="89514-230">Add the following code to the end of the `AnalyzeNode` method:</span></span>

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

<span data-ttu-id="89514-231">Právě přidaný kód zajišťuje, že proměnná nebude změněna, a je proto možné ji vytvořit `const` .</span><span class="sxs-lookup"><span data-stu-id="89514-231">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="89514-232">Je čas vyvolat diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="89514-232">It's time to raise the diagnostic.</span></span> <span data-ttu-id="89514-233">Jako poslední řádek přidejte následující kód `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="89514-233">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="89514-234">Svůj průběh můžete zjistit stisknutím klávesy <kbd>F5</kbd> ke spuštění analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="89514-234">You can check your progress by pressing <kbd>F5</kbd> to run your analyzer.</span></span> <span data-ttu-id="89514-235">Můžete načíst konzolovou aplikaci, kterou jste vytvořili dříve, a pak přidat následující zkušební kód:</span><span class="sxs-lookup"><span data-stu-id="89514-235">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="89514-236">Měla by se zobrazit žárovka a analyzátor by měl ohlásit diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="89514-236">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="89514-237">Žárovka však stále používá opravu kódu vygenerovanou šablonou a oznamuje vám, že může být proveden na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="89514-237">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="89514-238">V další části se dozvíte, jak napsat opravu kódu.</span><span class="sxs-lookup"><span data-stu-id="89514-238">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="89514-239">Zapsat opravu kódu</span><span class="sxs-lookup"><span data-stu-id="89514-239">Write the code fix</span></span>

<span data-ttu-id="89514-240">Analyzátor může poskytovat jednu nebo více oprav kódu.</span><span class="sxs-lookup"><span data-stu-id="89514-240">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="89514-241">Oprava kódu definuje úpravu, která řeší nahlášený problém.</span><span class="sxs-lookup"><span data-stu-id="89514-241">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="89514-242">Pro analyzátor, který jste vytvořili, můžete zadat opravu kódu, která vloží klíčové slovo const:</span><span class="sxs-lookup"><span data-stu-id="89514-242">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="89514-243">Uživatel zvolí tuto možnost z uživatelského rozhraní žárovky v editoru a Visual Studio změní kód.</span><span class="sxs-lookup"><span data-stu-id="89514-243">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="89514-244">Otevřete soubor **MakeConstCodeFixProvider.cs** , který šablona přidala.</span><span class="sxs-lookup"><span data-stu-id="89514-244">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="89514-245">Tato oprava kódu je již zapojena do ID diagnostiky vytvořeného analyzátorem diagnostiky, ale ještě neimplementuje správnou transformaci kódu.</span><span class="sxs-lookup"><span data-stu-id="89514-245">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="89514-246">Nejprve byste měli odebrat některý kód šablony.</span><span class="sxs-lookup"><span data-stu-id="89514-246">First you should remove some of the template code.</span></span> <span data-ttu-id="89514-247">Změňte řetězec nadpisu na "vytvořit konstantu":</span><span class="sxs-lookup"><span data-stu-id="89514-247">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="89514-248">Dále odstraňte `MakeUppercaseAsync` metodu.</span><span class="sxs-lookup"><span data-stu-id="89514-248">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="89514-249">Už se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="89514-249">It no longer applies.</span></span>

<span data-ttu-id="89514-250">Všichni poskytovatelé oprav kódu jsou odvozeni z <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider> .</span><span class="sxs-lookup"><span data-stu-id="89514-250">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="89514-251">Všechny jsou popsány <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> , aby nahlásily dostupné opravy kódu.</span><span class="sxs-lookup"><span data-stu-id="89514-251">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="89514-252">V nástroji `RegisterCodeFixesAsync` změňte typ nadřazeného uzlu, který hledáte, aby <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> odpovídal diagnostice:</span><span class="sxs-lookup"><span data-stu-id="89514-252">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="89514-253">Dále změňte poslední řádek pro registraci opravy kódu.</span><span class="sxs-lookup"><span data-stu-id="89514-253">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="89514-254">Vaše oprava vytvoří nový dokument, který je výsledkem přidání `const` modifikátoru k existující deklaraci:</span><span class="sxs-lookup"><span data-stu-id="89514-254">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="89514-255">Všimněte si červené vlnovky v kódu, který jste právě přidali na symbol `MakeConstAsync` .</span><span class="sxs-lookup"><span data-stu-id="89514-255">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="89514-256">Přidejte deklaraci `MakeConstAsync` jako následující kód:</span><span class="sxs-lookup"><span data-stu-id="89514-256">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="89514-257">Vaše nová `MakeConstAsync` Metoda provede transformaci <xref:Microsoft.CodeAnalysis.Document> zdrojového souboru uživatele do nového <xref:Microsoft.CodeAnalysis.Document> , který nyní obsahuje `const` deklaraci.</span><span class="sxs-lookup"><span data-stu-id="89514-257">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="89514-258">Vytvoříte nový `const` token klíčového slova pro vložení na začátek prohlášení.</span><span class="sxs-lookup"><span data-stu-id="89514-258">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="89514-259">Buďte opatrní, abyste nejdřív odebrali všechny úvodní minihry z prvního tokenu příkazu deklarace a připojili ho k `const` tokenu.</span><span class="sxs-lookup"><span data-stu-id="89514-259">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="89514-260">Do metody `MakeConstAsync` přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="89514-260">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="89514-261">Dále přidejte `const` token k deklaraci pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="89514-261">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="89514-262">Dále naformátujte novou deklaraci tak, aby odpovídala pravidlům formátování jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="89514-262">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="89514-263">Formátování změn tak, aby odpovídalo existujícímu kódu, vytvoří lepší prostředí.</span><span class="sxs-lookup"><span data-stu-id="89514-263">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="89514-264">Přidejte následující příkaz hned za existující kód:</span><span class="sxs-lookup"><span data-stu-id="89514-264">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="89514-265">Pro tento kód je vyžadován nový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="89514-265">A new namespace is required for this code.</span></span> <span data-ttu-id="89514-266">`using`Do horní části souboru přidejte následující direktivu:</span><span class="sxs-lookup"><span data-stu-id="89514-266">Add the following `using` directive to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="89514-267">Posledním krokem je provedení úprav.</span><span class="sxs-lookup"><span data-stu-id="89514-267">The final step is to make your edit.</span></span> <span data-ttu-id="89514-268">Tento postup má tři kroky:</span><span class="sxs-lookup"><span data-stu-id="89514-268">There are three steps to this process:</span></span>

1. <span data-ttu-id="89514-269">Získejte popisovač pro existující dokument.</span><span class="sxs-lookup"><span data-stu-id="89514-269">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="89514-270">Vytvořte nový dokument nahrazením existující deklarace novou deklarací.</span><span class="sxs-lookup"><span data-stu-id="89514-270">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="89514-271">Vrátí nový dokument.</span><span class="sxs-lookup"><span data-stu-id="89514-271">Return the new document.</span></span>

<span data-ttu-id="89514-272">Na konec metody přidejte následující kód `MakeConstAsync` :</span><span class="sxs-lookup"><span data-stu-id="89514-272">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="89514-273">Oprava kódu je připravená k vyzkoušení.</span><span class="sxs-lookup"><span data-stu-id="89514-273">Your code fix is ready to try.</span></span>  <span data-ttu-id="89514-274">Stisknutím klávesy <kbd>F5</kbd> spusťte projekt analyzátoru v druhé instanci aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89514-274">Press <kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="89514-275">Ve druhé instanci sady Visual Studio vytvořte nový projekt konzolové aplikace v jazyce C# a přidejte několik deklarací místních proměnných inicializovaných s konstantními hodnotami do metody Main.</span><span class="sxs-lookup"><span data-stu-id="89514-275">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="89514-276">Uvidíte, že jsou hlášeny jako upozornění, jak je uvedeno níže.</span><span class="sxs-lookup"><span data-stu-id="89514-276">You'll see that they are reported as warnings as below.</span></span>

![Může vytvořit konstantní upozornění.](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="89514-278">Provedli jste spoustu pokroku.</span><span class="sxs-lookup"><span data-stu-id="89514-278">You've made a lot of progress.</span></span> <span data-ttu-id="89514-279">V deklaracích, které mohou být provedeny, jsou vlnovky `const` .</span><span class="sxs-lookup"><span data-stu-id="89514-279">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="89514-280">I když ale pořád funguje.</span><span class="sxs-lookup"><span data-stu-id="89514-280">But there is still work to do.</span></span> <span data-ttu-id="89514-281">To funguje dobře, pokud přidáte `const` do deklarací, které začínají na `i` , `j` a nakonec a nakonec `k` .</span><span class="sxs-lookup"><span data-stu-id="89514-281">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="89514-282">Pokud však přidáte `const` Modifikátor v jiném pořadí, počínaje verzí `k` , váš analyzátor vytvoří chyby: `k` nelze deklarovat `const` , pokud `i` `j` již nejsou a `const` .</span><span class="sxs-lookup"><span data-stu-id="89514-282">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="89514-283">Máte možnost provést další analýzu, abyste se ujistili, že je možné zpracovat různé způsoby, které lze deklarovat a inicializovat.</span><span class="sxs-lookup"><span data-stu-id="89514-283">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="89514-284">Vytváření testů řízených daty</span><span class="sxs-lookup"><span data-stu-id="89514-284">Build data driven tests</span></span>

<span data-ttu-id="89514-285">Analyzátor a oprava kódu fungují na jednoduchém případu jedné deklarace, která může být vytvořena jako const.</span><span class="sxs-lookup"><span data-stu-id="89514-285">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="89514-286">Existuje mnoho možných příkazů deklarace, kde tato implementace způsobuje chyby.</span><span class="sxs-lookup"><span data-stu-id="89514-286">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="89514-287">Tyto případy se řeší při práci s knihovnou testu jednotek zapsanou šablonou.</span><span class="sxs-lookup"><span data-stu-id="89514-287">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="89514-288">Je mnohem rychlejší než opakované otevření druhé kopie sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89514-288">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="89514-289">Otevřete soubor **MakeConstUnitTests.cs** v projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="89514-289">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="89514-290">Šablona vytvořila dva testy, které následují dva běžné vzory pro analyzátor a opravu testování částí kódu.</span><span class="sxs-lookup"><span data-stu-id="89514-290">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="89514-291">`TestMethod1`zobrazuje vzor testu, který zajišťuje, že analyzátor neohlásí diagnostiku, pokud by neměl.</span><span class="sxs-lookup"><span data-stu-id="89514-291">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="89514-292">`TestMethod2`zobrazuje vzor pro vytváření sestav diagnostiky a spuštění opravy kódu.</span><span class="sxs-lookup"><span data-stu-id="89514-292">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="89514-293">Kód pro téměř každý test pro analyzátor následuje po jednom z těchto dvou vzorů.</span><span class="sxs-lookup"><span data-stu-id="89514-293">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="89514-294">V prvním kroku můžete tyto testy přepracovat jako testy řízené daty.</span><span class="sxs-lookup"><span data-stu-id="89514-294">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="89514-295">Pak bude snadné vytvořit nové testy přidáním nových řetězcových konstant pro reprezentaci různých testovacích vstupů.</span><span class="sxs-lookup"><span data-stu-id="89514-295">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="89514-296">V rámci efektivity je prvním krokem refaktorování dvou testů do testů řízených daty.</span><span class="sxs-lookup"><span data-stu-id="89514-296">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="89514-297">Pak stačí definovat několik řetězcových konstant pro každý nový test.</span><span class="sxs-lookup"><span data-stu-id="89514-297">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="89514-298">Když provádíte refaktoring, přejmenujte obě metody pro lepší názvy.</span><span class="sxs-lookup"><span data-stu-id="89514-298">While you are refactoring, rename both methods to better names.</span></span> <span data-ttu-id="89514-299">Nahraďte `TestMethod1` tímto testem, který zajišťuje, že se neaktivuje žádná diagnostika:</span><span class="sxs-lookup"><span data-stu-id="89514-299">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="89514-300">Můžete vytvořit nový řádek dat pro tento test definováním jakékoli fragmenty kódu, který by neměl způsobit, že diagnostika spustí upozornění.</span><span class="sxs-lookup"><span data-stu-id="89514-300">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="89514-301">Toto přetížení `VerifyCSharpDiagnostic` předává, když není pro fragment zdrojového kódu aktivována žádná Diagnostika.</span><span class="sxs-lookup"><span data-stu-id="89514-301">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="89514-302">Dále nahraďte `TestMethod2` tímto testem, který zajistí vyvolání diagnostiky, a opravu kódu použitou pro fragment zdrojového kódu:</span><span class="sxs-lookup"><span data-stu-id="89514-302">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

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

<span data-ttu-id="89514-303">Předchozí kód také provedl několik změn kódu, který vytváří očekávaný výsledek diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="89514-303">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="89514-304">Používá veřejné konstanty registrované v `MakeConst` analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="89514-304">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="89514-305">Kromě toho používá dvě řetězcové konstanty pro vstupní a pevný zdroj.</span><span class="sxs-lookup"><span data-stu-id="89514-305">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="89514-306">Do třídy přidejte následující řetězcové konstanty `UnitTest` :</span><span class="sxs-lookup"><span data-stu-id="89514-306">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="89514-307">Spusťte tyto dva testy, abyste se ujistili, že jsou průchody.</span><span class="sxs-lookup"><span data-stu-id="89514-307">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="89514-308">V aplikaci Visual Studio otevřete **Průzkumníka testů** výběrem **test**  >  **Windows**  >  **Průzkumník testů**systému Windows.</span><span class="sxs-lookup"><span data-stu-id="89514-308">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span> <span data-ttu-id="89514-309">Pak vyberte odkaz **Spustit vše** .</span><span class="sxs-lookup"><span data-stu-id="89514-309">Then select the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="89514-310">Vytvořit testy pro platné deklarace</span><span class="sxs-lookup"><span data-stu-id="89514-310">Create tests for valid declarations</span></span>

<span data-ttu-id="89514-311">Obecně platí, že analyzátory by měly skončit co nejrychleji, což má minimální práci.</span><span class="sxs-lookup"><span data-stu-id="89514-311">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="89514-312">Visual Studio volá zaregistrované analyzátory jako kód úprav uživatele.</span><span class="sxs-lookup"><span data-stu-id="89514-312">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="89514-313">Odezva je klíčovým požadavkem.</span><span class="sxs-lookup"><span data-stu-id="89514-313">Responsiveness is a key requirement.</span></span> <span data-ttu-id="89514-314">Existuje několik testovacích případů pro kód, který by neměl vyvolat diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="89514-314">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="89514-315">Analyzátor již zpracovává jeden z těchto testů, případ, kdy je přiřazena proměnná po inicializaci.</span><span class="sxs-lookup"><span data-stu-id="89514-315">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="89514-316">Přidejte následující řetězcovou konstantu do testů pro reprezentaci tohoto případu:</span><span class="sxs-lookup"><span data-stu-id="89514-316">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="89514-317">Pak přidejte řádek dat pro tento test, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="89514-317">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="89514-318">Tento test se také projde.</span><span class="sxs-lookup"><span data-stu-id="89514-318">This test passes as well.</span></span> <span data-ttu-id="89514-319">Dále přidejte konstanty pro podmínky, které jste ještě nezpracovali:</span><span class="sxs-lookup"><span data-stu-id="89514-319">Next, add constants for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="89514-320">Deklarace, které jsou již `const` , protože jsou již const:</span><span class="sxs-lookup"><span data-stu-id="89514-320">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="89514-321">Deklarace, které nemají žádný inicializátor, protože neexistuje žádná hodnota, která se má použít:</span><span class="sxs-lookup"><span data-stu-id="89514-321">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="89514-322">Deklarace, kde inicializátor není konstanta, protože nemohou být konstanty v čase kompilace:</span><span class="sxs-lookup"><span data-stu-id="89514-322">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="89514-323">Může být ještě složitější, protože C# umožňuje více deklarací v jednom příkazu.</span><span class="sxs-lookup"><span data-stu-id="89514-323">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="89514-324">Vezměte v úvahu následující řetězcové konstanty testovacího případu:</span><span class="sxs-lookup"><span data-stu-id="89514-324">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="89514-325">Proměnná `i` může být vytvořená jako konstanta, ale proměnná ale `j` nemůže.</span><span class="sxs-lookup"><span data-stu-id="89514-325">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="89514-326">Proto tento příkaz nelze vytvořit jako deklaraci konstanty.</span><span class="sxs-lookup"><span data-stu-id="89514-326">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="89514-327">Přidejte `DataRow` deklarace pro všechny tyto testy:</span><span class="sxs-lookup"><span data-stu-id="89514-327">Add the `DataRow` declarations for all these tests:</span></span>

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

<span data-ttu-id="89514-328">Spusťte testy znovu a uvidíte, že tyto nové testovací případy selžou.</span><span class="sxs-lookup"><span data-stu-id="89514-328">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="89514-329">Aktualizace analyzátoru tak, aby ignoroval správné deklarace</span><span class="sxs-lookup"><span data-stu-id="89514-329">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="89514-330">K `AnalyzeNode` odfiltrování kódu, který splňuje tyto podmínky, potřebujete nějaké vylepšení metody analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="89514-330">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="89514-331">Jsou to všechny související podmínky, takže podobné změny vyřeší všechny tyto podmínky.</span><span class="sxs-lookup"><span data-stu-id="89514-331">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="89514-332">Proveďte následující změny `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="89514-332">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="89514-333">Vaše Sémantická analýza prozkoumala deklaraci jedné proměnné.</span><span class="sxs-lookup"><span data-stu-id="89514-333">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="89514-334">Tento kód musí být ve `foreach` smyčce, která prověřuje všechny proměnné deklarované ve stejném příkazu.</span><span class="sxs-lookup"><span data-stu-id="89514-334">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="89514-335">Každá deklarovaná proměnná musí mít inicializátor.</span><span class="sxs-lookup"><span data-stu-id="89514-335">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="89514-336">Každý inicializátor deklarované proměnné musí být konstanta v čase kompilace.</span><span class="sxs-lookup"><span data-stu-id="89514-336">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="89514-337">V `AnalyzeNode` metodě nahraďte původní sémantickou analýzu:</span><span class="sxs-lookup"><span data-stu-id="89514-337">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

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

<span data-ttu-id="89514-338">s následujícím fragmentem kódu:</span><span class="sxs-lookup"><span data-stu-id="89514-338">with the following code snippet:</span></span>

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

<span data-ttu-id="89514-339">První `foreach` smyčka prověřuje každou deklaraci proměnné pomocí syntaktické analýzy.</span><span class="sxs-lookup"><span data-stu-id="89514-339">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="89514-340">První ověření zaručuje, že proměnná má inicializátor.</span><span class="sxs-lookup"><span data-stu-id="89514-340">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="89514-341">Druhá kontrolu garantuje, že inicializátor je konstanta.</span><span class="sxs-lookup"><span data-stu-id="89514-341">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="89514-342">Druhá smyčka má původní sémantickou analýzu.</span><span class="sxs-lookup"><span data-stu-id="89514-342">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="89514-343">Sémantické kontroly jsou samostatné smyčky, protože mají větší vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="89514-343">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="89514-344">Spusťte testy znovu a měli byste je vidět, že jsou všechny passované.</span><span class="sxs-lookup"><span data-stu-id="89514-344">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="89514-345">Přidat konečný polský</span><span class="sxs-lookup"><span data-stu-id="89514-345">Add the final polish</span></span>

<span data-ttu-id="89514-346">Už jste téměř hotovi.</span><span class="sxs-lookup"><span data-stu-id="89514-346">You're almost done.</span></span> <span data-ttu-id="89514-347">Analyzátor může zpracovat několik dalších podmínek.</span><span class="sxs-lookup"><span data-stu-id="89514-347">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="89514-348">Visual Studio volá analyzátory, zatímco uživatel píše kód.</span><span class="sxs-lookup"><span data-stu-id="89514-348">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="89514-349">Často se jedná o případ, kdy se analyzátor bude volat pro kód, který se nekompiluje.</span><span class="sxs-lookup"><span data-stu-id="89514-349">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="89514-350">Metoda diagnostického analyzátoru `AnalyzeNode` nekontroluje, zda je konstantní hodnota převoditelná na typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="89514-350">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="89514-351">Aktuální implementace tak bude Happily převést nesprávnou deklaraci, jako je int i = "ABC", na místní konstantu.</span><span class="sxs-lookup"><span data-stu-id="89514-351">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="89514-352">Přidat řetězcovou konstantu zdrojového řetězce pro tuto podmínku:</span><span class="sxs-lookup"><span data-stu-id="89514-352">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="89514-353">Odkazové typy se navíc nezpracovávají správně.</span><span class="sxs-lookup"><span data-stu-id="89514-353">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="89514-354">Jediná hodnota konstanty povolená pro odkazový typ je `null` , s výjimkou případu <xref:System.String?displayProperty=nameWithType> , který umožňuje řetězcové literály.</span><span class="sxs-lookup"><span data-stu-id="89514-354">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="89514-355">Jinými slovy, `const string s = "abc"` je právní, ale není `const object s = "abc"` .</span><span class="sxs-lookup"><span data-stu-id="89514-355">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="89514-356">Tento fragment kódu ověřuje tuto podmínku:</span><span class="sxs-lookup"><span data-stu-id="89514-356">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="89514-357">Chcete-li být důkladnější, je nutné přidat další test, abyste se ujistili, že můžete vytvořit konstantní deklarace pro řetězec.</span><span class="sxs-lookup"><span data-stu-id="89514-357">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="89514-358">Následující fragment kódu definuje kód, který vyvolává diagnostiku, a kód po použití opravy:</span><span class="sxs-lookup"><span data-stu-id="89514-358">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="89514-359">Nakonec, pokud je proměnná deklarována s `var` klíčovým slovem, oprava kódu nesprávné věci a vygeneruje `const var` deklaraci, která není podporována jazykem C#.</span><span class="sxs-lookup"><span data-stu-id="89514-359">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="89514-360">Chcete-li opravit tuto chybu, oprava kódu musí nahradit `var` klíčové slovo názvem odvozeného typu:</span><span class="sxs-lookup"><span data-stu-id="89514-360">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="89514-361">Tyto změny aktualizují deklarace datových řádků pro oba testy.</span><span class="sxs-lookup"><span data-stu-id="89514-361">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="89514-362">Následující kód ukazuje tyto testy se všemi atributy datových řádků:</span><span class="sxs-lookup"><span data-stu-id="89514-362">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="89514-363">Naštěstí můžete všechny výše uvedené chyby vyřešit pomocí stejných technik, které jste právě naučili.</span><span class="sxs-lookup"><span data-stu-id="89514-363">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="89514-364">Chcete-li opravit první chybu, nejprve otevřete **DiagnosticAnalyzer.cs** a vyhledejte smyčku foreach, kde jsou zkontrolovány jednotlivé Inicializátory místní deklarace, aby bylo zajištěno, že jsou přiřazeny pomocí konstantních hodnot.</span><span class="sxs-lookup"><span data-stu-id="89514-364">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="89514-365">Bezprostředně _před_ první smyčkou foreach volejte, `context.SemanticModel.GetTypeInfo()` aby načetla podrobné informace o deklarovaném typu místní deklarace:</span><span class="sxs-lookup"><span data-stu-id="89514-365">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="89514-366">Potom v rámci `foreach` smyčky zkontrolujte každý inicializátor a ujistěte se, že je převoditelné na typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="89514-366">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="89514-367">Po ověření, že inicializátor je konstanta, přidejte následující kontrolu:</span><span class="sxs-lookup"><span data-stu-id="89514-367">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="89514-368">Další změny se vytvoří po poslední.</span><span class="sxs-lookup"><span data-stu-id="89514-368">The next change builds upon the last one.</span></span> <span data-ttu-id="89514-369">Před pravou složenou závorkou první smyčky foreach přidejte následující kód pro zkontrolování typu místní deklarace, je-li konstanta řetězec nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="89514-369">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

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

<span data-ttu-id="89514-370">Chcete-li nahradit klíčové slovo var správným názvem typu, je nutné ve svém poskytovateli opravy kódu napsat trochu větší kód.</span><span class="sxs-lookup"><span data-stu-id="89514-370">You must write a bit more code in your code fix provider to replace the var' keyword with the correct type name.</span></span> <span data-ttu-id="89514-371">Vraťte se na **CodeFixProvider.cs**.</span><span class="sxs-lookup"><span data-stu-id="89514-371">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="89514-372">Kód, který přidáte, provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="89514-372">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="89514-373">Ověřte, zda je deklarace deklarace `var` , a pokud je:</span><span class="sxs-lookup"><span data-stu-id="89514-373">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="89514-374">Vytvoří nový typ pro odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="89514-374">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="89514-375">Ujistěte se, že deklarace typu není alias.</span><span class="sxs-lookup"><span data-stu-id="89514-375">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="89514-376">V takovém případě je právní deklarace platná `const var` .</span><span class="sxs-lookup"><span data-stu-id="89514-376">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="89514-377">Ujistěte se, že `var` v tomto programu není název typu.</span><span class="sxs-lookup"><span data-stu-id="89514-377">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="89514-378">(Pokud ano, `const var` je právní).</span><span class="sxs-lookup"><span data-stu-id="89514-378">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="89514-379">Zjednodušit úplný název typu</span><span class="sxs-lookup"><span data-stu-id="89514-379">Simplify the full type name</span></span>

<span data-ttu-id="89514-380">Tyto zvuky jako velké množství kódu.</span><span class="sxs-lookup"><span data-stu-id="89514-380">That sounds like a lot of code.</span></span> <span data-ttu-id="89514-381">Není to.</span><span class="sxs-lookup"><span data-stu-id="89514-381">It's not.</span></span> <span data-ttu-id="89514-382">Nahraďte řádek, který deklaruje a inicializuje, `newLocal` pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="89514-382">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="89514-383">Hned po inicializaci `newModifiers` :</span><span class="sxs-lookup"><span data-stu-id="89514-383">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="89514-384">`using`K použití tohoto typu budete muset přidat jednu direktivu <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> :</span><span class="sxs-lookup"><span data-stu-id="89514-384">You'll need to add one `using` directive to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="89514-385">Spusťte testy a všechny by měly být passované.</span><span class="sxs-lookup"><span data-stu-id="89514-385">Run your tests, and they should all pass.</span></span> <span data-ttu-id="89514-386">Congratulate se tak, že spustíte kompletní analyzátor.</span><span class="sxs-lookup"><span data-stu-id="89514-386">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="89514-387">Stisknutím <kbd>kombinace kláves CTRL + F5</kbd> spusťte projekt analyzátoru v druhé instanci sady Visual Studio s načteným rozšířením Roslyn Preview.</span><span class="sxs-lookup"><span data-stu-id="89514-387">Press <kbd>Ctrl+F5</kbd> to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="89514-388">Ve druhé instanci sady Visual Studio vytvořte nový projekt konzolové aplikace v jazyce C# a přidejte `int x = "abc";` ho do metody Main.</span><span class="sxs-lookup"><span data-stu-id="89514-388">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="89514-389">Děkujeme, že při první opravě chyby by se pro tuto místní proměnnou proměnné nemělo hlásit žádné upozornění (i když dojde k chybě kompilátoru, jak se očekávalo).</span><span class="sxs-lookup"><span data-stu-id="89514-389">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="89514-390">Dále přidejte `object s = "abc";` do metody Main.</span><span class="sxs-lookup"><span data-stu-id="89514-390">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="89514-391">Z důvodu druhé opravy chyby by se nemělo hlásit žádné upozornění.</span><span class="sxs-lookup"><span data-stu-id="89514-391">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="89514-392">Nakonec přidejte další místní proměnnou, která používá `var` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="89514-392">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="89514-393">Uvidíte, že se nahlásí upozornění a na levé straně se zobrazí návrh.</span><span class="sxs-lookup"><span data-stu-id="89514-393">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="89514-394">Přesuňte kurzor editoru na podtržení vlnovkou a stiskněte <kbd>kombinaci kláves CTRL +</kbd>.</span><span class="sxs-lookup"><span data-stu-id="89514-394">Move the editor caret over the squiggly underline and press <kbd>Ctrl+</kbd>.</span></span> <span data-ttu-id="89514-395">pro zobrazení navrhované opravy kódu.</span><span class="sxs-lookup"><span data-stu-id="89514-395">to display the suggested code fix.</span></span> <span data-ttu-id="89514-396">Po výběru opravy kódu si všimněte, že klíčové slovo var se nyní zpracovává správně.</span><span class="sxs-lookup"><span data-stu-id="89514-396">Upon selecting your code fix, note that the var' keyword is now handled correctly.</span></span>

<span data-ttu-id="89514-397">Nakonec přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="89514-397">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="89514-398">Po těchto změnách získáte červené vlnovky pouze první dvě proměnné.</span><span class="sxs-lookup"><span data-stu-id="89514-398">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="89514-399">Přidejte `const` do obou a a zobrazí se `i` `j` nové upozornění, protože se `k` teď může jednat o `const` .</span><span class="sxs-lookup"><span data-stu-id="89514-399">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="89514-400">Gratulujeme!</span><span class="sxs-lookup"><span data-stu-id="89514-400">Congratulations!</span></span> <span data-ttu-id="89514-401">Vytvořili jste první rozšíření .NET Compiler Platform, které provádí průběžnou analýzu kódu k detekci problému a nabízí rychlou opravu pro její opravu.</span><span class="sxs-lookup"><span data-stu-id="89514-401">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="89514-402">Na cestě jste se naučili mnoho rozhraní API kódu, která jsou součástí sady .NET Compiler Platform SDK (rozhraní API Roslyn).</span><span class="sxs-lookup"><span data-stu-id="89514-402">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="89514-403">Práci s [dokončenou ukázkou](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) najdete v našem úložišti GitHub Samples.</span><span class="sxs-lookup"><span data-stu-id="89514-403">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="89514-404">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="89514-404">Other resources</span></span>

- [<span data-ttu-id="89514-405">Začínáme s analýzou syntaxe</span><span class="sxs-lookup"><span data-stu-id="89514-405">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="89514-406">Začínáme se sémantickou analýzou</span><span class="sxs-lookup"><span data-stu-id="89514-406">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)

---
title: 'Kurz: Napište svůj první analyzátor a opravu kódu'
description: Tento kurz obsahuje podrobné pokyny k sestavení analyzátoru a opravy kódu pomocí sady SDK .NET Compiler SDK (Roslyn API).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: f6fc21c010f9b5fcd5e709ef822639c020a7c93b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240547"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="bd963-103">Kurz: Napište svůj první analyzátor a opravu kódu</span><span class="sxs-lookup"><span data-stu-id="bd963-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="bd963-104">Sada SDK platformy kompilátoru .NET poskytuje nástroje, které potřebujete k vytvoření vlastních upozornění, která cílí na kód jazyka C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bd963-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="bd963-105">**Analyzátor** obsahuje kód, který rozpozná porušení pravidla.</span><span class="sxs-lookup"><span data-stu-id="bd963-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="bd963-106">**Oprava kódu** obsahuje kód, který opravuje porušení.</span><span class="sxs-lookup"><span data-stu-id="bd963-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="bd963-107">Pravidla, která implementujete může být cokoli od struktury kódu na styl kódování na konvence pojmenování a další.</span><span class="sxs-lookup"><span data-stu-id="bd963-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="bd963-108">Platforma kompilátoru .NET poskytuje rámec pro spuštění analýzy, protože vývojáři píší kód a všechny funkce rozhraní Visual Studio pro opravu kódu: zobrazení vlnovek v editoru, vyplnění seznamu chyb sady Visual Studio, vytvoření "žárovky" návrhy a zobrazení bohaté náhledu navrhovaných oprav.</span><span class="sxs-lookup"><span data-stu-id="bd963-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="bd963-109">V tomto kurzu se budete zabývat **vytvořeníanalyzátoru** a doprovodný **kód opravit** pomocí Roslyn API.</span><span class="sxs-lookup"><span data-stu-id="bd963-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="bd963-110">Analyzátor je způsob, jak provést analýzu zdrojového kódu a nahlásit problém uživateli.</span><span class="sxs-lookup"><span data-stu-id="bd963-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="bd963-111">Volitelně může analyzátor také poskytnout opravu kódu, která představuje změnu zdrojového kódu uživatele.</span><span class="sxs-lookup"><span data-stu-id="bd963-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="bd963-112">Tento kurz vytvoří analyzátor, který vyhledá deklarace místní `const` proměnné, které by mohly být deklarovány pomocí modifikátoru, ale nejsou.</span><span class="sxs-lookup"><span data-stu-id="bd963-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="bd963-113">Doprovodný kód opravit upravuje tyto deklarace přidat `const` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="bd963-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd963-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd963-114">Prerequisites</span></span>

- [<span data-ttu-id="bd963-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="bd963-115">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [<span data-ttu-id="bd963-116">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="bd963-116">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="bd963-117">Budete muset nainstalovat **sdk platformy kompilátoru .NET** prostřednictvím Instalačního programu sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="bd963-117">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="bd963-118">Existuje několik kroků k vytvoření a ověření analyzátoru:</span><span class="sxs-lookup"><span data-stu-id="bd963-118">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="bd963-119">Vytvořte řešení.</span><span class="sxs-lookup"><span data-stu-id="bd963-119">Create the solution.</span></span>
1. <span data-ttu-id="bd963-120">Zaregistrujte název a popis analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="bd963-120">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="bd963-121">Nahlásit upozornění a doporučení analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="bd963-121">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="bd963-122">Implementujte opravu kódu přijímat doporučení.</span><span class="sxs-lookup"><span data-stu-id="bd963-122">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="bd963-123">Zlepšete analýzu pomocí jednotkových testů.</span><span class="sxs-lookup"><span data-stu-id="bd963-123">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="bd963-124">Prozkoumejte šablonu analyzátoru</span><span class="sxs-lookup"><span data-stu-id="bd963-124">Explore the analyzer template</span></span>

<span data-ttu-id="bd963-125">Analyzátor hlásí uživateli všechny deklarace místní proměnné, které lze převést na místní konstanty.</span><span class="sxs-lookup"><span data-stu-id="bd963-125">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="bd963-126">Zvažte například následující kód:</span><span class="sxs-lookup"><span data-stu-id="bd963-126">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="bd963-127">Ve výše uvedeném kódu `x` je přiřazena konstantní hodnota a nikdy se nemění.</span><span class="sxs-lookup"><span data-stu-id="bd963-127">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="bd963-128">To může být `const` deklarována pomocí modifikátoru:</span><span class="sxs-lookup"><span data-stu-id="bd963-128">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="bd963-129">Analýza k určení, zda proměnná může být konstanta je zapojen, vyžadující syntaktické analýzy, konstantní analýzy výrazu inicializátoru a analýzy toku dat zajistit, že proměnná je nikdy zapsána do.</span><span class="sxs-lookup"><span data-stu-id="bd963-129">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="bd963-130">Platforma kompilátoru .NET poskytuje rozhraní API, která usnadňují provádění této analýzy.</span><span class="sxs-lookup"><span data-stu-id="bd963-130">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="bd963-131">Prvním krokem je vytvoření nového **c# analyzátoru s projektem opravy kódu.**</span><span class="sxs-lookup"><span data-stu-id="bd963-131">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

- <span data-ttu-id="bd963-132">V sadě Visual Studio zvolte **Soubor > Nový > project...** a zobrazte dialogové okno Nový projekt.</span><span class="sxs-lookup"><span data-stu-id="bd963-132">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="bd963-133">V **části Visual C# > Rozšiřitelnost**zvolte **Analyzer with code fix (.NET Standard).**</span><span class="sxs-lookup"><span data-stu-id="bd963-133">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="bd963-134">Pojmenujte projekt**MakeConst**a klepněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="bd963-134">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="bd963-135">Analyzátor se šablonou oprava kódu vytvoří tři projekty: jeden obsahuje analyzátor a opravu kódu, druhý je projekt testování částí a třetí je projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="bd963-135">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="bd963-136">Výchozí projekt spuštění je projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="bd963-136">The default startup project is the VSIX project.</span></span> <span data-ttu-id="bd963-137">Stisknutím **klávesy F5** spusťte projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="bd963-137">Press **F5** to start the VSIX project.</span></span> <span data-ttu-id="bd963-138">Tím se spustí druhá instance sady Visual Studio, která načetla nový analyzátor.</span><span class="sxs-lookup"><span data-stu-id="bd963-138">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="bd963-139">Při spuštění analyzátoru spustíte druhou kopii sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd963-139">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="bd963-140">Tato druhá kopie používá k ukládání nastavení jiný podregistr registru.</span><span class="sxs-lookup"><span data-stu-id="bd963-140">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="bd963-141">To umožňuje odlišit vizuální nastavení ve dvou kopiích sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd963-141">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="bd963-142">Můžete vybrat jiný motiv pro experimentální spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd963-142">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="bd963-143">Kromě toho nepřecházejte nastavení nebo se přihlašujte k účtu sady Visual Studio pomocí experimentálního spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd963-143">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="bd963-144">To udržuje nastavení odlišné.</span><span class="sxs-lookup"><span data-stu-id="bd963-144">That keeps the settings different.</span></span>

<span data-ttu-id="bd963-145">V druhé instanci sady Visual Studio, kterou jste právě spustili, vytvořte nový projekt aplikace konzoly Jazyka C# (projekt .NET Core nebo .NET Framework bude fungovat -- analyzátory pracují na zdrojové úrovni.) Najeďte nad token s podtržením vlnovkou a zobrazí se varovný text poskytnutý analyzátorem.</span><span class="sxs-lookup"><span data-stu-id="bd963-145">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="bd963-146">Šablona vytvoří analyzátor, který hlásí upozornění na každé deklaraci typu, kde název typu obsahuje malá písmena, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="bd963-146">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Upozornění pro hlášení analyzátoru](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="bd963-148">Šablona také poskytuje opravu kódu, která změní libovolný název typu obsahující malá písmena na všechna velká písmena.</span><span class="sxs-lookup"><span data-stu-id="bd963-148">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="bd963-149">Můžete kliknout na žárovku zobrazenou s upozorněním, abyste viděli navrhované změny.</span><span class="sxs-lookup"><span data-stu-id="bd963-149">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="bd963-150">Přijetí navrhovaných změn aktualizuje název typu a všechny odkazy na tento typ v řešení.</span><span class="sxs-lookup"><span data-stu-id="bd963-150">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="bd963-151">Teď, když jste viděli počáteční analyzátor v akci, zavřete druhou instanci Sady Visual Studio a vraťte se do projektu analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="bd963-151">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="bd963-152">Není třeba spustit druhou kopii sady Visual Studio a vytvořit nový kód pro testování každé změny v analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="bd963-152">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="bd963-153">Šablona také vytvoří projekt testování částí pro vás.</span><span class="sxs-lookup"><span data-stu-id="bd963-153">The template also creates a unit test project for you.</span></span> <span data-ttu-id="bd963-154">Tento projekt obsahuje dva testy.</span><span class="sxs-lookup"><span data-stu-id="bd963-154">That project contains two tests.</span></span> <span data-ttu-id="bd963-155">`TestMethod1`zobrazuje typický formát testu, který analyzuje kód bez spuštění diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="bd963-155">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="bd963-156">`TestMethod2`zobrazuje formát testu, který spouští diagnostiku, a potom použije navrhovanou opravu kódu.</span><span class="sxs-lookup"><span data-stu-id="bd963-156">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="bd963-157">Při vytváření analyzátoru a opravy kódu napíšete testy pro různé struktury kódu, abyste ověřili svou práci.</span><span class="sxs-lookup"><span data-stu-id="bd963-157">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="bd963-158">Testy částí pro analyzátory jsou mnohem rychlejší než jejich interaktivní testování pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd963-158">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="bd963-159">Testy částí analyzátoru jsou skvělý nástroj, když víte, jaké konstrukce kódu by měly a neměly aktivovat analyzátor.</span><span class="sxs-lookup"><span data-stu-id="bd963-159">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="bd963-160">Načítání analyzátoru v jiné kopii sady Visual Studio je skvělý nástroj k prozkoumání a hledání konstrukcí, o kterých jste možná ještě nepřemýšleli.</span><span class="sxs-lookup"><span data-stu-id="bd963-160">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="bd963-161">Vytvořit registrace analyzátoru</span><span class="sxs-lookup"><span data-stu-id="bd963-161">Create analyzer registrations</span></span>

<span data-ttu-id="bd963-162">Šablona vytvoří `DiagnosticAnalyzer` počáteční třídu v **souboru MakeConstAnalyzer.cs.**</span><span class="sxs-lookup"><span data-stu-id="bd963-162">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="bd963-163">Tento počáteční analyzátor zobrazuje dvě důležité vlastnosti každého analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="bd963-163">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="bd963-164">Každý diagnostický analyzátor `[DiagnosticAnalyzer]` musí poskytnout atribut, který popisuje jazyk, ve kterém pracuje.</span><span class="sxs-lookup"><span data-stu-id="bd963-164">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="bd963-165">Každý diagnostický analyzátor musí <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> být odvozen ze třídy.</span><span class="sxs-lookup"><span data-stu-id="bd963-165">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="bd963-166">Šablona také zobrazuje základní funkce, které jsou součástí každého analyzátoru:</span><span class="sxs-lookup"><span data-stu-id="bd963-166">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="bd963-167">Zaregistrujte akce.</span><span class="sxs-lookup"><span data-stu-id="bd963-167">Register actions.</span></span> <span data-ttu-id="bd963-168">Akce představují změny kódu, které by měly aktivovat analyzátor prozkoumat kód pro porušení.</span><span class="sxs-lookup"><span data-stu-id="bd963-168">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="bd963-169">Když Visual Studio zjistí úpravy kódu, které odpovídají registrované akce, volá registrovaný metodu analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="bd963-169">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="bd963-170">Vytvořte diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="bd963-170">Create diagnostics.</span></span> <span data-ttu-id="bd963-171">Když analyzátor zjistí porušení, vytvoří diagnostický objekt, který Visual Studio používá k upozornění uživatele porušení.</span><span class="sxs-lookup"><span data-stu-id="bd963-171">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="bd963-172">Akce se zaregistruje v <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> přepsání metody.</span><span class="sxs-lookup"><span data-stu-id="bd963-172">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bd963-173">V tomto kurzu navštívíte **syntaktické uzly, které** hledají místní deklarace, a zjistíte, které z nich mají konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bd963-173">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="bd963-174">Pokud deklarace může být konstantní, analyzátor vytvoří a ohlásí diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="bd963-174">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="bd963-175">Prvním krokem je aktualizace registračníkonstanty `Initialize` a metody tak, aby tyto konstanty označují váš analyzátor "Make Const".</span><span class="sxs-lookup"><span data-stu-id="bd963-175">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="bd963-176">Většina konstant řetězce je definována v souboru prostředků řetězce.</span><span class="sxs-lookup"><span data-stu-id="bd963-176">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="bd963-177">Měli byste dodržovat tuto praxi pro snadnější lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="bd963-177">You should follow that practice for easier localization.</span></span> <span data-ttu-id="bd963-178">Otevřete soubor **Resources.resx** pro projekt analyzátoru **MakeConst.**</span><span class="sxs-lookup"><span data-stu-id="bd963-178">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="bd963-179">Zobrazí se editor prostředků.</span><span class="sxs-lookup"><span data-stu-id="bd963-179">This displays the resource editor.</span></span> <span data-ttu-id="bd963-180">Aktualizujte prostředky řetězce takto:</span><span class="sxs-lookup"><span data-stu-id="bd963-180">Update the string resources as follows:</span></span>

- <span data-ttu-id="bd963-181">Změna `AnalyzerTitle` na "Proměnná může být konstantní".</span><span class="sxs-lookup"><span data-stu-id="bd963-181">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
- <span data-ttu-id="bd963-182">Změna `AnalyzerMessageFormat` na "Může být konstantní".</span><span class="sxs-lookup"><span data-stu-id="bd963-182">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
- <span data-ttu-id="bd963-183">Změňte `AnalyzerDescription` na "Vytvořit konstantu".</span><span class="sxs-lookup"><span data-stu-id="bd963-183">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="bd963-184">Změňte také rozevírací soubor `public` **Modifikátor přístupu** na .</span><span class="sxs-lookup"><span data-stu-id="bd963-184">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="bd963-185">To usnadňuje použití těchto konstant v jednotkových testech.</span><span class="sxs-lookup"><span data-stu-id="bd963-185">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="bd963-186">Po dokončení by měl editor prostředků zobrazit následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="bd963-186">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Aktualizovat prostředky řetězce](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="bd963-188">Zbývající změny jsou v souboru analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="bd963-188">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="bd963-189">Otevřete **MakeConstAnalyzer.cs** v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd963-189">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="bd963-190">Změňte registrovanou akci z akce, která působí na symboly, na akci, která funguje na syntaxi.</span><span class="sxs-lookup"><span data-stu-id="bd963-190">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="bd963-191">V `MakeConstAnalyzerAnalyzer.Initialize` metodě najděte řádek, který registruje akci na symboly:</span><span class="sxs-lookup"><span data-stu-id="bd963-191">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="bd963-192">Nahraďte jej následujícím řádkem:</span><span class="sxs-lookup"><span data-stu-id="bd963-192">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="bd963-193">Po této změně můžete `AnalyzeSymbol` odstranit metodu.</span><span class="sxs-lookup"><span data-stu-id="bd963-193">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="bd963-194">Tento analyzátor <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>zkoumá <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> , nikoli příkazy.</span><span class="sxs-lookup"><span data-stu-id="bd963-194">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="bd963-195">Všimněte `AnalyzeNode` si, že má červené klikyháky pod ním.</span><span class="sxs-lookup"><span data-stu-id="bd963-195">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="bd963-196">Kód, který jste právě `AnalyzeNode` přidali odkazuje na metodu, která nebyla deklarována.</span><span class="sxs-lookup"><span data-stu-id="bd963-196">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="bd963-197">Deklarujte tuto metodu pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="bd963-197">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="bd963-198">Změňte `Category` na "Využití" v **MakeConstAnalyzer.cs** jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="bd963-198">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="bd963-199">Najít místní prohlášení, která by mohla být const</span><span class="sxs-lookup"><span data-stu-id="bd963-199">Find local declarations that could be const</span></span>

<span data-ttu-id="bd963-200">Je čas napsat první verzi `AnalyzeNode` metody.</span><span class="sxs-lookup"><span data-stu-id="bd963-200">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="bd963-201">Měl by hledat jednu místní `const` deklaraci, která by mohla být, ale není, jako následující kód:</span><span class="sxs-lookup"><span data-stu-id="bd963-201">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="bd963-202">Prvním krokem je najít místní prohlášení.</span><span class="sxs-lookup"><span data-stu-id="bd963-202">The first step is to find local declarations.</span></span> <span data-ttu-id="bd963-203">Do `AnalyzeNode` **MakeConstAnalyzer.cs**přidejte následující kód :</span><span class="sxs-lookup"><span data-stu-id="bd963-203">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="bd963-204">Toto přetypované vždy úspěšné, protože analyzátor registrovány pro změny místní deklarace a pouze místní deklarace.</span><span class="sxs-lookup"><span data-stu-id="bd963-204">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="bd963-205">Žádný jiný typ uzlu nespustí `AnalyzeNode` volání vaší metody.</span><span class="sxs-lookup"><span data-stu-id="bd963-205">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="bd963-206">Dále zkontrolujte deklaraci `const` pro všechny modifikátory.</span><span class="sxs-lookup"><span data-stu-id="bd963-206">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="bd963-207">Pokud je najdete, okamžitě se vraťte.</span><span class="sxs-lookup"><span data-stu-id="bd963-207">If you find them, return immediately.</span></span> <span data-ttu-id="bd963-208">Následující kód hledá `const` všechny modifikátory v místní deklaraci:</span><span class="sxs-lookup"><span data-stu-id="bd963-208">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="bd963-209">Nakonec je třeba zkontrolovat, zda `const`proměnná může být .</span><span class="sxs-lookup"><span data-stu-id="bd963-209">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="bd963-210">To znamená, že po inicializace není nikdy přiřazen.</span><span class="sxs-lookup"><span data-stu-id="bd963-210">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="bd963-211">Provedete sémantickou analýzu <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>pomocí .</span><span class="sxs-lookup"><span data-stu-id="bd963-211">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="bd963-212">Pomocí argumentu `context` můžete určit, zda lze `const`provést deklaraci místní proměnné .</span><span class="sxs-lookup"><span data-stu-id="bd963-212">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="bd963-213">Představuje <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> všechny sémantické informace v jednom zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="bd963-213">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents of all semantic information in a single source file.</span></span> <span data-ttu-id="bd963-214">Další informace naleznete v článku, který pokrývá [sémantické modely](../work-with-semantics.md).</span><span class="sxs-lookup"><span data-stu-id="bd963-214">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="bd963-215">Budete používat k <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> provedení analýzy toku dat na příkaz místní deklarace.</span><span class="sxs-lookup"><span data-stu-id="bd963-215">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="bd963-216">Potom použijete výsledky této analýzy toku dat k zajištění, že místní proměnná není zapsána s novou hodnotou nikde jinde.</span><span class="sxs-lookup"><span data-stu-id="bd963-216">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="bd963-217">Volání <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> metody rozšíření načíst <xref:Microsoft.CodeAnalysis.ILocalSymbol> pro proměnnou a zkontrolujte, zda <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> není obsažena s kolekcí analýzy toku dat.</span><span class="sxs-lookup"><span data-stu-id="bd963-217">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="bd963-218">Na konec `AnalyzeNode` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="bd963-218">Add the following code to the end of the `AnalyzeNode` method:</span></span>

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

<span data-ttu-id="bd963-219">Právě přidaný kód zajišťuje, že proměnná není změněna, a proto může být provedena `const`.</span><span class="sxs-lookup"><span data-stu-id="bd963-219">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="bd963-220">Je čas zvýšit diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="bd963-220">It's time to raise the diagnostic.</span></span> <span data-ttu-id="bd963-221">Přidejte následující kód jako `AnalyzeNode`poslední řádek v :</span><span class="sxs-lookup"><span data-stu-id="bd963-221">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="bd963-222">Průběh můžete zkontrolovat stisknutím **klávesy F5** a spusťte analyzátor.</span><span class="sxs-lookup"><span data-stu-id="bd963-222">You can check your progress by pressing **F5** to run your analyzer.</span></span> <span data-ttu-id="bd963-223">Můžete načíst konzolovou aplikaci, kterou jste vytvořili dříve, a pak přidat následující testovací kód:</span><span class="sxs-lookup"><span data-stu-id="bd963-223">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="bd963-224">Měla by se zobrazit žárovka a analyzátor by měl hlásit diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="bd963-224">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="bd963-225">Žárovka však stále používá šablonu generovaný kód opravit a řekne vám, že může být velká písmena.</span><span class="sxs-lookup"><span data-stu-id="bd963-225">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="bd963-226">V další části je vysvětleno, jak napsat opravu kódu.</span><span class="sxs-lookup"><span data-stu-id="bd963-226">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="bd963-227">Napsat opravu kódu</span><span class="sxs-lookup"><span data-stu-id="bd963-227">Write the code fix</span></span>

<span data-ttu-id="bd963-228">Analyzátor může poskytnout jednu nebo více oprav kódu.</span><span class="sxs-lookup"><span data-stu-id="bd963-228">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="bd963-229">Oprava kódu definuje úpravu, která řeší nahlášený problém.</span><span class="sxs-lookup"><span data-stu-id="bd963-229">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="bd963-230">Pro analyzátor, který jste vytvořili, můžete poskytnout opravu kódu, která vloží klíčové slovo const:</span><span class="sxs-lookup"><span data-stu-id="bd963-230">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="bd963-231">Uživatel si jej vybere z uživatelského rozhraní žárovky v editoru a Visual Studio změní kód.</span><span class="sxs-lookup"><span data-stu-id="bd963-231">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="bd963-232">Otevřete **soubor MakeConstCodeFixProvider.cs** přidaný šablonou.</span><span class="sxs-lookup"><span data-stu-id="bd963-232">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="bd963-233">Tato oprava kódu je již připojena k ID diagnostiky vytvořeného diagnostickým analyzátorem, ale ještě neimplementuje správnou transformaci kódu.</span><span class="sxs-lookup"><span data-stu-id="bd963-233">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="bd963-234">Nejprve byste měli odstranit některé kód šablony.</span><span class="sxs-lookup"><span data-stu-id="bd963-234">First you should remove some of the template code.</span></span> <span data-ttu-id="bd963-235">Změňte řetězec nadpisu na "Vytvořit konstantu":</span><span class="sxs-lookup"><span data-stu-id="bd963-235">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="bd963-236">Dále odstraňte `MakeUppercaseAsync` metodu.</span><span class="sxs-lookup"><span data-stu-id="bd963-236">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="bd963-237">Už to neplatí.</span><span class="sxs-lookup"><span data-stu-id="bd963-237">It no longer applies.</span></span>

<span data-ttu-id="bd963-238">Všichni zprostředkovatelé opravy <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>kódu jsou odvozeni z .</span><span class="sxs-lookup"><span data-stu-id="bd963-238">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="bd963-239">Všechny přepsat <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> nahlásit dostupné opravy kódu.</span><span class="sxs-lookup"><span data-stu-id="bd963-239">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="bd963-240">V `RegisterCodeFixesAsync`aplikace změňte hledaný typ předchůdce na <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> typ uzlu tak, aby odpovídal diagnostice:</span><span class="sxs-lookup"><span data-stu-id="bd963-240">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="bd963-241">Dále změňte poslední řádek a zaregistrujte opravu kódu.</span><span class="sxs-lookup"><span data-stu-id="bd963-241">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="bd963-242">Oprava vytvoří nový dokument, který je `const` výsledkem přidání modifikátoru do existující deklarace:</span><span class="sxs-lookup"><span data-stu-id="bd963-242">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="bd963-243">V kódu, který jste právě přidali na symbol `MakeConstAsync`, si všimnete červených vlnovek .</span><span class="sxs-lookup"><span data-stu-id="bd963-243">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="bd963-244">Přidejte deklaraci pro `MakeConstAsync` následující kód:</span><span class="sxs-lookup"><span data-stu-id="bd963-244">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="bd963-245">Nová `MakeConstAsync` metoda transformuje <xref:Microsoft.CodeAnalysis.Document> představující zdrojový soubor uživatele na <xref:Microsoft.CodeAnalysis.Document> nový, `const` který nyní obsahuje deklaraci.</span><span class="sxs-lookup"><span data-stu-id="bd963-245">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="bd963-246">Vytvoříte nový `const` token klíčového slova vložit na přední straně prohlášení prohlášení.</span><span class="sxs-lookup"><span data-stu-id="bd963-246">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="bd963-247">Buďte opatrní nejprve odebrat všechny vedoucí trivia z prvnítoken `const` prohlášení prohlášení a připojit jej k tokenu.</span><span class="sxs-lookup"><span data-stu-id="bd963-247">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="bd963-248">Do metody `MakeConstAsync` přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="bd963-248">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="bd963-249">Dále přidejte `const` token do deklarace pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="bd963-249">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="bd963-250">Dále naformátujte novou deklaraci tak, aby odpovídala pravidlům formátování jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="bd963-250">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="bd963-251">Formátování změn tak, aby odpovídaly existujícímu kódu, vytvoří lepší prostředí.</span><span class="sxs-lookup"><span data-stu-id="bd963-251">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="bd963-252">Přidejte následující příkaz ihned za existující kód:</span><span class="sxs-lookup"><span data-stu-id="bd963-252">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="bd963-253">Pro tento kód je vyžadován nový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="bd963-253">A new namespace is required for this code.</span></span> <span data-ttu-id="bd963-254">Do horní `using` části souboru přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="bd963-254">Add the following `using` statement to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="bd963-255">Posledním krokem je, aby vaše úpravy.</span><span class="sxs-lookup"><span data-stu-id="bd963-255">The final step is to make your edit.</span></span> <span data-ttu-id="bd963-256">Tento proces má tři kroky:</span><span class="sxs-lookup"><span data-stu-id="bd963-256">There are three steps to this process:</span></span>

1. <span data-ttu-id="bd963-257">Získejte popisovač existujícího dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bd963-257">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="bd963-258">Vytvořte nový dokument nahrazením existující deklarace s novou deklarací.</span><span class="sxs-lookup"><span data-stu-id="bd963-258">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="bd963-259">Vraťte nový dokument.</span><span class="sxs-lookup"><span data-stu-id="bd963-259">Return the new document.</span></span>

<span data-ttu-id="bd963-260">Na konec `MakeConstAsync` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="bd963-260">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="bd963-261">Oprava kódu je připravena k vyzkoušení.</span><span class="sxs-lookup"><span data-stu-id="bd963-261">Your code fix is ready to try.</span></span>  <span data-ttu-id="bd963-262">Stisknutím klávesy F5 spusťte projekt analyzátoru v druhé instanci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd963-262">Press F5 to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="bd963-263">V druhé instanci Sady Visual Studio vytvořte nový projekt aplikace konzoly Jazyka C# a přidejte několik deklarací místních proměnných inicializovaných s konstantními hodnotami do metody Main.</span><span class="sxs-lookup"><span data-stu-id="bd963-263">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="bd963-264">Uvidíte, že jsou hlášeny jako varování, jak je uvedeno níže.</span><span class="sxs-lookup"><span data-stu-id="bd963-264">You'll see that they are reported as warnings as below.</span></span>

![Může const varování](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="bd963-266">Udělal jsi velký pokrok.</span><span class="sxs-lookup"><span data-stu-id="bd963-266">You've made a lot of progress.</span></span> <span data-ttu-id="bd963-267">Existují klikyháky pod prohlášení, které `const`mohou být provedeny .</span><span class="sxs-lookup"><span data-stu-id="bd963-267">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="bd963-268">Ale je tu ještě práce.</span><span class="sxs-lookup"><span data-stu-id="bd963-268">But there is still work to do.</span></span> <span data-ttu-id="bd963-269">Tato práce citlivý- `const` li tebe přidat `i`až `j` k `k`the declarations začíná na . then a finally .</span><span class="sxs-lookup"><span data-stu-id="bd963-269">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="bd963-270">Pokud však přidáte `const` modifikátor v jiném `k`pořadí, počínaje písmenem , analyzátor vytvoří chyby: `k` nelze `const`deklarovat , `i` pokud a `j` nejsou již `const`obě .</span><span class="sxs-lookup"><span data-stu-id="bd963-270">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="bd963-271">Musíte provést další analýzu, abyste zajistili, že zvládnete různé způsoby, jak mohou být proměnné deklarovány a inicializovány.</span><span class="sxs-lookup"><span data-stu-id="bd963-271">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="bd963-272">Sestavení testů řízených daty</span><span class="sxs-lookup"><span data-stu-id="bd963-272">Build data driven tests</span></span>

<span data-ttu-id="bd963-273">Analyzátor a kód opravit práci na jednoduchý případ jednoho prohlášení, které mohou být provedeny const.</span><span class="sxs-lookup"><span data-stu-id="bd963-273">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="bd963-274">Existuje mnoho možných prohlášení prohlášení, kde tato implementace dělá chyby.</span><span class="sxs-lookup"><span data-stu-id="bd963-274">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="bd963-275">Tyto případy vyřešíte pomocí knihovny testování částí napsané šablonou.</span><span class="sxs-lookup"><span data-stu-id="bd963-275">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="bd963-276">Je to mnohem rychlejší než opakované otevření druhé kopie sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd963-276">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="bd963-277">Otevřete soubor **MakeConstUnitTests.cs** v projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="bd963-277">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="bd963-278">Šablona vytvořila dva testy, které následují dva běžné vzory pro analyzátor a test jednotky oprava kódu.</span><span class="sxs-lookup"><span data-stu-id="bd963-278">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="bd963-279">`TestMethod1`zobrazí vzor pro test, který zajišťuje, že analyzátor nehlásí diagnostiku, když by neměl.</span><span class="sxs-lookup"><span data-stu-id="bd963-279">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="bd963-280">`TestMethod2`zobrazuje vzor pro nahlášení diagnostiky a spuštění opravy kódu.</span><span class="sxs-lookup"><span data-stu-id="bd963-280">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="bd963-281">Kód pro téměř každý test pro analyzátor následuje jeden z těchto dvou vzorů.</span><span class="sxs-lookup"><span data-stu-id="bd963-281">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="bd963-282">Pro první krok můžete přepracovat tyto testy jako testy řízené daty.</span><span class="sxs-lookup"><span data-stu-id="bd963-282">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="bd963-283">Potom bude snadné vytvořit nové testy přidáním nové řetězce konstanty představují různé testovací vstupy.</span><span class="sxs-lookup"><span data-stu-id="bd963-283">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="bd963-284">Z důvodu efektivity je prvním krokem refaktoring dvou testů do testů řízených daty.</span><span class="sxs-lookup"><span data-stu-id="bd963-284">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="bd963-285">Potom stačí definovat několik konstant řetězce pro každý nový test.</span><span class="sxs-lookup"><span data-stu-id="bd963-285">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="bd963-286">Při refaktoringu přejmenujte obě metody na lepší názvy.</span><span class="sxs-lookup"><span data-stu-id="bd963-286">While your refactoring, rename both methods to better names.</span></span> <span data-ttu-id="bd963-287">Nahraďte `TestMethod1` tímto testem, který zajistí, že nebude vyvolána žádná diagnostika:</span><span class="sxs-lookup"><span data-stu-id="bd963-287">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="bd963-288">Můžete vytvořit nový řádek dat pro tento test definováním libovolný fragment kódu, který by neměl způsobit diagnostiku aktivovat upozornění.</span><span class="sxs-lookup"><span data-stu-id="bd963-288">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="bd963-289">Toto `VerifyCSharpDiagnostic` přetížení průchodů, pokud neexistují žádné diagnostiky spuštěna pro fragment zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="bd963-289">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="bd963-290">Dále nahraďte `TestMethod2` tímto testem, který zajistí, že je vyvolána diagnostika a oprava kódu použitá pro fragment zdrojového kódu:</span><span class="sxs-lookup"><span data-stu-id="bd963-290">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

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

<span data-ttu-id="bd963-291">Předchozí kód také provedl několik změn v kódu, který vytváří očekávaný výsledek diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="bd963-291">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="bd963-292">Používá veřejné konstanty registrované `MakeConst` v analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="bd963-292">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="bd963-293">Kromě toho používá dvě konstanty řetězce pro vstup a pevný zdroj.</span><span class="sxs-lookup"><span data-stu-id="bd963-293">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="bd963-294">Do `UnitTest` třídy přidejte následující konstanty řetězce:</span><span class="sxs-lookup"><span data-stu-id="bd963-294">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="bd963-295">Spusťte tyto dva testy, abyste se ujistili, že projdou.</span><span class="sxs-lookup"><span data-stu-id="bd963-295">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="bd963-296">V sadě Visual Studio otevřete **Průzkumníka testů** výběrem **možnosti Testovat** > **Průzkumníka testů systému\*\*\*\*Windows** > .</span><span class="sxs-lookup"><span data-stu-id="bd963-296">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span>  <span data-ttu-id="bd963-297">Stisknutím tlačítka **Spustit vše** odkaz.</span><span class="sxs-lookup"><span data-stu-id="bd963-297">The press the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="bd963-298">Vytvořit testy pro platné deklarace</span><span class="sxs-lookup"><span data-stu-id="bd963-298">Create tests for valid declarations</span></span>

<span data-ttu-id="bd963-299">Obecně platí, že analyzátory by měly ukončit co nejrychleji a dělat minimální práci.</span><span class="sxs-lookup"><span data-stu-id="bd963-299">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="bd963-300">Visual Studio volá registrované analyzátory jako uživatel ueviduje kód.</span><span class="sxs-lookup"><span data-stu-id="bd963-300">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="bd963-301">Reakce je klíčovým požadavkem.</span><span class="sxs-lookup"><span data-stu-id="bd963-301">Responsiveness is a key requirement.</span></span> <span data-ttu-id="bd963-302">Existuje několik testovacích případů pro kód, který by neměl vyvolat diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="bd963-302">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="bd963-303">Analyzátor již zpracovává jeden z těchto testů, případ, kdy je proměnná přiřazena po inicializování.</span><span class="sxs-lookup"><span data-stu-id="bd963-303">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="bd963-304">Přidejte do testů následující řetězcovou konstantu, která představuje toto případ:</span><span class="sxs-lookup"><span data-stu-id="bd963-304">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="bd963-305">Potom přidejte datový řádek pro tento test, jak je znázorněno ve fragmentu níže:</span><span class="sxs-lookup"><span data-stu-id="bd963-305">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="bd963-306">Tento test projde také.</span><span class="sxs-lookup"><span data-stu-id="bd963-306">This test passes as well.</span></span> <span data-ttu-id="bd963-307">Dále přidejte konstanty pro podmínky, které jste ještě nezpracovali:</span><span class="sxs-lookup"><span data-stu-id="bd963-307">Next, add constants for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="bd963-308">Prohlášení, která `const`jsou již , protože jsou již const:</span><span class="sxs-lookup"><span data-stu-id="bd963-308">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="bd963-309">Deklarace, které nemají inicializátor, protože neexistuje žádná hodnota pro použití:</span><span class="sxs-lookup"><span data-stu-id="bd963-309">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="bd963-310">Deklarace, kde inicializátor není konstanta, protože nemohou být konstanty v době kompilace:</span><span class="sxs-lookup"><span data-stu-id="bd963-310">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="bd963-311">Může být ještě složitější, protože C# umožňuje více deklarací jako jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="bd963-311">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="bd963-312">Zvažte následující konstantu řetězce testovacího případu:</span><span class="sxs-lookup"><span data-stu-id="bd963-312">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="bd963-313">Proměnná `i` může být konstantní, `j` ale proměnná nemůže.</span><span class="sxs-lookup"><span data-stu-id="bd963-313">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="bd963-314">Proto toto prohlášení nelze provést const prohlášení.</span><span class="sxs-lookup"><span data-stu-id="bd963-314">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="bd963-315">Přidejte `DataRow` deklarace pro všechny tyto testy:</span><span class="sxs-lookup"><span data-stu-id="bd963-315">Add the `DataRow` declarations for all these tests:</span></span>

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

<span data-ttu-id="bd963-316">Spusťte testy znovu a uvidíte, že tyto nové testovací případy se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="bd963-316">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="bd963-317">Aktualizace analyzátoru ignorovat správné deklarace</span><span class="sxs-lookup"><span data-stu-id="bd963-317">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="bd963-318">Potřebujete některá vylepšení metody analyzátoru `AnalyzeNode` k odfiltrování kódu, který odpovídá těmto podmínkám.</span><span class="sxs-lookup"><span data-stu-id="bd963-318">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="bd963-319">Všechny jsou související podmínky, takže podobné změny opraví všechny tyto podmínky.</span><span class="sxs-lookup"><span data-stu-id="bd963-319">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="bd963-320">Proveďte následující `AnalyzeNode`změny :</span><span class="sxs-lookup"><span data-stu-id="bd963-320">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="bd963-321">Vaše sémantická analýza zkoumala jednu deklaraci proměnné.</span><span class="sxs-lookup"><span data-stu-id="bd963-321">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="bd963-322">Tento kód musí být `foreach` ve smyčce, která zkoumá všechny proměnné deklarované ve stejném příkazu.</span><span class="sxs-lookup"><span data-stu-id="bd963-322">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="bd963-323">Každá deklarovaná proměnná musí mít inicializátor.</span><span class="sxs-lookup"><span data-stu-id="bd963-323">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="bd963-324">Každá deklarovaná proměnná inicializátor musí být konstanta v čase kompilace.</span><span class="sxs-lookup"><span data-stu-id="bd963-324">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="bd963-325">Ve `AnalyzeNode` své metodě nahraďte původní sémantickou analýzu:</span><span class="sxs-lookup"><span data-stu-id="bd963-325">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

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

<span data-ttu-id="bd963-326">s následujícím fragmentem kódu:</span><span class="sxs-lookup"><span data-stu-id="bd963-326">with the following code snippet:</span></span>

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

<span data-ttu-id="bd963-327">První `foreach` smyčka zkoumá každou deklaraci proměnné pomocí syntaktické analýzy.</span><span class="sxs-lookup"><span data-stu-id="bd963-327">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="bd963-328">První kontrola zaručuje, že proměnná má inicializátor.</span><span class="sxs-lookup"><span data-stu-id="bd963-328">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="bd963-329">Druhá kontrola zaručuje, že inicializátor je konstanta.</span><span class="sxs-lookup"><span data-stu-id="bd963-329">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="bd963-330">Druhá smyčka má původní sémantickou analýzu.</span><span class="sxs-lookup"><span data-stu-id="bd963-330">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="bd963-331">Sémantické kontroly jsou v samostatné smyčce, protože má větší vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="bd963-331">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="bd963-332">Spusťte testy znovu, a měli byste vidět všechny projít.</span><span class="sxs-lookup"><span data-stu-id="bd963-332">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="bd963-333">Přidejte konečný lesk</span><span class="sxs-lookup"><span data-stu-id="bd963-333">Add the final polish</span></span>

<span data-ttu-id="bd963-334">Už jste téměř hotovi.</span><span class="sxs-lookup"><span data-stu-id="bd963-334">You're almost done.</span></span> <span data-ttu-id="bd963-335">Existuje několik dalších podmínek pro váš analyzátor zvládnout.</span><span class="sxs-lookup"><span data-stu-id="bd963-335">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="bd963-336">Visual Studio volá analyzátory, zatímco uživatel píše kód.</span><span class="sxs-lookup"><span data-stu-id="bd963-336">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="bd963-337">Často se stává, že váš analyzátor bude volán pro kód, který se nekompiluje.</span><span class="sxs-lookup"><span data-stu-id="bd963-337">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="bd963-338">Metoda diagnostického analyzátoru `AnalyzeNode` nekontroluje, zda je konstantní hodnota konvertibilní na typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="bd963-338">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="bd963-339">Takže aktuální implementace bude šťastně převést nesprávné deklarace, jako je int i = "abc"' na místní konstantu.</span><span class="sxs-lookup"><span data-stu-id="bd963-339">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="bd963-340">Přidejte konstantu zdrojového řetězce pro tuto podmínku:</span><span class="sxs-lookup"><span data-stu-id="bd963-340">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="bd963-341">Kromě toho nejsou správně zpracovány typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="bd963-341">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="bd963-342">Jedinou konstantní hodnotou povolenou `null`pro typ odkazu <xref:System.String?displayProperty=nameWithType>je , s výjimkou tohoto případu , který umožňuje řetězcové literály.</span><span class="sxs-lookup"><span data-stu-id="bd963-342">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="bd963-343">Jinými slovy, `const string s = "abc"` je `const object s = "abc"` legální, ale není.</span><span class="sxs-lookup"><span data-stu-id="bd963-343">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="bd963-344">Tento fragment kódu tuto podmínku ověří:</span><span class="sxs-lookup"><span data-stu-id="bd963-344">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="bd963-345">Chcete-li být důkladný, musíte přidat další test, abyste se ujistili, že můžete vytvořit konstantní deklaraci pro řetězec.</span><span class="sxs-lookup"><span data-stu-id="bd963-345">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="bd963-346">Následující úryvek definuje kód, který vyvolává diagnostiku, i kód po použití opravy:</span><span class="sxs-lookup"><span data-stu-id="bd963-346">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="bd963-347">Nakonec pokud je proměnná `var` deklarována pomocí klíčového slova, `const var` oprava kódu nesprávná věc a generuje deklaraci, která není podporována jazykem Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="bd963-347">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="bd963-348">Chcete-li tuto chybu opravit, `var` oprava kódu musí nahradit klíčové slovo s názvem odvozeného typu:</span><span class="sxs-lookup"><span data-stu-id="bd963-348">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="bd963-349">Tyto změny aktualizovat deklarace řádků dat pro oba testy.</span><span class="sxs-lookup"><span data-stu-id="bd963-349">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="bd963-350">Následující kód ukazuje tyto testy se všemi atributy řádku dat:</span><span class="sxs-lookup"><span data-stu-id="bd963-350">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="bd963-351">Naštěstí všechny výše uvedené chyby mohou být řešeny pomocí stejných technik, které jste se právě naučili.</span><span class="sxs-lookup"><span data-stu-id="bd963-351">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="bd963-352">Chcete-li opravit první chybu, **nejprve** otevřete DiagnosticAnalyzer.cs a vyhledejte foreach smyčky, kde jsou kontrolovány každý z inicializátory místní deklarace, aby bylo zajištěno, že jsou přiřazeny s konstantní mise.</span><span class="sxs-lookup"><span data-stu-id="bd963-352">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="bd963-353">Bezprostředně _před_ první foreach `context.SemanticModel.GetTypeInfo()` smyčky, volání načíst podrobné informace o deklarovaný typ místní deklarace:</span><span class="sxs-lookup"><span data-stu-id="bd963-353">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="bd963-354">Potom ve `foreach` smyčce zkontrolujte každý inicializátor, abyste se ujistili, že je konvertibilní na typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="bd963-354">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="bd963-355">Přidejte následující kontrolu po zajištění, že inicializátor je konstanta:</span><span class="sxs-lookup"><span data-stu-id="bd963-355">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="bd963-356">Další změna navazuje na poslední.</span><span class="sxs-lookup"><span data-stu-id="bd963-356">The next change builds upon the last one.</span></span> <span data-ttu-id="bd963-357">Před uzavírací složené závorky první smyčky foreach, přidejte následující kód pro kontrolu typu místní deklarace, pokud je konstanta řetězec nebo null.</span><span class="sxs-lookup"><span data-stu-id="bd963-357">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

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

<span data-ttu-id="bd963-358">Musíte napsat trochu více kódu ve vašem zprostředkovateli opravy kódu nahradit var ' klíčové slovo se správným názvem typu.</span><span class="sxs-lookup"><span data-stu-id="bd963-358">You must write a bit more code in your code fix provider to replace the var' keyword with the correct type name.</span></span> <span data-ttu-id="bd963-359">Vraťte se do **CodeFixProvider.cs**.</span><span class="sxs-lookup"><span data-stu-id="bd963-359">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="bd963-360">Kód, který přidáte, provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="bd963-360">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="bd963-361">Zkontrolujte, zda `var` je deklarace deklarace a zda je:</span><span class="sxs-lookup"><span data-stu-id="bd963-361">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="bd963-362">Vytvořte nový typ pro odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="bd963-362">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="bd963-363">Ujistěte se, že deklarace typu není alias.</span><span class="sxs-lookup"><span data-stu-id="bd963-363">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="bd963-364">Pokud ano, je legální `const var`prohlásit .</span><span class="sxs-lookup"><span data-stu-id="bd963-364">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="bd963-365">Ujistěte `var` se, že v tomto programu není název typu.</span><span class="sxs-lookup"><span data-stu-id="bd963-365">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="bd963-366">(Pokud ano, `const var` je legální).</span><span class="sxs-lookup"><span data-stu-id="bd963-366">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="bd963-367">Zjednodušení celého názvu typu</span><span class="sxs-lookup"><span data-stu-id="bd963-367">Simplify the full type name</span></span>

<span data-ttu-id="bd963-368">To zní jako hodně kódu.</span><span class="sxs-lookup"><span data-stu-id="bd963-368">That sounds like a lot of code.</span></span> <span data-ttu-id="bd963-369">Není.</span><span class="sxs-lookup"><span data-stu-id="bd963-369">It's not.</span></span> <span data-ttu-id="bd963-370">Nahraďte řádek, který deklaruje a inicializuje `newLocal` s následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="bd963-370">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="bd963-371">Jde bezprostředně po inicializaci `newModifiers`:</span><span class="sxs-lookup"><span data-stu-id="bd963-371">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="bd963-372">Chcete-li použít typ, `using` <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> budete muset přidat jeden příkaz:</span><span class="sxs-lookup"><span data-stu-id="bd963-372">You'll need to add one `using` statement to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="bd963-373">Spusťte testy a všechny by měly projít.</span><span class="sxs-lookup"><span data-stu-id="bd963-373">Run your tests, and they should all pass.</span></span> <span data-ttu-id="bd963-374">Pogratulujte si spuštěním hotového analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="bd963-374">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="bd963-375">Stisknutím kombinace kláves Ctrl+F5 spusťte projekt analyzátoru ve druhé instanci sady Visual Studio s načteným rozšířením Roslyn Preview.</span><span class="sxs-lookup"><span data-stu-id="bd963-375">Press Ctrl+F5 to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="bd963-376">V druhé instanci Sady Visual Studio vytvořte `int x = "abc";` nový projekt aplikace konzoly Jazyka C# a přidejte do metody Main.</span><span class="sxs-lookup"><span data-stu-id="bd963-376">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="bd963-377">Díky první opravě chyby by nemělo být hlášeno žádné upozornění pro tuto deklaraci místní proměnné (i když je chyba kompilátoru podle očekávání).</span><span class="sxs-lookup"><span data-stu-id="bd963-377">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="bd963-378">Dále přidejte `object s = "abc";` do hlavní metody.</span><span class="sxs-lookup"><span data-stu-id="bd963-378">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="bd963-379">Z důvodu druhé opravy chyby by měla být hlášena žádná upozornění.</span><span class="sxs-lookup"><span data-stu-id="bd963-379">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="bd963-380">Nakonec přidejte další místní `var` proměnnou, která používá klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="bd963-380">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="bd963-381">Uvidíte, že je hlášeno upozornění a vlevo se zobrazí návrh.</span><span class="sxs-lookup"><span data-stu-id="bd963-381">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="bd963-382">Přesuňte stříšku editoru přes vlnité podtržení a stiskněte kombinaci kláves Ctrl+.</span><span class="sxs-lookup"><span data-stu-id="bd963-382">Move the editor caret over the squiggly underline and press Ctrl+.</span></span> <span data-ttu-id="bd963-383">zobrazíte navrhovanou opravu kódu.</span><span class="sxs-lookup"><span data-stu-id="bd963-383">to display the suggested code fix.</span></span> <span data-ttu-id="bd963-384">Po výběru opravy kódu si všimněte, že klíčové slovo var je nyní správně zpracováno.</span><span class="sxs-lookup"><span data-stu-id="bd963-384">Upon selecting your code fix, note that the var' keyword is now handled correctly.</span></span>

<span data-ttu-id="bd963-385">Nakonec přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="bd963-385">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="bd963-386">Po těchto změnách získáte červené vlnovky pouze na první dvě proměnné.</span><span class="sxs-lookup"><span data-stu-id="bd963-386">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="bd963-387">Přidejte `const` `i` do `j`obou a a dostanete `k` nové upozornění, `const`protože nyní může být .</span><span class="sxs-lookup"><span data-stu-id="bd963-387">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="bd963-388">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="bd963-388">Congratulations!</span></span> <span data-ttu-id="bd963-389">Vytvořili jste první rozšíření platformy kompilátoru .NET, které provádí průběžnou analýzu kódu za účelem zjištění problému a poskytuje rychlou opravu k jeho opravě.</span><span class="sxs-lookup"><span data-stu-id="bd963-389">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="bd963-390">Cestou jste se naučili mnoho rozhraní API kódu, které jsou součástí rozhraní .NET Compiler Platform SDK (Roslyn API).</span><span class="sxs-lookup"><span data-stu-id="bd963-390">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="bd963-391">Svou práci můžete zkontrolovat podle [dokončené ukázky](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) v našem ukázkovém úložišti GitHub.</span><span class="sxs-lookup"><span data-stu-id="bd963-391">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="bd963-392">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="bd963-392">Other resources</span></span>

- [<span data-ttu-id="bd963-393">Začínáme se syntaktickou analýzou</span><span class="sxs-lookup"><span data-stu-id="bd963-393">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="bd963-394">Začínáme se sémantickou analýzou</span><span class="sxs-lookup"><span data-stu-id="bd963-394">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)

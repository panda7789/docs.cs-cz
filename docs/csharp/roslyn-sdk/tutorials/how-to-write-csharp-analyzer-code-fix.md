---
title: 'Kurz: Zápis první opravu analyzátoru a kódu'
description: Tento kurz obsahuje podrobné pokyny k sestavení analyzátor a oprava kódu pomocí sady SDK kompilátoru .NET (Roslyn API).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: 45529a72e3c64a573bfc043fe44da29caed1a0c4
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870552"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="6fc05-103">Kurz: Zápis první opravu analyzátoru a kódu</span><span class="sxs-lookup"><span data-stu-id="6fc05-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="6fc05-104">Sada SDK platformy kompilátoru .NET poskytuje nástroje, které potřebujete k vytvoření vlastní upozornění tento cíl C# nebo kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6fc05-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="6fc05-105">Vaše **analyzátor** obsahuje kód, který rozpozná porušení pravidla.</span><span class="sxs-lookup"><span data-stu-id="6fc05-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="6fc05-106">Vaše **opravu kódu** obsahuje kód, který opraví porušení zásady.</span><span class="sxs-lookup"><span data-stu-id="6fc05-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="6fc05-107">Pravidla, která můžete implementovat můžou být čímkoli od strukturu kódu na kódování styl konvence pojmenování a další.</span><span class="sxs-lookup"><span data-stu-id="6fc05-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="6fc05-108">.NET Compiler Platform poskytuje rozhraní pro spuštění analýzy jako vývojáři psaní kódu a funkce všech rozhraní Visual Studia pro opravu kódu: zobrazující podtržení vlnovkou v editoru Visual Studio seznamu chyb, vytváření "žárovky" vyplnění návrhy a zobrazuje bohaté možnosti ve verzi preview návrhy jejich oprav.</span><span class="sxs-lookup"><span data-stu-id="6fc05-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="6fc05-109">V tomto kurzu prozkoumáte vytváření **analyzátor** a je v doprovodné **opravu kódu** pomocí rozhraní Roslyn API.</span><span class="sxs-lookup"><span data-stu-id="6fc05-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="6fc05-110">Analyzátor je způsob, jak provést analýzu zdrojového kódu a ohlásit problém pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="6fc05-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="6fc05-111">Analyzátor Volitelně můžete zadat taky opravy kódu, který představuje úpravy zdrojového kódu uživatele.</span><span class="sxs-lookup"><span data-stu-id="6fc05-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="6fc05-112">Tento kurz vytvoří analyzátor, který hledá místní deklarace proměnných, které mohou být deklarovány pomocí `const` modifikátor ale nejsou.</span><span class="sxs-lookup"><span data-stu-id="6fc05-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="6fc05-113">Související opravu kódu upravuje tyto deklarace pro přidání `const` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="6fc05-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6fc05-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fc05-114">Prerequisites</span></span>

* [<span data-ttu-id="6fc05-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="6fc05-115">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
* [<span data-ttu-id="6fc05-116">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="6fc05-116">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="6fc05-117">Budete muset nainstalovat **sada SDK platformy kompilátoru .NET** prostřednictvím instalačního Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="6fc05-117">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Intaller:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="6fc05-118">Existuje několik kroků k vytvoření a ověření vašich analyzer:</span><span class="sxs-lookup"><span data-stu-id="6fc05-118">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="6fc05-119">Vytvořte řešení.</span><span class="sxs-lookup"><span data-stu-id="6fc05-119">Create the solution.</span></span>
1. <span data-ttu-id="6fc05-120">Registrace analyzátoru název a popis.</span><span class="sxs-lookup"><span data-stu-id="6fc05-120">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="6fc05-121">Sestavy analyzátoru upozornění a doporučení.</span><span class="sxs-lookup"><span data-stu-id="6fc05-121">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="6fc05-122">Implementujte opravu kódu tak, aby přijímal doporučení.</span><span class="sxs-lookup"><span data-stu-id="6fc05-122">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="6fc05-123">Vylepšení analýzy prostřednictvím testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="6fc05-123">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="6fc05-124">Prozkoumání šablony analyzátoru</span><span class="sxs-lookup"><span data-stu-id="6fc05-124">Explore the analyzer template</span></span>

<span data-ttu-id="6fc05-125">Vaše analyzátor ohlásí uživateli žádné místní deklarace proměnných, které lze převést na lokální konstanty.</span><span class="sxs-lookup"><span data-stu-id="6fc05-125">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="6fc05-126">Zvažte například následující kód:</span><span class="sxs-lookup"><span data-stu-id="6fc05-126">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="6fc05-127">Ve výše uvedeném kódu `x` přiřazena konstantní hodnotou a se nikdy nemění.</span><span class="sxs-lookup"><span data-stu-id="6fc05-127">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="6fc05-128">Mohou být deklarovány pomocí `const` modifikátor:</span><span class="sxs-lookup"><span data-stu-id="6fc05-128">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="6fc05-129">Součástí analýzy k určení, zda proměnné může být změněna na konstantní vyžadující syntaktické analýzy, konstantní analýzy inicializačního výrazu a analýzy datového toku k zajištění, že proměnná je nikdy zapsána do.</span><span class="sxs-lookup"><span data-stu-id="6fc05-129">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="6fc05-130">Na platformě kompilátoru .NET poskytuje rozhraní API, která usnadňují provádění této analýzy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-130">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="6fc05-131">Prvním krokem je vytvoření nového jazyka C# **analyzátor s opravu kódu** projektu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-131">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

* <span data-ttu-id="6fc05-132">V sadě Visual Studio, zvolte **soubor > Nový > projekt...**  zobrazíte dialogové okno Nový projekt.</span><span class="sxs-lookup"><span data-stu-id="6fc05-132">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
* <span data-ttu-id="6fc05-133">V části **Visual C# > rozšíření**, zvolte **Analyzátor se oprava kódu (.NET Standard)** .</span><span class="sxs-lookup"><span data-stu-id="6fc05-133">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
* <span data-ttu-id="6fc05-134">Pojmenujte svůj projekt "**MakeConst**" a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="6fc05-134">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="6fc05-135">Vytvoří analyzátor s šablonou opravu kódu tři projekty: jeden obsahuje analyzer a oprava kódu, projekt testování částí je druhý a třetí je projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="6fc05-135">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="6fc05-136">Výchozí spouštěný projekt je projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="6fc05-136">The default startup project is the VSIX project.</span></span> <span data-ttu-id="6fc05-137">Stisknutím klávesy **F5** ke spuštění projektu VSIX.</span><span class="sxs-lookup"><span data-stu-id="6fc05-137">Press **F5** to start the VSIX project.</span></span> <span data-ttu-id="6fc05-138">Otevře se druhá instance sady Visual Studio, který byl načten nový analyzátor.</span><span class="sxs-lookup"><span data-stu-id="6fc05-138">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="6fc05-139">Při spuštění vaší analyzer spusťte druhé kopie sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6fc05-139">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="6fc05-140">Tato druhá kopie využívá k ukládání nastavení různých podregistru.</span><span class="sxs-lookup"><span data-stu-id="6fc05-140">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="6fc05-141">Která umožňuje rozlišovat visual nastavení v dvě kopie sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6fc05-141">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="6fc05-142">Můžete si vybrat jiný motiv pro experimentální spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6fc05-142">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="6fc05-143">Kromě toho není roaming nastavení nebo přihlášení k Visual Studio spustit účtu pomocí experimentální instanci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6fc05-143">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="6fc05-144">Která udržuje jiné nastavení.</span><span class="sxs-lookup"><span data-stu-id="6fc05-144">That keeps the settings different.</span></span>

<span data-ttu-id="6fc05-145">Ve druhé instanci aplikace Visual Studio, který jste právě spustili vytvořte nový projekt konzolové aplikace jazyka C# (.NET Core nebo projekt se rozhraní .NET Framework pracovat – analyzátory práce na úrovni zdroje.) Najeďte myší token s podtržení vlnovkou a zobrazí se text upozornění poskytované analyzátor.</span><span class="sxs-lookup"><span data-stu-id="6fc05-145">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="6fc05-146">Šablona vytvoří analyzátor, který bude hlásit upozornění na deklaraci typu, kde název typu obsahuje malá písmena, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="6fc05-146">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Analyzátor reporting upozornění](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="6fc05-148">Šablona také nabízí opravu kódu, který změní libovolný typ název obsahuje malá písmena na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6fc05-148">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="6fc05-149">Kliknutím na žárovku, zobrazí se upozornění zobrazíte navrhované změny.</span><span class="sxs-lookup"><span data-stu-id="6fc05-149">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="6fc05-150">Přijetí aktualizací navrhované změny, název typu a všechny odkazy na tento typ v řešení.</span><span class="sxs-lookup"><span data-stu-id="6fc05-150">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="6fc05-151">Teď, když už víte, počáteční analyzátor v akci, zavřete druhou instanci aplikace Visual Studio a vraťte se do projektu analyzátor.</span><span class="sxs-lookup"><span data-stu-id="6fc05-151">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="6fc05-152">Není nutné ke spuštění druhé kopie sady Visual Studio a vytvořte nový kód pro testování každé změně ve vaší analyzátor.</span><span class="sxs-lookup"><span data-stu-id="6fc05-152">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="6fc05-153">Šablona vytvoří projekt testu jednotek také za vás.</span><span class="sxs-lookup"><span data-stu-id="6fc05-153">The template also creates a unit test project for you.</span></span> <span data-ttu-id="6fc05-154">Tento projekt obsahuje dva testy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-154">That project contains two tests.</span></span> <span data-ttu-id="6fc05-155">`TestMethod1` ukazuje typický formát test, který analyzuje kódu bez aktivace diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="6fc05-155">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="6fc05-156">`TestMethod2` ukazuje formátu test, který se spustí Diagnostika a poté použije opravu navrhované kódu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-156">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="6fc05-157">Během vytváření analyzer a oprava kódu bude psaní testů pro různý kód struktury ověřit svou práci.</span><span class="sxs-lookup"><span data-stu-id="6fc05-157">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="6fc05-158">Testy jednotek pro analyzátory jsou mnohem rychleji než při testování interaktivně pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6fc05-158">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="6fc05-159">Analyzátor testování jednotek je skvělý nástroj, když víte, jaký kód konstrukce by měl a nesmí aktivovat váš analyzátor.</span><span class="sxs-lookup"><span data-stu-id="6fc05-159">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="6fc05-160">Načítají se vaše analyzátor v jiné kopii sady Visual Studio je skvělý nástroj pro zkoumání a najít konstrukce, které vás nemusí mít myslet na ještě.</span><span class="sxs-lookup"><span data-stu-id="6fc05-160">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="6fc05-161">Vytvoření registrace analyzátoru</span><span class="sxs-lookup"><span data-stu-id="6fc05-161">Create analyzer registrations</span></span>

<span data-ttu-id="6fc05-162">Šablona vytvoří počáteční `DiagnosticAnalyzer` třídy v **MakeConstAnalyzer.cs** souboru.</span><span class="sxs-lookup"><span data-stu-id="6fc05-162">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="6fc05-163">Tento počáteční analyzátor ukazuje dvě důležité vlastnosti každé analyzátor.</span><span class="sxs-lookup"><span data-stu-id="6fc05-163">This initial analyzer shows two important properties of every analyzer.</span></span>

* <span data-ttu-id="6fc05-164">Musíte zadat každou diagnostického analyzátoru `[DiagnosticAnalyzer]` atribut, který popisuje pracuje na jazyk.</span><span class="sxs-lookup"><span data-stu-id="6fc05-164">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
* <span data-ttu-id="6fc05-165">Každý diagnostického analyzátoru musí být odvozen od <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> třídy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-165">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="6fc05-166">Šablona také ukazuje základní funkce, které jsou součástí žádné analyzer:</span><span class="sxs-lookup"><span data-stu-id="6fc05-166">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="6fc05-167">Zaregistrujte akce.</span><span class="sxs-lookup"><span data-stu-id="6fc05-167">Register actions.</span></span> <span data-ttu-id="6fc05-168">Akce představují změny kódu, které by měly aktivovat váš analyzátor pro zkoumání kódu pro porušení.</span><span class="sxs-lookup"><span data-stu-id="6fc05-168">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="6fc05-169">Když Visual Studio zjistí úpravy kódu, které odpovídají registrované akce, volá metodu v analyzéru registrovaný.</span><span class="sxs-lookup"><span data-stu-id="6fc05-169">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="6fc05-170">Vytvoření diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="6fc05-170">Create diagnostics.</span></span> <span data-ttu-id="6fc05-171">Když vaše analyzátor zjistí narušení, vytvoří objekt diagnostické, využívající Visual Studio na upozornění pro uživatele porušení zásady.</span><span class="sxs-lookup"><span data-stu-id="6fc05-171">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="6fc05-172">Zaregistrovat akce v přepsání metody <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="6fc05-172">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6fc05-173">V tomto kurzu budete navštívíte **syntaxe uzly** hledá místní deklarace a zjistili, který z nich jsou konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6fc05-173">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="6fc05-174">Pokud deklarace může být konstantní, bude vaše analyzátor vytvořit a nahlaste diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="6fc05-174">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="6fc05-175">Prvním krokem je aktualizace konstanty registrace a `Initialize` metoda tak tyto konstanty označení vaší analyzátor "Ujistěte se, Const".</span><span class="sxs-lookup"><span data-stu-id="6fc05-175">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="6fc05-176">Většina řetězcové konstanty jsou definovány v souboru prostředků řetězce.</span><span class="sxs-lookup"><span data-stu-id="6fc05-176">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="6fc05-177">Měli byste postupovat podle této normy pro jednodušší lokalizace.</span><span class="sxs-lookup"><span data-stu-id="6fc05-177">You should follow that practice for easier localization.</span></span> <span data-ttu-id="6fc05-178">Otevřít **Resources.resx** souboru **MakeConst** analyzátor projektu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-178">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="6fc05-179">Zobrazí se editor prostředků.</span><span class="sxs-lookup"><span data-stu-id="6fc05-179">This displays the resource editor.</span></span> <span data-ttu-id="6fc05-180">Aktualizace řetězcové prostředky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6fc05-180">Update the string resources as follows:</span></span>

* <span data-ttu-id="6fc05-181">Změna `AnalyzerTitle` na "Proměnná může být změněna na konstantní".</span><span class="sxs-lookup"><span data-stu-id="6fc05-181">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
* <span data-ttu-id="6fc05-182">Změna `AnalyzerMessageFormat` do "Může být změněna na konstantní".</span><span class="sxs-lookup"><span data-stu-id="6fc05-182">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
* <span data-ttu-id="6fc05-183">Změna `AnalyzerDescription` aby "konstanty".</span><span class="sxs-lookup"><span data-stu-id="6fc05-183">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="6fc05-184">Změnit také, **modifikátor přístupu** rozevíracího seznamu `public`.</span><span class="sxs-lookup"><span data-stu-id="6fc05-184">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="6fc05-185">Který usnadňuje použití tyto konstanty při testech jednotek.</span><span class="sxs-lookup"><span data-stu-id="6fc05-185">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="6fc05-186">Jakmile budete hotovi, editor prostředků by měla vypadat jako postupujte podle obrázku je vidět:</span><span class="sxs-lookup"><span data-stu-id="6fc05-186">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Aktualizovat prostředky řetězců](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="6fc05-188">Zbývající změny jsou v souboru analyzátor.</span><span class="sxs-lookup"><span data-stu-id="6fc05-188">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="6fc05-189">Otevřít **MakeConstAnalyzer.cs** v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6fc05-189">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="6fc05-190">Změňte registrované akce z jednoho, který funguje na symboly, který funguje na syntaxi.</span><span class="sxs-lookup"><span data-stu-id="6fc05-190">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="6fc05-191">V `MakeConstAnalyzerAnalyzer.Initialize` metoda, vyhledejte řádek, který registruje akce na symboly:</span><span class="sxs-lookup"><span data-stu-id="6fc05-191">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="6fc05-192">Nahraďte ho následující řádek:</span><span class="sxs-lookup"><span data-stu-id="6fc05-192">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="6fc05-193">Po této změně můžete odstranit `AnalyzeSymbol` metody.</span><span class="sxs-lookup"><span data-stu-id="6fc05-193">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="6fc05-194">Tento analyzátor kontroluje <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, nikoli <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> příkazy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-194">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="6fc05-195">Všimněte si, že `AnalyzeNode` má červenou vlnovkou pod ním.</span><span class="sxs-lookup"><span data-stu-id="6fc05-195">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="6fc05-196">Kód, který jste právě přidali odkazy `AnalyzeNode` metodu, která nebyla deklarována.</span><span class="sxs-lookup"><span data-stu-id="6fc05-196">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="6fc05-197">Deklarujte metody pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6fc05-197">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="6fc05-198">Změnit `Category` "Využití" v **MakeConstAnalyzer.cs** jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="6fc05-198">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="6fc05-199">Najít místní deklarace, které by mohly být const</span><span class="sxs-lookup"><span data-stu-id="6fc05-199">Find local declarations that could be const</span></span>

<span data-ttu-id="6fc05-200">Je čas zápisu první verzi `AnalyzeNode` metody.</span><span class="sxs-lookup"><span data-stu-id="6fc05-200">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="6fc05-201">Měl by vypadat pro jeden místní deklarace, které by mohly `const` , ale není k dispozici, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="6fc05-201">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="6fc05-202">Prvním krokem je najít místní deklarace.</span><span class="sxs-lookup"><span data-stu-id="6fc05-202">The first step is to find local declarations.</span></span> <span data-ttu-id="6fc05-203">Přidejte následující kód, který `AnalyzeNode` v **MakeConstAnalyzer.cs**:</span><span class="sxs-lookup"><span data-stu-id="6fc05-203">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="6fc05-204">Toto přetypování vždy úspěšná, protože vaše analyzátor zaregistrovat pro změny místní deklarace a jenom místní deklarace.</span><span class="sxs-lookup"><span data-stu-id="6fc05-204">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="6fc05-205">Žádný jiný typ uzlu aktivuje volání dané k vaší `AnalyzeNode` metody.</span><span class="sxs-lookup"><span data-stu-id="6fc05-205">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="6fc05-206">Dále zkontrolujte deklaraci pro všechny `const` modifikátory.</span><span class="sxs-lookup"><span data-stu-id="6fc05-206">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="6fc05-207">Pokud je najít, vrátí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="6fc05-207">If you find them, return immediately.</span></span> <span data-ttu-id="6fc05-208">Následující kód vyhledá všechny `const` modifikátory u místní deklarace:</span><span class="sxs-lookup"><span data-stu-id="6fc05-208">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="6fc05-209">A konečně, je potřeba zkontrolovat, že může být proměnná `const`.</span><span class="sxs-lookup"><span data-stu-id="6fc05-209">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="6fc05-210">To znamená, že provedení, ji není nikdy přiřazeno po inicializaci.</span><span class="sxs-lookup"><span data-stu-id="6fc05-210">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="6fc05-211">Budete provádět některé pomocí sémantické analýzy <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span><span class="sxs-lookup"><span data-stu-id="6fc05-211">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="6fc05-212">Můžete použít `context` argument k určení, zda mohou být vytvořeny deklarace lokální proměnné `const`.</span><span class="sxs-lookup"><span data-stu-id="6fc05-212">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="6fc05-213">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> představuje všech sémantických informací v jediném souboru.</span><span class="sxs-lookup"><span data-stu-id="6fc05-213">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents of all semantic information in a single source file.</span></span> <span data-ttu-id="6fc05-214">Můžete další informace najdete v článku určeného po [sémantickým modelům](../work-with-semantics.md).</span><span class="sxs-lookup"><span data-stu-id="6fc05-214">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="6fc05-215">Budete používat <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> provádět analýzy toku dat v příkazu místní deklarace.</span><span class="sxs-lookup"><span data-stu-id="6fc05-215">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="6fc05-216">Potom použijte výsledky této analýzy toku dat k zajištění, že místní proměnná není zapsán s novou hodnotou někde jinde.</span><span class="sxs-lookup"><span data-stu-id="6fc05-216">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="6fc05-217">Volání <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> metodu rozšíření k získání <xref:Microsoft.CodeAnalysis.ILocalSymbol> pro proměnnou a zkontrolujte, že se nenachází se <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> kolekce dat tok analýzy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-217">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="6fc05-218">Přidejte následující kód do konce `AnalyzeNode` metody:</span><span class="sxs-lookup"><span data-stu-id="6fc05-218">Add the following code to the end of the `AnalyzeNode` method:</span></span>

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

<span data-ttu-id="6fc05-219">Kód, který právě přidali zajistí, že proměnné není upraven a proto nelze realizovat `const`.</span><span class="sxs-lookup"><span data-stu-id="6fc05-219">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="6fc05-220">Je čas vyvolání diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="6fc05-220">It's time to raise the diagnostic.</span></span> <span data-ttu-id="6fc05-221">Přidejte následující kód jako poslední řádek v `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="6fc05-221">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="6fc05-222">Průběh můžete zkontrolovat stisknutím kombinace kláves **F5** ke spouštění vaší analyzer.</span><span class="sxs-lookup"><span data-stu-id="6fc05-222">You can check your progress by pressing **F5** to run your analyzer.</span></span> <span data-ttu-id="6fc05-223">Můžete načíst konzolové aplikace, kterou jste vytvořili dříve a pak přidejte následující kód testu:</span><span class="sxs-lookup"><span data-stu-id="6fc05-223">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="6fc05-224">Žárovky by se měla objevit a vaše analyzátor ohlaste diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="6fc05-224">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="6fc05-225">Ale žárovky stále používá vygenerovanou šablonu opravu kódu a zjistíte, že ji můžete nastavit na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6fc05-225">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="6fc05-226">V další části vysvětluje, jak napsat kód opravy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-226">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="6fc05-227">Zápis opravy kódu</span><span class="sxs-lookup"><span data-stu-id="6fc05-227">Write the code fix</span></span>

<span data-ttu-id="6fc05-228">Analyzátor můžete zadat jednu nebo více oprav kódu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-228">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="6fc05-229">Oprava kódu definuje úpravy, které řeší nahlášeného problému.</span><span class="sxs-lookup"><span data-stu-id="6fc05-229">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="6fc05-230">Pro analyzátor, který jste vytvořili mohli zajistit opravu kódu, který se vkládá const – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="6fc05-230">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="6fc05-231">Uživatel vybere z žárovky uživatelského rozhraní v editoru a sady Visual Studio změny kódu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-231">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="6fc05-232">Otevřít **MakeConstCodeFixProvider.cs** soubory přidané pomocí šablony.</span><span class="sxs-lookup"><span data-stu-id="6fc05-232">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="6fc05-233">Tato oprava kódu je již svázanou s ID diagnostiky vytvářených diagnostického analyzátoru, ale ještě neimplementuje transformace správný kód.</span><span class="sxs-lookup"><span data-stu-id="6fc05-233">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="6fc05-234">Nejdřív byste měli odebrat některé kód šablony.</span><span class="sxs-lookup"><span data-stu-id="6fc05-234">First you should remove some of the template code.</span></span> <span data-ttu-id="6fc05-235">Změna názvu řetězec "Zkontrolujte konstanta":</span><span class="sxs-lookup"><span data-stu-id="6fc05-235">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="6fc05-236">V dalším kroku odstranit `MakeUppercaseAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="6fc05-236">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="6fc05-237">To už neplatí.</span><span class="sxs-lookup"><span data-stu-id="6fc05-237">It no longer applies.</span></span>

<span data-ttu-id="6fc05-238">Všichni poskytovatelé opravu kódu jsou odvozeny z <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span><span class="sxs-lookup"><span data-stu-id="6fc05-238">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="6fc05-239">Všechny přepsat <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> hlášení opravy kódu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6fc05-239">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="6fc05-240">V `RegisterCodeFixesAsync`, změňte typ uzlu předchůdce hledáte k <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> tak, aby odpovídaly diagnostiky:</span><span class="sxs-lookup"><span data-stu-id="6fc05-240">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="6fc05-241">V dalším kroku změňte poslední řádek k registraci opravu kódu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-241">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="6fc05-242">Jste kód opravili správně vytvoří nový dokument, který je výsledkem přidání `const` modifikátor na existující deklaraci:</span><span class="sxs-lookup"><span data-stu-id="6fc05-242">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="6fc05-243">Můžete si všimnout červenou vlnovkou v kódu, kterou jste právě přidali na symbol `MakeConstAsync`.</span><span class="sxs-lookup"><span data-stu-id="6fc05-243">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="6fc05-244">Přidat deklaraci `MakeConstAsync` , jako je následující kód:</span><span class="sxs-lookup"><span data-stu-id="6fc05-244">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="6fc05-245">Vaše nová `MakeConstAsync` metoda provede transformaci <xref:Microsoft.CodeAnalysis.Document> představující uživatele zdrojový soubor do nového <xref:Microsoft.CodeAnalysis.Document> , která teď obsahuje `const` deklarace.</span><span class="sxs-lookup"><span data-stu-id="6fc05-245">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="6fc05-246">Vytvoření nového `const` – klíčové slovo token pro vložení do přední části příkazu deklarace.</span><span class="sxs-lookup"><span data-stu-id="6fc05-246">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="6fc05-247">Dejte pozor, abyste nejdřív odebrat všechny úvodní triviální prvek z první token příkazu deklarace a připojte ji k `const` token.</span><span class="sxs-lookup"><span data-stu-id="6fc05-247">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="6fc05-248">Přidejte následující kód, který `MakeConstAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="6fc05-248">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="6fc05-249">V dalším kroku přidejte `const` token deklarace pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6fc05-249">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="6fc05-250">V dalším kroku naformátujte nové deklarace tak, aby odpovídaly pravidla formátování C#.</span><span class="sxs-lookup"><span data-stu-id="6fc05-250">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="6fc05-251">Lepší prostředí pro formátování provedené změny tak, aby odpovídaly existujícího kódu vytvoří.</span><span class="sxs-lookup"><span data-stu-id="6fc05-251">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="6fc05-252">Přidejte následující příkaz ihned po existující kód:</span><span class="sxs-lookup"><span data-stu-id="6fc05-252">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="6fc05-253">Nový obor názvů se vyžaduje pro tento kód.</span><span class="sxs-lookup"><span data-stu-id="6fc05-253">A new namespace is required for this code.</span></span> <span data-ttu-id="6fc05-254">Přidejte následující `using` příkaz do horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="6fc05-254">Add the following `using` statement to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="6fc05-255">Posledním krokem je provést úpravy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-255">The final step is to make your edit.</span></span> <span data-ttu-id="6fc05-256">K tomuto procesu tři kroky:</span><span class="sxs-lookup"><span data-stu-id="6fc05-256">There are three steps to this process:</span></span>

1. <span data-ttu-id="6fc05-257">Získejte popisovač pro k existujícímu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-257">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="6fc05-258">Vytvoření nového dokumentu tak, že nahradíte existující deklarace s novou deklaraci.</span><span class="sxs-lookup"><span data-stu-id="6fc05-258">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="6fc05-259">Vrátí nový dokument.</span><span class="sxs-lookup"><span data-stu-id="6fc05-259">Return the new document.</span></span>

<span data-ttu-id="6fc05-260">Přidejte následující kód do konce `MakeConstAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="6fc05-260">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="6fc05-261">Jste kód opravili správně kódu připravená k vyzkoušení.</span><span class="sxs-lookup"><span data-stu-id="6fc05-261">Your code fix is ready to try.</span></span>  <span data-ttu-id="6fc05-262">Stisknutím klávesy F5 spusťte analyzátor projektu ve druhé instanci aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6fc05-262">Press F5 to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="6fc05-263">Ve druhé instanci aplikace Visual Studio vytvořte nový projekt konzolové aplikace jazyka C# a přidejte několik místní deklarace proměnných inicializována s konstantní hodnoty do metody Main.</span><span class="sxs-lookup"><span data-stu-id="6fc05-263">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="6fc05-264">Uvidíte, že jsou hlášeny jako varování, jak je uvedeno níže.</span><span class="sxs-lookup"><span data-stu-id="6fc05-264">You'll see that they are reported as warnings as below.</span></span>

![Může být const upozornění](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="6fc05-266">Jsme udělali spoustu průběh.</span><span class="sxs-lookup"><span data-stu-id="6fc05-266">You've made a lot of progress.</span></span> <span data-ttu-id="6fc05-267">Existují podtržení vlnovkou v rámci deklarace, které mohou být provedeny `const`.</span><span class="sxs-lookup"><span data-stu-id="6fc05-267">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="6fc05-268">Ale bude stále na práci není.</span><span class="sxs-lookup"><span data-stu-id="6fc05-268">But there is still work to do.</span></span> <span data-ttu-id="6fc05-269">To funguje správně, pokud přidáte `const` deklaracích počínaje `i`, pak `j` a nakonec `k`.</span><span class="sxs-lookup"><span data-stu-id="6fc05-269">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="6fc05-270">Ale pokud přidáte `const` modifikátor v jiném pořadí, počínaje `k`, vaše analyzátor vytvoří chyby: `k` nejde použít deklaraci `const`, není-li `i` a `j` jsou již `const`.</span><span class="sxs-lookup"><span data-stu-id="6fc05-270">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="6fc05-271">Máte s nimi dělat další analýzy k zajištění, že zpracovávat různé způsoby proměnné mohou být deklarovány a inicializovány.</span><span class="sxs-lookup"><span data-stu-id="6fc05-271">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="6fc05-272">Vytvořit testy řízené daty</span><span class="sxs-lookup"><span data-stu-id="6fc05-272">Build data driven tests</span></span>

<span data-ttu-id="6fc05-273">Analyzátoru a kódu opravit práce v jednoduchém případě jedné deklarace, které můžete provést const.</span><span class="sxs-lookup"><span data-stu-id="6fc05-273">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="6fc05-274">Existuje mnoho příkazy možné deklarace, kde je tato implementace chyby.</span><span class="sxs-lookup"><span data-stu-id="6fc05-274">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="6fc05-275">Při práci s knihovnou testovací jednotky zapsány pomocí šablony budete řešit tyto případy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-275">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="6fc05-276">Je mnohem rychlejší než opakovaného otevírání druhé kopie sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6fc05-276">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="6fc05-277">Otevřít **MakeConstUnitTests.cs** souboru v projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="6fc05-277">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="6fc05-278">Šablona vytvoří dva testy, které následují dvě běžné vzory pro analyzátor a testování částí opravu kódu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-278">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="6fc05-279">`TestMethod1` ukazuje, že vzor pro test, který zajišťuje, analyzátor nebude hlásit Diagnostika v případě, že by se neměly.</span><span class="sxs-lookup"><span data-stu-id="6fc05-279">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="6fc05-280">`TestMethod2` ukazuje vzor pro vytváření sestav Diagnostika a spuštěný opravu kódu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-280">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="6fc05-281">Kód pro téměř každý test pro vaše analyzátor používá jednu z těchto dvou vzorků.</span><span class="sxs-lookup"><span data-stu-id="6fc05-281">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="6fc05-282">Pro první krok můžete tyto testy Přepracujte jako testy řízené daty.</span><span class="sxs-lookup"><span data-stu-id="6fc05-282">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="6fc05-283">Pak bude možné snadno vytvořit nové testy tak, že přidáte nový řetězec konstanty k reprezentaci různých testovací vstupy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-283">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="6fc05-284">Z důvodu efektivity prvním krokem je lze refaktorovat dva testy do testy řízené daty.</span><span class="sxs-lookup"><span data-stu-id="6fc05-284">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="6fc05-285">Potom stačí definovat několik řetězcové konstanty pro každý nový test.</span><span class="sxs-lookup"><span data-stu-id="6fc05-285">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="6fc05-286">Při vaší refaktoring přejmenování obě metody lepší názvy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-286">While your refactoring, rename both methods to better names.</span></span> <span data-ttu-id="6fc05-287">Nahraďte `TestMethod1` je vyvolána s tímto testem, který zajišťuje žádné diagnostiky:</span><span class="sxs-lookup"><span data-stu-id="6fc05-287">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="6fc05-288">Nový řádek dat pro tento test můžete vytvořit tak, že definujete jakékoli fragment kódu, který by nemělo způsobit vaší diagnostiky pro aktivaci upozornění.</span><span class="sxs-lookup"><span data-stu-id="6fc05-288">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="6fc05-289">Toto přetížení `VerifyCSharpDiagnostic` úspěšný, pokud neexistují žádné diagnostiky pro fragment kódu zdroje.</span><span class="sxs-lookup"><span data-stu-id="6fc05-289">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="6fc05-290">V dalším kroku nahraďte `TestMethod2` tento test, který zajišťuje diagnostiky se vyvolá, a oprava kódu u zdroje fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="6fc05-290">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

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

<span data-ttu-id="6fc05-291">Předchozí kód také provedli několik změn kódu, který sestaví očekávaný výsledek diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="6fc05-291">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="6fc05-292">Používá veřejné konstanty zaregistrovaný v `MakeConst` analyzátor.</span><span class="sxs-lookup"><span data-stu-id="6fc05-292">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="6fc05-293">Kromě toho používá dva řetězcové konstanty pro zdroje vstupu a oprava.</span><span class="sxs-lookup"><span data-stu-id="6fc05-293">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="6fc05-294">Přidejte následující konstanty na řetězec `UnitTest` třídy:</span><span class="sxs-lookup"><span data-stu-id="6fc05-294">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="6fc05-295">Spusťte tyto dva testy, abyste měli jistotu, že bude úspěšné.</span><span class="sxs-lookup"><span data-stu-id="6fc05-295">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="6fc05-296">V sadě Visual Studio, otevřete **Průzkumník testů** tak, že vyberete **testovací** > **Windows** > **Průzkumník testů**.</span><span class="sxs-lookup"><span data-stu-id="6fc05-296">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span>  <span data-ttu-id="6fc05-297">Stiskněte klávesu **spustit všechny** odkaz.</span><span class="sxs-lookup"><span data-stu-id="6fc05-297">The press the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="6fc05-298">Vytvořit testy pro platné deklarace</span><span class="sxs-lookup"><span data-stu-id="6fc05-298">Create tests for valid declarations</span></span>

<span data-ttu-id="6fc05-299">Jako obecné pravidlo má analyzátory ukončit co nejrychleji, provádění minimálním úsilím.</span><span class="sxs-lookup"><span data-stu-id="6fc05-299">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="6fc05-300">Visual Studio volání analyzátory zaregistrovaný jako uživatelského kódu pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-300">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="6fc05-301">Schopnost reagovat je klíčovým požadavkem.</span><span class="sxs-lookup"><span data-stu-id="6fc05-301">Responsiveness is a key requirement.</span></span> <span data-ttu-id="6fc05-302">Existuje několik testovacích případů pro kód, který by neměl zvýšit vaši diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="6fc05-302">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="6fc05-303">Vaše analyzátor již zpracovává jeden z těchto testů, případ, kdy se po jejich inicializaci přiřazenou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="6fc05-303">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="6fc05-304">Přidejte následující konstantu řetězce do testů pro reprezentaci případ:</span><span class="sxs-lookup"><span data-stu-id="6fc05-304">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="6fc05-305">Pak přidejte řádek dat pro tento test, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="6fc05-305">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="6fc05-306">Tento test úspěšný také.</span><span class="sxs-lookup"><span data-stu-id="6fc05-306">This test passes as well.</span></span> <span data-ttu-id="6fc05-307">V dalším kroku přidejte konstanty pro podmínky, které nebyly dosud zpracovány:</span><span class="sxs-lookup"><span data-stu-id="6fc05-307">Next, add constants for conditions you haven't handled yet:</span></span>

* <span data-ttu-id="6fc05-308">Deklarace, které jsou již `const`, protože jsou již const:</span><span class="sxs-lookup"><span data-stu-id="6fc05-308">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

* <span data-ttu-id="6fc05-309">Deklarace, které mají žádný inicializátor, protože neexistuje žádná hodnota používat:</span><span class="sxs-lookup"><span data-stu-id="6fc05-309">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

* <span data-ttu-id="6fc05-310">Deklarace, kde inicializátor není konstantní, protože nemohou být konstanty z doby kompilace:</span><span class="sxs-lookup"><span data-stu-id="6fc05-310">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="6fc05-311">Může být ještě složitější, protože C# umožňuje více deklarací jako jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="6fc05-311">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="6fc05-312">Vezměte v úvahu následující řetězcová konstanta testovacího případu:</span><span class="sxs-lookup"><span data-stu-id="6fc05-312">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="6fc05-313">Proměnná `i` provádět – konstanta, ale proměnná `j` nelze.</span><span class="sxs-lookup"><span data-stu-id="6fc05-313">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="6fc05-314">Proto tento příkaz nelze nastavit jako deklarace const.</span><span class="sxs-lookup"><span data-stu-id="6fc05-314">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="6fc05-315">Přidat `DataRow` deklarace pro tyto testy:</span><span class="sxs-lookup"><span data-stu-id="6fc05-315">Add the `DataRow` declarations for all these tests:</span></span>

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

<span data-ttu-id="6fc05-316">Znovu spusťte testy a zobrazí se vám tyto nové testovací případy selhání.</span><span class="sxs-lookup"><span data-stu-id="6fc05-316">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="6fc05-317">Aktualizujte vaše analyzátor ignorovat správné deklarace</span><span class="sxs-lookup"><span data-stu-id="6fc05-317">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="6fc05-318">V analyzéru je potřeba určitá vylepšení `AnalyzeNode` metoda odfiltrovat kód, který splňuje tyto podmínky.</span><span class="sxs-lookup"><span data-stu-id="6fc05-318">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="6fc05-319">Všechny související podmínky jsou podobné změny budou opravit tyto podmínky.</span><span class="sxs-lookup"><span data-stu-id="6fc05-319">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="6fc05-320">Proveďte následující změny `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="6fc05-320">Make the following changes to `AnalyzeNode`:</span></span>

* <span data-ttu-id="6fc05-321">Sémantická analýza prozkoumat jedné deklarace proměnné.</span><span class="sxs-lookup"><span data-stu-id="6fc05-321">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="6fc05-322">Tento kód musí být v `foreach` smyčku, která zkontroluje všechny proměnné deklarované ve stejném příkazu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-322">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
* <span data-ttu-id="6fc05-323">Každou deklaraci proměnných musí mít inicializátor.</span><span class="sxs-lookup"><span data-stu-id="6fc05-323">Each declared variable needs to have an initializer.</span></span>
* <span data-ttu-id="6fc05-324">Inicializátor každé deklarované proměnné musí být konstanta za kompilace.</span><span class="sxs-lookup"><span data-stu-id="6fc05-324">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="6fc05-325">Ve vaší `AnalyzeNode` metoda, nahraďte původní sémantické analýzy:</span><span class="sxs-lookup"><span data-stu-id="6fc05-325">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

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

<span data-ttu-id="6fc05-326">Pomocí následujícího fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="6fc05-326">with the following code snippet:</span></span>

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

<span data-ttu-id="6fc05-327">První `foreach` smyčky zkontroluje každou deklaraci proměnné pomocí syntaktické analýzy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-327">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="6fc05-328">První kontrola zaručuje, že má proměnná inicializátor.</span><span class="sxs-lookup"><span data-stu-id="6fc05-328">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="6fc05-329">Druhý kontrola zaručuje, že inicializátoru je konstanta.</span><span class="sxs-lookup"><span data-stu-id="6fc05-329">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="6fc05-330">Druhý smyčka má původní sémantické analýzy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-330">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="6fc05-331">Sémantické kontroly jsou v samostatné smyčky, protože má větší vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="6fc05-331">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="6fc05-332">Znovu spusťte testy a měli byste vidět jejich předávání.</span><span class="sxs-lookup"><span data-stu-id="6fc05-332">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="6fc05-333">Přidejte poslední polština</span><span class="sxs-lookup"><span data-stu-id="6fc05-333">Add the final polish</span></span>

<span data-ttu-id="6fc05-334">Už jste téměř hotovi.</span><span class="sxs-lookup"><span data-stu-id="6fc05-334">You're almost done.</span></span> <span data-ttu-id="6fc05-335">Existuje několik další podmínky pro vaše analyzátor pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="6fc05-335">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="6fc05-336">Visual Studio volá analyzátory, když uživatel píše kód.</span><span class="sxs-lookup"><span data-stu-id="6fc05-336">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="6fc05-337">Je často případ, který vaše analyzátor bude volána pro kód, který nepodporuje kompilaci.</span><span class="sxs-lookup"><span data-stu-id="6fc05-337">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="6fc05-338">Diagnostického analyzátoru `AnalyzeNode` metoda nekontroluje, jestli je konstantní hodnoty lze převést na typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="6fc05-338">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="6fc05-339">Ano, aktuální implementace využívá elastic převést nesprávná deklarace například int i = "abc" "na lokální konstanta.</span><span class="sxs-lookup"><span data-stu-id="6fc05-339">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="6fc05-340">Přidáte konstantu zdrojové řetězce pro tuto podmínku:</span><span class="sxs-lookup"><span data-stu-id="6fc05-340">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="6fc05-341">Kromě toho nejsou správně zpracovány typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="6fc05-341">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="6fc05-342">Pouze konstantní hodnota povolená pro typ odkazu je `null`, s výjimkou v tomto případě <xref:System.String?displayProperty=nameWIthType>, což umožňuje řetězcové literály.</span><span class="sxs-lookup"><span data-stu-id="6fc05-342">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWIthType>, which allows string literals.</span></span> <span data-ttu-id="6fc05-343">Jinými slovy `const string s = "abc"` je právní, ale `const object s = "abc"` není.</span><span class="sxs-lookup"><span data-stu-id="6fc05-343">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="6fc05-344">Tento fragment kódu ověří tuto podmínku:</span><span class="sxs-lookup"><span data-stu-id="6fc05-344">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="6fc05-345">Bude důkladné, budete muset přidat další test, abyste měli jistotu, že můžete vytvořit deklaraci konstanty pro řetězec.</span><span class="sxs-lookup"><span data-stu-id="6fc05-345">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="6fc05-346">Následující fragment kódu definuje kód, který vyvolá diagnostickou i kód po použití opravy:</span><span class="sxs-lookup"><span data-stu-id="6fc05-346">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="6fc05-347">Nakonec pokud je proměnná deklarována s `var` – klíčové slovo, nemá špatného opravu kódu a generuje `const var` prohlášení, což není podporováno v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="6fc05-347">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="6fc05-348">Chcete-li vyřešit tuto chybu, musíte nahradit opravu kódu `var` – klíčové slovo s názvem odvozený typ:</span><span class="sxs-lookup"><span data-stu-id="6fc05-348">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="6fc05-349">Tyto změny aktualizují data řádku deklarace pro oba testy.</span><span class="sxs-lookup"><span data-stu-id="6fc05-349">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="6fc05-350">Následující kód ukazuje tyto testy se všechny atributy řádků dat:</span><span class="sxs-lookup"><span data-stu-id="6fc05-350">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="6fc05-351">Naštěstí všechny výše uvedené chyby se dají řešit pomocí stejné techniky, které právě jste se dozvěděli.</span><span class="sxs-lookup"><span data-stu-id="6fc05-351">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="6fc05-352">Chcete-li oprava první chyby, nejdřív otevřete **DiagnosticAnalyzer.cs** a vyhledejte smyčky foreach, kde každý z místní deklarace inicializátory jsou zkontrolovány Ujistěte se, že jsou přiřazení konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6fc05-352">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="6fc05-353">Okamžitě _před_ první smyčka foreach, volání `context.SemanticModel.GetTypeInfo()` načíst podrobnosti o deklarovaný typ lokální deklarace:</span><span class="sxs-lookup"><span data-stu-id="6fc05-353">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="6fc05-354">Potom v rámci vaší `foreach` opakovat, zkontrolujte každý inicializační výraz, ujistěte se, že je lze převést na typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="6fc05-354">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="6fc05-355">Přidejte následující kontroly až se ujistíte, že inicializátoru je konstanta:</span><span class="sxs-lookup"><span data-stu-id="6fc05-355">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="6fc05-356">Další změně staví na poslední z nich.</span><span class="sxs-lookup"><span data-stu-id="6fc05-356">The next change builds upon the last one.</span></span> <span data-ttu-id="6fc05-357">Před uzavírací složenou závorku prvního foreach smyčky, přidejte následující kód pro kontrolu typu místní deklarace při konstanty je řetězec nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="6fc05-357">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

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

<span data-ttu-id="6fc05-358">Je nutné napsat kód o něco více ve zprostředkovateli opravu kódu k nahrazení var' – klíčové slovo s názvem správného typu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-358">You must write a bit more code in your code fix provider to replace the var' keyword with the correct type name.</span></span> <span data-ttu-id="6fc05-359">Vraťte se na **CodeFixProvider.cs**.</span><span class="sxs-lookup"><span data-stu-id="6fc05-359">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="6fc05-360">Kód, který přidáte provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="6fc05-360">The code you'll add does the following steps:</span></span>

* <span data-ttu-id="6fc05-361">Zkontrolujte, jestli je deklarace `var` deklarace, a pokud je:</span><span class="sxs-lookup"><span data-stu-id="6fc05-361">Check if the declaration is a `var` declaration, and if it is:</span></span>
* <span data-ttu-id="6fc05-362">Vytvoření nového typu odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-362">Create a new type for the inferred type.</span></span>
* <span data-ttu-id="6fc05-363">Ujistěte se, že deklarace typu není alias.</span><span class="sxs-lookup"><span data-stu-id="6fc05-363">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="6fc05-364">Pokud ano, je možné deklarovat `const var`.</span><span class="sxs-lookup"><span data-stu-id="6fc05-364">If so, it is legal to declare `const var`.</span></span>
* <span data-ttu-id="6fc05-365">Ujistěte se, že `var` není název typu v rámci tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-365">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="6fc05-366">(Pokud ano, `const var` je platný).</span><span class="sxs-lookup"><span data-stu-id="6fc05-366">(If so, `const var` is legal).</span></span>
* <span data-ttu-id="6fc05-367">Zjednodušení úplný název typu</span><span class="sxs-lookup"><span data-stu-id="6fc05-367">Simplify the full type name</span></span>

<span data-ttu-id="6fc05-368">Že zdá se, že velké množství kódu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-368">That sounds like a lot of code.</span></span> <span data-ttu-id="6fc05-369">Není.</span><span class="sxs-lookup"><span data-stu-id="6fc05-369">It's not.</span></span> <span data-ttu-id="6fc05-370">Nahraďte řádek, který deklaruje a inicializuje `newLocal` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="6fc05-370">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="6fc05-371">Prochází hned po inicializaci `newModifiers`:</span><span class="sxs-lookup"><span data-stu-id="6fc05-371">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="6fc05-372">Bude nutné, aby vám ho přidal `using` příkaz k použití <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> typu:</span><span class="sxs-lookup"><span data-stu-id="6fc05-372">You'll need to add one `using` statement to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="6fc05-373">Spuštění testů a bude by všechny úspěšné.</span><span class="sxs-lookup"><span data-stu-id="6fc05-373">Run your tests, and they should all pass.</span></span> <span data-ttu-id="6fc05-374">Spuštěním na dokončení analyzátor Blahopřání sami.</span><span class="sxs-lookup"><span data-stu-id="6fc05-374">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="6fc05-375">Načíst, stiskněte Ctrl + F5 ke spuštění projektu analyzátor v druhé instance sady Visual Studio s rozšířením Roslyn ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="6fc05-375">Press Ctrl+F5 to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

* <span data-ttu-id="6fc05-376">Ve druhé instanci aplikace Visual Studio vytvořte nový projekt konzolové aplikace jazyka C# a přidejte `int x = "abc";` do metody Main.</span><span class="sxs-lookup"><span data-stu-id="6fc05-376">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="6fc05-377">Díky první oprava chyby bez upozornění by se měly hlásit pro deklarace lokální proměnné (i když dochází k chybě kompilátoru podle očekávání).</span><span class="sxs-lookup"><span data-stu-id="6fc05-377">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
* <span data-ttu-id="6fc05-378">V dalším kroku přidejte `object s = "abc";` do metody Main.</span><span class="sxs-lookup"><span data-stu-id="6fc05-378">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="6fc05-379">Z důvodu druhý oprava chyby by se měly hlásit bez upozornění.</span><span class="sxs-lookup"><span data-stu-id="6fc05-379">Because of the second bug fix, no warning should be reported.</span></span>
* <span data-ttu-id="6fc05-380">Nakonec přidejte další místní proměnná, která používá `var` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6fc05-380">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="6fc05-381">Uvidíte, že upozornění je hlášeno a návrh se zobrazí pod vlevo.</span><span class="sxs-lookup"><span data-stu-id="6fc05-381">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
* <span data-ttu-id="6fc05-382">Přesune blikající kurzor editoru přes podtržení vlnovkou a stiskněte klávesu Ctrl +.</span><span class="sxs-lookup"><span data-stu-id="6fc05-382">Move the editor caret over the squiggly underline and press Ctrl+.</span></span> <span data-ttu-id="6fc05-383">Chcete-li zobrazit opravu navrhované kódu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-383">to display the suggested code fix.</span></span> <span data-ttu-id="6fc05-384">Po výběru kód opravit, Všimněte si, že var' – klíčové slovo nyní správně zpracovaly.</span><span class="sxs-lookup"><span data-stu-id="6fc05-384">Upon selecting your code fix, note that the var' keyword is now handled correctly.</span></span>

<span data-ttu-id="6fc05-385">Nakonec přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="6fc05-385">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="6fc05-386">Po provedení těchto změn získat červenou vlnovkou jenom na prvních dvou proměnných.</span><span class="sxs-lookup"><span data-stu-id="6fc05-386">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="6fc05-387">Přidat `const` zároveň `i` a `j`, a získat nové upozornění `k` vzhledem k tomu, že teď může být `const`.</span><span class="sxs-lookup"><span data-stu-id="6fc05-387">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="6fc05-388">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="6fc05-388">Congratulations!</span></span> <span data-ttu-id="6fc05-389">Vytvořili jste své první rozšíření .NET Compiler Platform, který provádí analýzu kódu na průběžné rozpoznat potíže a nabízí rychlé opravy na opravu.</span><span class="sxs-lookup"><span data-stu-id="6fc05-389">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="6fc05-390">Na cestě když jste se naučili řadu kódu rozhraní API, která jsou součástí sady SDK platformy kompilátoru .NET (rozhraní Roslyn API).</span><span class="sxs-lookup"><span data-stu-id="6fc05-390">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="6fc05-391">Můžete zkontrolovat práce proti [úplnou vzorovou](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) v našem úložišti GitHub s ukázkami.</span><span class="sxs-lookup"><span data-stu-id="6fc05-391">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span> <span data-ttu-id="6fc05-392">Nebo si můžete stáhnout [soubor zip dokončení projektu](https://github.com/dotnet/samples/blob/master/csharp/roslyn-sdk/Tutorials/MakeConst.zip)</span><span class="sxs-lookup"><span data-stu-id="6fc05-392">Or you can download [zip file of the completed project](https://github.com/dotnet/samples/blob/master/csharp/roslyn-sdk/Tutorials/MakeConst.zip)</span></span>

## <a name="other-resources"></a><span data-ttu-id="6fc05-393">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="6fc05-393">Other resources</span></span>

- [<span data-ttu-id="6fc05-394">Začínáme s analýzou syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fc05-394">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="6fc05-395">Začínáme s sémantická analýza</span><span class="sxs-lookup"><span data-stu-id="6fc05-395">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)

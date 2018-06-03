---
title: 'Začínáme s F # v sadě Visual Studio kódu'
description: 'Další informace o použití F # s Visual Studio Code a suite Ionide modulu plug-in.'
ms.date: 05/28/2018
ms.openlocfilehash: e56274caf36be231338876ded5a6d7c7968906b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728625"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="f698b-103">Začínáme s F # v sadě Visual Studio kódu</span><span class="sxs-lookup"><span data-stu-id="f698b-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="f698b-104">Můžete napsat F # [Visual Studio Code](https://code.visualstudio.com) s [modulu plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), abyste získali optimálního uživatelského prostředí integrované vývojové prostředí (IDE) a platformy, lightweight s IntelliSense a základní kódu refaktoring.</span><span class="sxs-lookup"><span data-stu-id="f698b-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="f698b-105">Navštivte [Ionide.io](http://ionide.io) Další informace o sadě modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="f698b-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f698b-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f698b-106">Prerequisites</span></span>

<span data-ttu-id="f698b-107">Musíte mít [nainstalovat git](https://git-scm.com/download) a k dispozici na CESTU ke zkontrolujte pomocí šablon projektu v Ionide.</span><span class="sxs-lookup"><span data-stu-id="f698b-107">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span> <span data-ttu-id="f698b-108">Můžete ověřit, zda je správně nainstalován zadáním `git --version` v příkazovém řádku a stiskněte **Enter**.</span><span class="sxs-lookup"><span data-stu-id="f698b-108">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="f698b-109">macOS</span><span class="sxs-lookup"><span data-stu-id="f698b-109">macOS</span></span>](#tab/macos)

<span data-ttu-id="f698b-110">Používá Ionide [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="f698b-110">Ionide uses [Mono](http://www.mono-project.com).</span></span> <span data-ttu-id="f698b-111">Nejjednodušší způsob, jak nainstalovat Mono v systému macOS je prostřednictvím Homebrew.</span><span class="sxs-lookup"><span data-stu-id="f698b-111">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="f698b-112">Jednoduše zadejte do terminálu následující:</span><span class="sxs-lookup"><span data-stu-id="f698b-112">Simply type the following into your terminal:</span></span>

```
brew install mono
```

<span data-ttu-id="f698b-113">Je také nutné nainstalovat [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="f698b-113">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="f698b-114">Linux</span><span class="sxs-lookup"><span data-stu-id="f698b-114">Linux</span></span>](#tab/linux)

<span data-ttu-id="f698b-115">V systému Linux, Ionide také používá [Mono](https://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="f698b-115">On Linux, Ionide also uses [Mono](https://www.mono-project.com).</span></span> <span data-ttu-id="f698b-116">Pokud jste na Debian a Ubuntu, můžete použít následující:</span><span class="sxs-lookup"><span data-stu-id="f698b-116">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="f698b-117">Je také nutné nainstalovat [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="f698b-117">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="f698b-118">Windows</span><span class="sxs-lookup"><span data-stu-id="f698b-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="f698b-119">Pokud jste v systému Windows, musíte [instalaci sady Visual Studio s podporou F #](get-started-visual-studio.md#installing-f).</span><span class="sxs-lookup"><span data-stu-id="f698b-119">If you're on Windows, you must [install Visual Studio with F# support](get-started-visual-studio.md#installing-f).</span></span> <span data-ttu-id="f698b-120">Tím se nainstaluje všechny komponenty potřebné k zápisu, zkompilování a spuštění kódu F #.</span><span class="sxs-lookup"><span data-stu-id="f698b-120">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="f698b-121">Je také nutné nainstalovat [.NET Core SDK](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="f698b-121">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="f698b-122">Instalace Visual Studio Code a Ionide modulu plug-in</span><span class="sxs-lookup"><span data-stu-id="f698b-122">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="f698b-123">Můžete nainstalovat Visual Studio Code z [code.visualstudio.com](https://code.visualstudio.com) webu.</span><span class="sxs-lookup"><span data-stu-id="f698b-123">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span>

<span data-ttu-id="f698b-124">Poté kliknutím na ikonu rozšíření a vyhledejte "Ionide":</span><span class="sxs-lookup"><span data-stu-id="f698b-124">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="f698b-125">Pouze modul plug-in, které jsou potřebné pro podporu F # ve Visual Studio Code je [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="f698b-125">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="f698b-126">Ale můžete taky nainstalovat [Ionide PHISHING](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) získat [ZFALŠOVAT](https://fsharp.github.io/FAKE/) podporu a [Ionide Stáhnout](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) získat [Stáhnout](https://fsprojects.github.io/Paket/) podporovat.</span><span class="sxs-lookup"><span data-stu-id="f698b-126">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="f698b-127">ZFALŠOVAT a stáhnout další nástroje komunity F # pro sestavování projektů a správu závislosti, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f698b-127">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="f698b-128">Vytvoření prvního projektu s Ionide</span><span class="sxs-lookup"><span data-stu-id="f698b-128">Creating your first project with Ionide</span></span>

<span data-ttu-id="f698b-129">Pokud chcete vytvořit nový projekt F #, otevřete Visual Studio Code do nové složky (můžete pojmenovat se vám líbí).</span><span class="sxs-lookup"><span data-stu-id="f698b-129">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="f698b-130">Dále otevřete příkaz pallette (**zobrazení > příkaz Pallette**) a zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="f698b-130">Next, open the command pallette (**View > Command Pallette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="f698b-131">To používá technologii [FORGE](https://github.com/fsharp-editing/Forge) projektu.</span><span class="sxs-lookup"><span data-stu-id="f698b-131">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
<span data-ttu-id="f698b-132">Pokud nevidíte šablonu možnosti, aktualizujte šablony spuštěním následujícího příkazu v příkazu palety: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="f698b-132">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="f698b-133">Vyberte "F #: nový projekt" zasažení **Enter**.</span><span class="sxs-lookup"><span data-stu-id="f698b-133">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="f698b-134">Tím přejdete k dalšímu kroku, který je pro výběr šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="f698b-134">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="f698b-135">Vyberte `classlib` šablony a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="f698b-135">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="f698b-136">V dalším kroku vyberte adresář pro vytvoření projektu v.</span><span class="sxs-lookup"><span data-stu-id="f698b-136">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="f698b-137">Pokud pole ponecháte prázdné, použije se aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="f698b-137">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="f698b-138">Nakonec název projektu v posledním kroku.</span><span class="sxs-lookup"><span data-stu-id="f698b-138">Finally, name your project in the final step.</span></span> <span data-ttu-id="f698b-139">F # používá [pascalcase](http://c2.com/cgi/wiki?PascalCase) pro názvy projektů.</span><span class="sxs-lookup"><span data-stu-id="f698b-139">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="f698b-140">Tento článek používá `ClassLibraryDemo` jako název.</span><span class="sxs-lookup"><span data-stu-id="f698b-140">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="f698b-141">Po zadání názvu, který chcete pro svůj projekt, stiskněte tlačítko **Enter**.</span><span class="sxs-lookup"><span data-stu-id="f698b-141">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="f698b-142">Pokud jste postupovali podle předchozího kroku, měli byste obdržet Visual Studio Code pracovní prostor na levé straně a zobrazují se následující:</span><span class="sxs-lookup"><span data-stu-id="f698b-142">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="f698b-143">F # projektu samostatně, pod `ClassLibraryDemo` složky.</span><span class="sxs-lookup"><span data-stu-id="f698b-143">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="f698b-144">Správnou adresářovou strukturu pro přidávání balíčků prostřednictvím [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="f698b-144">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="f698b-145">Napříč platformami sestavení skriptu s [ `FAKE` ](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="f698b-145">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="f698b-146">`paket.exe` Spustitelný soubor, který můžete načíst balíčky a vyřešit závislosti pro vás.</span><span class="sxs-lookup"><span data-stu-id="f698b-146">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="f698b-147">A `.gitignore` soubor, pokud chcete přidat tento projekt na základě Git zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f698b-147">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="f698b-148">Zápis některých kódu</span><span class="sxs-lookup"><span data-stu-id="f698b-148">Writing some code</span></span>

<span data-ttu-id="f698b-149">Otevřete *ClassLibraryDemo* složky.</span><span class="sxs-lookup"><span data-stu-id="f698b-149">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="f698b-150">Měli byste vidět následující soubory:</span><span class="sxs-lookup"><span data-stu-id="f698b-150">You should see the following files:</span></span>

1. <span data-ttu-id="f698b-151">`ClassLibraryDemo.fs`, F # implementace souboru třídy definované.</span><span class="sxs-lookup"><span data-stu-id="f698b-151">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="f698b-152">`ClassLibraryDemo.fsproj`, F # souboru projektu aplikace sloužící k vytvoření tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="f698b-152">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="f698b-153">`Script.fsx`, F # skript soubor, který načte zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="f698b-153">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="f698b-154">`paket.references`, stáhnout soubor, který určuje závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="f698b-154">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="f698b-155">Otevřete `Script.fsx`a přidejte následující kód na konci ho:</span><span class="sxs-lookup"><span data-stu-id="f698b-155">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="f698b-156">Tato funkce převede slovo forma [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="f698b-156">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="f698b-157">Dalším krokem je vyhodnotit pomocí F # interaktivní (FSI).</span><span class="sxs-lookup"><span data-stu-id="f698b-157">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="f698b-158">Zvýrazněte celý funkce (by měl být dlouhý 11 řádky).</span><span class="sxs-lookup"><span data-stu-id="f698b-158">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="f698b-159">Jakmile se zvýrazní, podržte **Alt** klíče a počtu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="f698b-159">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="f698b-160">Můžete si všimnout okno otevíraném níže a jeho by měl zobrazit přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="f698b-160">You'll notice a window pop up below, and it should show something like this:</span></span>

![Příklad výstupu F # interaktivní s Ionide](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="f698b-162">To provedl tři věci:</span><span class="sxs-lookup"><span data-stu-id="f698b-162">This did three things:</span></span>

1. <span data-ttu-id="f698b-163">Spuštění procesu FSI.</span><span class="sxs-lookup"><span data-stu-id="f698b-163">It started the FSI process.</span></span>
2. <span data-ttu-id="f698b-164">Vámi vybraný úsek zvýrazněný kód se odešlou přes FSI proces.</span><span class="sxs-lookup"><span data-stu-id="f698b-164">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="f698b-165">Proces FSI vyhodnotí kód, který jste odeslali přes.</span><span class="sxs-lookup"><span data-stu-id="f698b-165">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="f698b-166">Protože odeslané přes [funkce](../language-reference/functions/index.md), můžete nyní volání této funkce se FSI!</span><span class="sxs-lookup"><span data-stu-id="f698b-166">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="f698b-167">V okně interaktivní zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f698b-167">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="f698b-168">Měli byste vidět následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="f698b-168">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="f698b-169">Nyní zkuste to prosím ještě s samohláskou jako první písmeno.</span><span class="sxs-lookup"><span data-stu-id="f698b-169">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="f698b-170">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f698b-170">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="f698b-171">Měli byste vidět následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="f698b-171">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="f698b-172">Zdá se, že funkce fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="f698b-172">The function appears to be working as expected.</span></span> <span data-ttu-id="f698b-173">Blahopřejeme, stačí napsali první funkce F # ve Visual Studio Code a vyhodnotit s FSI.</span><span class="sxs-lookup"><span data-stu-id="f698b-173">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="f698b-174">Protože jste si všimli, jsou řádky v FSI byla ukončena s `;;`.</span><span class="sxs-lookup"><span data-stu-id="f698b-174">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="f698b-175">To je proto FSI umožňuje zadat více řádků.</span><span class="sxs-lookup"><span data-stu-id="f698b-175">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="f698b-176">`;;` Na konci umožňuje FSI vědět, kdy je dokončena kód.</span><span class="sxs-lookup"><span data-stu-id="f698b-176">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="f698b-177">Vysvětlení kód</span><span class="sxs-lookup"><span data-stu-id="f698b-177">Explaining the code</span></span>

<span data-ttu-id="f698b-178">Pokud si nejste si jisti, co kód ve skutečnosti provádí, zde je krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="f698b-178">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="f698b-179">Jak vidíte, `toPigLatin` je funkce, která přebírá slovo jako vstup a převede jej na znázornění Pig Latin tohoto slova.</span><span class="sxs-lookup"><span data-stu-id="f698b-179">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="f698b-180">Pravidla pro toto jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f698b-180">The rules for this are as follows:</span></span>

<span data-ttu-id="f698b-181">Pokud první znak v slovo začíná samohláskou, přidejte na konec slovo "yay".</span><span class="sxs-lookup"><span data-stu-id="f698b-181">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="f698b-182">Pokud se nespustí, s samohláskou, přesuňte tento první znak ke konci slova a přidejte do ní "ay".</span><span class="sxs-lookup"><span data-stu-id="f698b-182">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="f698b-183">Může dojít k tomu následující FSI:</span><span class="sxs-lookup"><span data-stu-id="f698b-183">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="f698b-184">To stavů, které `toPigLatin` je funkce, která přebírá `string` jako vstup (nazývá `word`) a vrátí jiné `string`.</span><span class="sxs-lookup"><span data-stu-id="f698b-184">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="f698b-185">To se označuje jako [podpis typu funkce](https://fsharpforfunandprofit.com/posts/function-signatures/), základní část F #, která je klíčem k pochopení F # – kód.</span><span class="sxs-lookup"><span data-stu-id="f698b-185">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="f698b-186">Tento postup můžete si všimnout také v Pokud najedete funkci v aplikaci Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f698b-186">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="f698b-187">V těle funkce můžete si všimnout dvou různých částí:</span><span class="sxs-lookup"><span data-stu-id="f698b-187">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="f698b-188">Vnitřní funkce, nazývá `isVowel`, která určuje, zda daného znaku (`c`) je samohláskou kontrolou, pokud odpovídá jednomu vzoru zadaný prostřednictvím [porovnávání vzorů](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="f698b-188">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="f698b-189">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Výraz, který zkontroluje, zda je první znak samohláskou a konstrukce vrátí hodnotu mimo vstupní znaky na základě-li první znak byla samohláskou nebo ne:</span><span class="sxs-lookup"><span data-stu-id="f698b-189">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="f698b-190">Tok `toPigLatin` proto:</span><span class="sxs-lookup"><span data-stu-id="f698b-190">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="f698b-191">Zkontrolujte, jestli je první znak vstupní slovo samohláskou.</span><span class="sxs-lookup"><span data-stu-id="f698b-191">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="f698b-192">Je-li, připojte na konec slovo "yay".</span><span class="sxs-lookup"><span data-stu-id="f698b-192">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="f698b-193">Jinak přesuňte tento první znak ke konci slova a do ní přidejte "ay".</span><span class="sxs-lookup"><span data-stu-id="f698b-193">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="f698b-194">Neexistuje jeden konečné si všimněte o to: neexistuje žádné explicitní instrukce k návratu z funkce, na rozdíl od mnoha dalších jazycích odhlašování došlo.</span><span class="sxs-lookup"><span data-stu-id="f698b-194">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="f698b-195">Je to proto F # je založené na výrazu a poslední výrazů v těle funkce je návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f698b-195">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="f698b-196">Protože `if..then..else` je sám výraz text `then` bloku nebo textu `else` bloku bude vrácen v závislosti na vstupní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f698b-196">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="f698b-197">Přesunutí kód skriptu do souboru implementace</span><span class="sxs-lookup"><span data-stu-id="f698b-197">Moving your script code into the implementation file</span></span>

<span data-ttu-id="f698b-198">V předchozích částech v tomto článku ukázán běžné prvním krokem při psaní kódu F #: psaní počáteční funkce a provádění interaktivně s FSI.</span><span class="sxs-lookup"><span data-stu-id="f698b-198">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="f698b-199">To se označuje jako REPL řízený vývoj, kde [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) znamená "Pro čtení vyhodnotit tiskových smyčka".</span><span class="sxs-lookup"><span data-stu-id="f698b-199">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="f698b-200">Je skvělým způsobem, jak experimentovat s funkcemi, dokud něco práce.</span><span class="sxs-lookup"><span data-stu-id="f698b-200">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="f698b-201">Dalším krokem v vývoje řízeného REPL je přesunout funkční kód do souboru implementace F #.</span><span class="sxs-lookup"><span data-stu-id="f698b-201">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="f698b-202">Ho můžete pak zkompilovat pomocí kompilátor jazyka F # do sestavení, které mohou být provedeny.</span><span class="sxs-lookup"><span data-stu-id="f698b-202">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="f698b-203">Chcete-li začít, otevřete `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="f698b-203">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="f698b-204">Můžete si všimnout, že některé kódu se již existuje.</span><span class="sxs-lookup"><span data-stu-id="f698b-204">You'll notice that some code is already in there.</span></span> <span data-ttu-id="f698b-205">Pokračujte a odstranit definice třídy, ale ponechte [ `namespace` ](../language-reference/namespaces.md) deklarace v horní části.</span><span class="sxs-lookup"><span data-stu-id="f698b-205">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="f698b-206">Dál vytvořte novou [ `module` ](../language-reference/modules.md) názvem `PigLatin` a zkopírujte `toPigLatin` funkce do ní takto:</span><span class="sxs-lookup"><span data-stu-id="f698b-206">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="f698b-207">Dále otevřete `Script.fsx` znovu a odstranit celý `toPigLatin` fungovat, ale ujistěte se, aby následující dva řádky v souboru:</span><span class="sxs-lookup"><span data-stu-id="f698b-207">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="f698b-208">První řádek je potřeba pro FSI skriptování načíst `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="f698b-208">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span> <span data-ttu-id="f698b-209">Druhý řádek je pro vaše pohodlí: ho vynechání je nepovinný, ale budete muset zadejte `open ClassLibraryDemo` v okně FSI Pokud chcete převést `ToPigLatin` modulu do oboru.</span><span class="sxs-lookup"><span data-stu-id="f698b-209">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="f698b-210">Potom v okně FSI volání funkce s `PigLatin` modul, který jste definovali dříve:</span><span class="sxs-lookup"><span data-stu-id="f698b-210">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="f698b-211">Úspěšné!</span><span class="sxs-lookup"><span data-stu-id="f698b-211">Success!</span></span> <span data-ttu-id="f698b-212">Stejné výsledky jako před, ale nyní načtena ze souboru implementace F #.</span><span class="sxs-lookup"><span data-stu-id="f698b-212">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="f698b-213">Hlavní rozdíl je, že jsou zdrojové soubory F # zkompilovány do sestavení, které mohou být provedeny kdekoli, ne jenom při FSI.</span><span class="sxs-lookup"><span data-stu-id="f698b-213">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="f698b-214">Souhrn</span><span class="sxs-lookup"><span data-stu-id="f698b-214">Summary</span></span>

<span data-ttu-id="f698b-215">V tomto článku když jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="f698b-215">In this article, you've learned:</span></span>

1. <span data-ttu-id="f698b-216">Jak nastavit Visual Studio Code s Ionide.</span><span class="sxs-lookup"><span data-stu-id="f698b-216">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="f698b-217">Jak vytvořit svůj první projekt F # s Ionide.</span><span class="sxs-lookup"><span data-stu-id="f698b-217">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="f698b-218">Jak používat F # skriptování k zápisu první funkce F # v Ionide a potom spusťte v FSI.</span><span class="sxs-lookup"><span data-stu-id="f698b-218">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="f698b-219">Postup migrace vašeho skriptu Chcete-li F # zdrojový kód a potom tento kód volat z FSI.</span><span class="sxs-lookup"><span data-stu-id="f698b-219">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="f698b-220">Jste nyní vybavený napsat mnohem víc kód F # pomocí sady Visual Studio Code a Ionide.</span><span class="sxs-lookup"><span data-stu-id="f698b-220">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="f698b-221">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="f698b-221">Troubleshooting</span></span>

<span data-ttu-id="f698b-222">Můžete řešit určité problémy, které můžete narazit na několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="f698b-222">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="f698b-223">Získat kód funkce Ionide úprav, měly být uloženy na disk a uvnitř složky, která je otevřený v pracovním prostoru Visual Studio Code soubory F #.</span><span class="sxs-lookup"><span data-stu-id="f698b-223">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="f698b-224">Pokud jste provedené změny v systému nebo nainstalované s Visual Studio Code otevřete Ionide požadavky, restartujte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f698b-224">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="f698b-225">Zkontrolujte, že můžete kompilátor jazyka F # a F # interaktivní z příkazového řádku bez plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="f698b-225">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="f698b-226">To lze provést zadáním `fsc` v příkazovém řádku pro kompilátor F # a `fsi` nebo `fsharpi` pro Visual F # nástrojů v systému Windows a Mono na Mac/Linux, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f698b-226">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="f698b-227">Pokud projekt adresáře obsahuje neplatné znaky, Ionide nemusí fungovat.</span><span class="sxs-lookup"><span data-stu-id="f698b-227">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="f698b-228">Pokud se jedná o tento případ, přejmenování adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="f698b-228">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="f698b-229">Pokud žádná z příkazy Ionide pracují, zkontrolujte vaše [klíčových vazeb Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) chcete zobrazit, pokud jste se jejich přepsání omylem odstraněný.</span><span class="sxs-lookup"><span data-stu-id="f698b-229">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="f698b-230">Pokud Ionide je rozděleno na váš počítač a žádná z výše má pevnou váš problém, zkuste odebrat `ionide-fsharp` adresář na váš počítač a znovu nainstalujte modul plug-in.</span><span class="sxs-lookup"><span data-stu-id="f698b-230">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="f698b-231">Ionide je opensourcový projekt vytvořené a spravují členové komunity F #.</span><span class="sxs-lookup"><span data-stu-id="f698b-231">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="f698b-232">Zkontrolujte hlášení problémů a Nebojte se přispět na [Ionide VSCode: úložiště FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="f698b-232">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="f698b-233">Pokud máte potíže do sestavy, postupujte podle [pokyny pro získání protokolů vykazování problém](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="f698b-233">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="f698b-234">Můžete také požádat o další pomoc z Ionide vývojáři a F # komunity v [Ionide Gitter kanál](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="f698b-234">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f698b-235">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f698b-235">Next steps</span></span>

<span data-ttu-id="f698b-236">Další informace o F # a funkce jazyka, podívejte se na [prohlídka z F #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="f698b-236">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

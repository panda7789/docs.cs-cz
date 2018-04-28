---
title: 'Začínáme s F # v sadě Visual Studio kódu'
description: 'Další informace o použití F # s Visual Studio Code a suite Ionide modulu plug-in.'
author: cartermp
ms.author: phcart
ms.date: 02/28/2018
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 43fed76a57bd7749a7f22a2039ad625e3d26d132
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="84f14-103">Začínáme s F # v sadě Visual Studio kódu</span><span class="sxs-lookup"><span data-stu-id="84f14-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="84f14-104">Můžete napsat F # [Visual Studio Code](https://code.visualstudio.com) s [modulu plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), abyste získali optimálního uživatelského prostředí IDE (Integrade vývoj Enivronment) a platformy, lightweight s IntelliSense a základní kódu refaktoring.</span><span class="sxs-lookup"><span data-stu-id="84f14-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight IDE (Integrade Development Enivronment) experience with IntelliSense and basic code refactorings.</span></span>  <span data-ttu-id="84f14-105">Navštivte [Ionide.io](http://ionide.io) Další informace o sadě modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="84f14-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="84f14-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84f14-106">Prerequisites</span></span>

<span data-ttu-id="84f14-107">Musíte mít [nainstalovat git](https://git-scm.com/download) a k dispozici na CESTU ke zkontrolujte pomocí šablon projektu v Ionide.</span><span class="sxs-lookup"><span data-stu-id="84f14-107">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span>  <span data-ttu-id="84f14-108">Můžete ověřit, zda je správně nainstalován zadáním `git --version` v příkazovém řádku a stiskněte **Enter**.</span><span class="sxs-lookup"><span data-stu-id="84f14-108">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="84f14-109">macOS</span><span class="sxs-lookup"><span data-stu-id="84f14-109">macOS</span></span>](#tab/macos)

<span data-ttu-id="84f14-110">Používá Ionide [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="84f14-110">Ionide uses [Mono](http://www.mono-project.com).</span></span>  <span data-ttu-id="84f14-111">Nejjednodušší způsob, jak nainstalovat Mono v systému macOS je prostřednictvím Homebrew.</span><span class="sxs-lookup"><span data-stu-id="84f14-111">The easiest way to install Mono on macOS is via Homebrew.</span></span>  <span data-ttu-id="84f14-112">Jednoduše zadejte do terminálu následující:</span><span class="sxs-lookup"><span data-stu-id="84f14-112">Simply type the following into your terminal:</span></span>

```
brew install mono
```

<span data-ttu-id="84f14-113">Je také nutné nainstalovat [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="84f14-113">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="84f14-114">Linux</span><span class="sxs-lookup"><span data-stu-id="84f14-114">Linux</span></span>](#tab/linux)

<span data-ttu-id="84f14-115">V systému Linux, Ionide také používá [Mono](https://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="84f14-115">On Linux, Ionide also uses [Mono](https://www.mono-project.com).</span></span> <span data-ttu-id="84f14-116">Pokud jste na Debian a Ubuntu, můžete použít následující:</span><span class="sxs-lookup"><span data-stu-id="84f14-116">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="84f14-117">Je také nutné nainstalovat [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="84f14-117">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="84f14-118">Windows</span><span class="sxs-lookup"><span data-stu-id="84f14-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="84f14-119">Pokud jste v systému Windows, musíte [instalaci sady Visual Studio s podporou F #](get-started-visual-studio.md#installing-f).</span><span class="sxs-lookup"><span data-stu-id="84f14-119">If you're on Windows, you must [install Visual Studio with F# support](get-started-visual-studio.md#installing-f).</span></span> <span data-ttu-id="84f14-120">Tím se nainstaluje všechny komponenty potřebné k zápisu, zkompilování a spuštění kódu F #.</span><span class="sxs-lookup"><span data-stu-id="84f14-120">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="84f14-121">Je také nutné nainstalovat [.NET Core SDK](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="84f14-121">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="84f14-122">Instalace Visual Studio Code a Ionide modulu plug-in</span><span class="sxs-lookup"><span data-stu-id="84f14-122">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="84f14-123">Můžete nainstalovat Visual Studio Code z [code.visualstudio.com](https://code.visualstudio.com) webu.</span><span class="sxs-lookup"><span data-stu-id="84f14-123">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span> <span data-ttu-id="84f14-124">Potom existují dva způsoby jak najít modul plug-in Ionide:</span><span class="sxs-lookup"><span data-stu-id="84f14-124">After that, there are two ways to find the Ionide plugin:</span></span>

1. <span data-ttu-id="84f14-125">Použijte příkaz palety (Ctrl + Shift + P v systému Windows, ⌘ + Shift + P v systému macOS, Ctrl + Shift + P v systému Linux) a zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="84f14-125">Use the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

    ```
    >ext install Ionide
    ```

2. <span data-ttu-id="84f14-126">Klikněte na ikonu rozšíření a vyhledejte "Ionide":</span><span class="sxs-lookup"><span data-stu-id="84f14-126">Click the Extensions icon and search for "Ionide":</span></span>

    ![](media/getting-started-vscode/vscode-ext.png)

<span data-ttu-id="84f14-127">Pouze modul plug-in, které jsou potřebné pro podporu F # ve Visual Studio Code je [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="84f14-127">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="84f14-128">Ale můžete taky nainstalovat [Ionide PHISHING](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) a získat [ZFALŠOVAT](https://fsharp.github.io/FAKE/) podporu a [Ionide Stáhnout](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) získat [Stáhnout](https://fsprojects.github.io/Paket/) podporovat.</span><span class="sxs-lookup"><span data-stu-id="84f14-128">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) and to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="84f14-129">ZFALŠOVAT a stáhnout dalších F # komunity nástroje pro sestavení projektů a správu závislosti, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="84f14-129">FAKE and Paket are additonal F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="84f14-130">Vytvoření prvního projektu s Ionide</span><span class="sxs-lookup"><span data-stu-id="84f14-130">Creating your first project with Ionide</span></span>

<span data-ttu-id="84f14-131">Pokud chcete vytvořit nový projekt F #, otevřete Visual Studio Code do nové složky (můžete pojmenovat se vám líbí).</span><span class="sxs-lookup"><span data-stu-id="84f14-131">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

![](media/getting-started-vscode/vscode-open-dir.png)

<span data-ttu-id="84f14-132">Dále otevřete příkaz palety (Ctrl + Shift + P v systému Windows, ⌘ + Shift + P v systému macOS, Ctrl + Shift + P v systému Linux) a zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="84f14-132">Next, open the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

```
>f#: New Project
```

<span data-ttu-id="84f14-133">To používá technologii [FORGE](https://github.com/fsharp-editing/Forge) projektu.</span><span class="sxs-lookup"><span data-stu-id="84f14-133">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>  <span data-ttu-id="84f14-134">Měli byste vidět zhruba takhle:</span><span class="sxs-lookup"><span data-stu-id="84f14-134">You should see something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
<span data-ttu-id="84f14-135">Pokud nevidíte výše, aktualizujte šablony spuštěním následujícího příkazu v příkazu palety: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="84f14-135">If you don't see the above, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="84f14-136">Vyberte "F #: nový projekt" zasažení **Enter**, který se dostanete k tomuto kroku:</span><span class="sxs-lookup"><span data-stu-id="84f14-136">Select "F#: New Project" by hitting **Enter**, which will take you to this step:</span></span>

![](media/getting-started-vscode/vscode-proj-type.png)

<span data-ttu-id="84f14-137">To bude vyberte šablonu pro konkrétní typ projektu.</span><span class="sxs-lookup"><span data-stu-id="84f14-137">This will select a template for a specific type of project.</span></span>  <span data-ttu-id="84f14-138">Existuje zde několik možností, jako [FsLab](https://fslab.org) šablonu pro vědecké zpracování dat nebo [Suave](https://suave.io) šablonu pro webové programování.</span><span class="sxs-lookup"><span data-stu-id="84f14-138">There are quite a few options here, such as an [FsLab](https://fslab.org) template for Data Science or [Suave](https://suave.io) template for Web Programming.</span></span>  <span data-ttu-id="84f14-139">Tento článek používá `classlib` šablony, takže zvýrazněte a stiskněte tlačítko **Enter**.</span><span class="sxs-lookup"><span data-stu-id="84f14-139">This article uses the `classlib` template, so highlight that and hit **Enter**.</span></span>  <span data-ttu-id="84f14-140">Potom bude přístup následující krok:</span><span class="sxs-lookup"><span data-stu-id="84f14-140">You will then reach the following step:</span></span>

![](media/getting-started-vscode/vscode-new-dir.png)

<span data-ttu-id="84f14-141">To vám umožní vytvořit projekt v jiném adresáři, pokud chcete.</span><span class="sxs-lookup"><span data-stu-id="84f14-141">This lets you create the project in a different directory, if you like.</span></span>  <span data-ttu-id="84f14-142">Necháte prázdné, teď.</span><span class="sxs-lookup"><span data-stu-id="84f14-142">Leave it blank for now.</span></span>  <span data-ttu-id="84f14-143">Vytvoří projekt v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="84f14-143">It will create the project in the current directory.</span></span>  <span data-ttu-id="84f14-144">Po stisknutí klávesy **Enter**, nedostanete následující krok:</span><span class="sxs-lookup"><span data-stu-id="84f14-144">Once you press **Enter**, you will reach the following step:</span></span>

![](media/getting-started-vscode/vscode-proj-name.png)

<span data-ttu-id="84f14-145">Díky tomu můžete název projektu.</span><span class="sxs-lookup"><span data-stu-id="84f14-145">This lets you name your project.</span></span>  <span data-ttu-id="84f14-146">F # používá [pascalcase](http://c2.com/cgi/wiki?PascalCase) pro názvy projektů.</span><span class="sxs-lookup"><span data-stu-id="84f14-146">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span>  <span data-ttu-id="84f14-147">Tento článek používá `ClassLibraryDemo` jako název.</span><span class="sxs-lookup"><span data-stu-id="84f14-147">This article uses `ClassLibraryDemo` as the name.</span></span>  <span data-ttu-id="84f14-148">Po zadání názvu, který chcete pro svůj projekt, stiskněte tlačítko **Enter**.</span><span class="sxs-lookup"><span data-stu-id="84f14-148">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="84f14-149">Pokud jste postupovali podle předchozích kroků krok, měli byste obdržet Visual Studio Code pracovní prostor na levé straně a vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="84f14-149">If you followed the previous step steps, you should get the Visual Studio Code Workspace on the left-hand side to look something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

<span data-ttu-id="84f14-150">Tato šablona vytváří několik věcí, které budete užitečné:</span><span class="sxs-lookup"><span data-stu-id="84f14-150">This template generates a few things you'll find useful:</span></span>

1. <span data-ttu-id="84f14-151">F # projektu samostatně, pod `ClassLibraryDemo` složky.</span><span class="sxs-lookup"><span data-stu-id="84f14-151">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="84f14-152">Správnou adresářovou strukturu pro přidávání balíčků prostřednictvím [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="84f14-152">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="84f14-153">Napříč platformami sestavení skriptu s [ `FAKE` ](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="84f14-153">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="84f14-154">`paket.exe` Spustitelný soubor, který může načíst balíčky a vyřešení závislostí pro vás.</span><span class="sxs-lookup"><span data-stu-id="84f14-154">The `paket.exe` executable which can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="84f14-155">A `.gitignore` soubor, pokud chcete přidat tento projekt na základě Git zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="84f14-155">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="84f14-156">Zápis některých kódu</span><span class="sxs-lookup"><span data-stu-id="84f14-156">Writing some code</span></span>

<span data-ttu-id="84f14-157">Otevřete *ClassLibraryDemo* složky.</span><span class="sxs-lookup"><span data-stu-id="84f14-157">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="84f14-158">Měli byste vidět následující soubory:</span><span class="sxs-lookup"><span data-stu-id="84f14-158">You should see the following files:</span></span>

1. <span data-ttu-id="84f14-159">`ClassLibraryDemo.fs`, F # implementace souboru třídy definované.</span><span class="sxs-lookup"><span data-stu-id="84f14-159">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="84f14-160">`CassLibraryDemo.fsproj`, F # souboru projektu aplikace sloužící k vytvoření tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="84f14-160">`CassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="84f14-161">`Script.fsx`, F # skript soubor který načte zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="84f14-161">`Script.fsx`, an F# script file which loads the source file.</span></span>
4. <span data-ttu-id="84f14-162">`paket.references`, stáhnout soubor, který určuje závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="84f14-162">`paket.references`, a Paket file which specifies the project dependencies.</span></span>

<span data-ttu-id="84f14-163">Otevřete `Script.fsx`a přidejte následující kód na konci ho:</span><span class="sxs-lookup"><span data-stu-id="84f14-163">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="84f14-164">Tato funkce převede slovo forma [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="84f14-164">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span>  <span data-ttu-id="84f14-165">Dalším krokem je vyhodnotit pomocí F # interaktivní (FSI).</span><span class="sxs-lookup"><span data-stu-id="84f14-165">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="84f14-166">Zvýrazněte celý funkce (by měl být dlouhý 11 řádky).</span><span class="sxs-lookup"><span data-stu-id="84f14-166">Highlight the entire function (it should be 11 lines long).</span></span>  <span data-ttu-id="84f14-167">Jakmile se zvýrazní, podržte **Alt** klíče a počtu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="84f14-167">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span>  <span data-ttu-id="84f14-168">Můžete si všimnout okno otevíraném níže a jeho by měl zobrazit přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="84f14-168">You'll notice a window pop up below, and it should show something like this:</span></span>

![](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="84f14-169">To provedl tři věci:</span><span class="sxs-lookup"><span data-stu-id="84f14-169">This did three things:</span></span>

1. <span data-ttu-id="84f14-170">Spuštění procesu FSI.</span><span class="sxs-lookup"><span data-stu-id="84f14-170">It started the FSI process.</span></span>
2. <span data-ttu-id="84f14-171">Vámi vybraný úsek zvýrazněný kód se odešlou přes FSI proces.</span><span class="sxs-lookup"><span data-stu-id="84f14-171">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="84f14-172">Proces FSI vyhodnotí kód, který jste odeslali přes.</span><span class="sxs-lookup"><span data-stu-id="84f14-172">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="84f14-173">Protože odeslané přes [funkce](../language-reference/functions/index.md), můžete nyní volání této funkce se FSI!</span><span class="sxs-lookup"><span data-stu-id="84f14-173">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span>  <span data-ttu-id="84f14-174">V okně interaktivní zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="84f14-174">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="84f14-175">Měli byste vidět následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="84f14-175">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="84f14-176">Nyní zkuste to prosím ještě s samohláskou jako první písmeno.</span><span class="sxs-lookup"><span data-stu-id="84f14-176">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="84f14-177">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="84f14-177">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="84f14-178">Měli byste vidět následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="84f14-178">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="84f14-179">Zdá se, že funkce fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="84f14-179">The function appears to be working as expected.</span></span>  <span data-ttu-id="84f14-180">Blahopřejeme, stačí napsali první funkce F # ve Visual Studio Code a vyhodnotit s FSI.</span><span class="sxs-lookup"><span data-stu-id="84f14-180">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="84f14-181">Protože jste si všimli, jsou řádky v FSI byla ukončena s `;;`.</span><span class="sxs-lookup"><span data-stu-id="84f14-181">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span>  <span data-ttu-id="84f14-182">To je proto FSI umožňuje zadat více řádků.</span><span class="sxs-lookup"><span data-stu-id="84f14-182">This is because FSI allows you to enter multiple lines.</span></span>  <span data-ttu-id="84f14-183">`;;` Na konci umožňuje FSI vědět, kdy je dokončena kód.</span><span class="sxs-lookup"><span data-stu-id="84f14-183">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="84f14-184">Vysvětlení kód</span><span class="sxs-lookup"><span data-stu-id="84f14-184">Explaining the code</span></span>

<span data-ttu-id="84f14-185">Pokud si nejste si jisti, co kód ve skutečnosti provádí, zde je krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="84f14-185">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="84f14-186">Jak vidíte, `toPigLatin` je funkce, která přebírá slovo jako vstup a převede jej na znázornění Pig Latin tohoto slova.</span><span class="sxs-lookup"><span data-stu-id="84f14-186">As you can see, `toPigLatin` is a function which takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span>  <span data-ttu-id="84f14-187">Pravidla pro toto jsou následující:</span><span class="sxs-lookup"><span data-stu-id="84f14-187">The rules for this are as follows:</span></span>

<span data-ttu-id="84f14-188">Pokud první znak v slovo začíná samohláskou, přidejte na konec slovo "yay".</span><span class="sxs-lookup"><span data-stu-id="84f14-188">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span>  <span data-ttu-id="84f14-189">Pokud se nespustí, s samohláskou, přesuňte tento první znak ke konci slova a přidejte do ní "ay".</span><span class="sxs-lookup"><span data-stu-id="84f14-189">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="84f14-190">Může dojít k tomu následující FSI:</span><span class="sxs-lookup"><span data-stu-id="84f14-190">You may have noticed the following in FSI:</span></span>

```
val toPigLatin : word:string -> string
```

<span data-ttu-id="84f14-191">To stavů, které `toPigLatin` je funkce, která přebírá `string` jako vstup (nazývá `word`) a vrátí jiné `string`.</span><span class="sxs-lookup"><span data-stu-id="84f14-191">This states that `toPigLatin` is a function which takes in a `string` as input (called `word`), and returns another `string`.</span></span>  <span data-ttu-id="84f14-192">To se označuje jako [podpis typu funkce](https://fsharpforfunandprofit.com/posts/function-signatures/), základní část F #, která je klíčem k pochopení F # – kód.</span><span class="sxs-lookup"><span data-stu-id="84f14-192">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span>  <span data-ttu-id="84f14-193">Tento postup můžete si všimnout také v Pokud najedete funkci v aplikaci Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="84f14-193">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="84f14-194">V těle funkce můžete si všimnout dvou různých částí:</span><span class="sxs-lookup"><span data-stu-id="84f14-194">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="84f14-195">Vnitřní funkce, nazývá `isVowel`, která určuje, zda daného znaku (`c`) je samohláskou kontrolou, pokud odpovídá jednomu vzoru zadaný prostřednictvím [porovnávání vzorů](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="84f14-195">An inner function, called `isVowel`, which determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="84f14-196">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Výrazu, které ověří, zda je první znak je samohláskou a vytvoří návratovou hodnotu mimo vstupní znaky na základě-li první znak byla samohláskou nebo ne:</span><span class="sxs-lookup"><span data-stu-id="84f14-196">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression which checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="84f14-197">Tok `toPigLatin` proto:</span><span class="sxs-lookup"><span data-stu-id="84f14-197">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="84f14-198">Zkontrolujte, jestli je první znak vstupní slovo samohláskou.</span><span class="sxs-lookup"><span data-stu-id="84f14-198">Check if the first character of the input word is a vowel.</span></span>  <span data-ttu-id="84f14-199">Je-li, připojte na konec slovo "yay".</span><span class="sxs-lookup"><span data-stu-id="84f14-199">If it is, attach "yay" to the end of the word.</span></span>  <span data-ttu-id="84f14-200">Jinak přesuňte tento první znak ke konci slova a do ní přidejte "ay".</span><span class="sxs-lookup"><span data-stu-id="84f14-200">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="84f14-201">Neexistuje jeden konečné si všimněte o to: neexistuje žádné explicitní instrukce k návratu z funkce, na rozdíl od mnoha dalších jazycích odhlašování došlo.</span><span class="sxs-lookup"><span data-stu-id="84f14-201">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span>  <span data-ttu-id="84f14-202">Je to proto F # je založené na výrazu a poslední výrazů v těle funkce je návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="84f14-202">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span>  <span data-ttu-id="84f14-203">Protože `if..then..else` je sám výraz text `then` bloku nebo textu `else` bloku bude vrácen v závislosti na vstupní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="84f14-203">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="84f14-204">Přesunutí kód skriptu do souboru implementace</span><span class="sxs-lookup"><span data-stu-id="84f14-204">Moving your script code into the implementation file</span></span>

<span data-ttu-id="84f14-205">V předchozích částech v tomto článku ukázán běžné prvním krokem při psaní kódu F #: psaní počáteční funkce a provádění interaktivně s FSI.</span><span class="sxs-lookup"><span data-stu-id="84f14-205">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span>  <span data-ttu-id="84f14-206">To se označuje jako REPL řízený vývoj, kde REPL znamená "Pro čtení vyhodnotit tiskových smyčka".</span><span class="sxs-lookup"><span data-stu-id="84f14-206">This is known as REPL-driven development, where REPL stands for "Read-Evaluate-Print Loop".</span></span>  <span data-ttu-id="84f14-207">Je skvělým způsobem, jak experimentovat s funkcemi, dokud něco práce.</span><span class="sxs-lookup"><span data-stu-id="84f14-207">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="84f14-208">Dalším krokem v vývoje řízeného REPL je přesunout funkční kód do souboru implementace F #.</span><span class="sxs-lookup"><span data-stu-id="84f14-208">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span>  <span data-ttu-id="84f14-209">Ho můžete pak zkompilovat pomocí kompilátor jazyka F # do sestavení, které mohou být provedeny.</span><span class="sxs-lookup"><span data-stu-id="84f14-209">It can then be compiled by the F# compiler into an assembly which can be executed.</span></span>

<span data-ttu-id="84f14-210">Chcete-li začít, otevřete `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="84f14-210">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="84f14-211">Můžete si všimnout, že některé kódu se již existuje.</span><span class="sxs-lookup"><span data-stu-id="84f14-211">You'll notice that some code is already in there.</span></span>  <span data-ttu-id="84f14-212">Pokračujte a odstranit definice třídy, ale ponechte [ `namespace` ](../language-reference/namespaces.md) deklarace v horní části.</span><span class="sxs-lookup"><span data-stu-id="84f14-212">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="84f14-213">Dál vytvořte novou [ `module` ](../language-reference/modules.md) názvem `PigLatin` a zkopírujte `toPigLatin` funkce do ní takto:</span><span class="sxs-lookup"><span data-stu-id="84f14-213">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="84f14-214">Toto je jedna z mnoha způsoby, jak můžete uspořádat funkcí v F # – kód a běžný postup, pokud chcete také volání kódu z jazyka C# nebo projekty Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="84f14-214">This is one of the many ways you can organize functions in F# code, and a common approach if you also want to call your code from C# or Visual Basic projects.</span></span>

<span data-ttu-id="84f14-215">Dále otevřete `Script.fsx` znovu a odstranit celý `toPigLatin` fungovat, ale ujistěte se, aby následující dva řádky v souboru:</span><span class="sxs-lookup"><span data-stu-id="84f14-215">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="84f14-216">První řádek je potřeba pro FSI skriptování načíst `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="84f14-216">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="84f14-217">Druhý řádek je pro vaše pohodlí: ho vynechání je nepovinný, ale budete muset zadejte `open ClassLibraryDemo` v okně FSI Pokud chcete převést `ToPigLatin` modulu do oboru.</span><span class="sxs-lookup"><span data-stu-id="84f14-217">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="84f14-218">Potom v okně FSI volání funkce s `PigLatin` modul, který jste definovali dříve:</span><span class="sxs-lookup"><span data-stu-id="84f14-218">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="84f14-219">Úspěšné!</span><span class="sxs-lookup"><span data-stu-id="84f14-219">Success!</span></span>  <span data-ttu-id="84f14-220">Stejné výsledky jako před, ale nyní načtena ze souboru implementace F #.</span><span class="sxs-lookup"><span data-stu-id="84f14-220">You get the same results as before, but now loaded from an F# implementation file.</span></span>  <span data-ttu-id="84f14-221">Hlavní rozdíl je, že jsou zdrojové soubory F # zkompilovány do sestavení, které lze spustit kdekoliv a nikoli pouze v FSI.</span><span class="sxs-lookup"><span data-stu-id="84f14-221">The major difference here is that F# source files are compiled into assemblies which can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="84f14-222">Souhrn</span><span class="sxs-lookup"><span data-stu-id="84f14-222">Summary</span></span>

<span data-ttu-id="84f14-223">V tomto článku když jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="84f14-223">In this article, you've learned:</span></span>

1. <span data-ttu-id="84f14-224">Jak nastavit Visual Studio Code s Ionide.</span><span class="sxs-lookup"><span data-stu-id="84f14-224">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="84f14-225">Jak vytvořit svůj první projekt F # s Ionide.</span><span class="sxs-lookup"><span data-stu-id="84f14-225">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="84f14-226">Jak používat F # skriptování k zápisu první funkce F # v Ionide a potom spusťte v FSI.</span><span class="sxs-lookup"><span data-stu-id="84f14-226">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="84f14-227">Postup migrace vašeho skriptu Chcete-li F # zdrojový kód a potom tento kód volat z FSI.</span><span class="sxs-lookup"><span data-stu-id="84f14-227">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="84f14-228">Jste nyní vybavený napsat mnohem víc kód F # pomocí sady Visual Studio Code a Ionide.</span><span class="sxs-lookup"><span data-stu-id="84f14-228">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="84f14-229">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="84f14-229">Troubleshooting</span></span>

<span data-ttu-id="84f14-230">Můžete řešit určité problémy, které můžete narazit na několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="84f14-230">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="84f14-231">Získat kód funkce Ionide úprav, měly být uloženy na disk a uvnitř složky, která je otevřený v pracovním prostoru Visual Studio Code soubory F #.</span><span class="sxs-lookup"><span data-stu-id="84f14-231">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="84f14-232">Pokud jste provedené změny v systému nebo nainstalované s Visual Studio Code otevřete Ionide požadavky, restartujte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="84f14-232">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="84f14-233">Zkontrolujte, že můžete kompilátor jazyka F # a F # interaktivní z příkazového řádku bez plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="84f14-233">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span>  <span data-ttu-id="84f14-234">To lze provést zadáním `fsc` v příkazovém řádku pro kompilátor F # a `fsi` nebo `fsharpi` pro Visual F # nástrojů v systému Windows a Mono na Mac/Linux, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="84f14-234">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="84f14-235">Pokud projekt adresáře obsahuje neplatné znaky, Ionide nemusí fungovat.</span><span class="sxs-lookup"><span data-stu-id="84f14-235">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="84f14-236">Pokud se jedná o tento případ, přejmenování adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="84f14-236">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="84f14-237">Pokud žádná z příkazy Ionide pracují, zkontrolujte vaše [klíčových vazeb Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) chcete zobrazit, pokud jste se jejich přepsání omylem odstraněný.</span><span class="sxs-lookup"><span data-stu-id="84f14-237">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="84f14-238">Pokud Ionide je rozděleno na váš počítač a žádná z výše má pevnou váš problém, zkuste odebrat `ionide-fsharp` adresář na váš počítač a znovu nainstalujte modul plug-in.</span><span class="sxs-lookup"><span data-stu-id="84f14-238">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="84f14-239">Ionide je opensourcový projekt vytvořené a spravují členové komunity F #.</span><span class="sxs-lookup"><span data-stu-id="84f14-239">Ionide is an open source project built and maintained by members of the F# community.</span></span>  <span data-ttu-id="84f14-240">Zkontrolujte hlášení problémů a Nebojte se přispět na [Ionide VSCode: úložiště FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="84f14-240">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="84f14-241">Pokud máte potíže do sestavy, postupujte podle [pokyny pro získání protokolů vykazování problém](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="84f14-241">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="84f14-242">Můžete také požádat o další pomoc z Ionide vývojáři a F # komunity v [Ionide Gitter kanál](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="84f14-242">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="84f14-243">Další kroky</span><span class="sxs-lookup"><span data-stu-id="84f14-243">Next steps</span></span>

<span data-ttu-id="84f14-244">Další informace o F # a funkce jazyka, podívejte se na [prohlídka z F #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="84f14-244">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84f14-245">Viz také</span><span class="sxs-lookup"><span data-stu-id="84f14-245">See also</span></span>

[<span data-ttu-id="84f14-246">Prohlídka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="84f14-246">Tour of F#</span></span>](../tour.md)

[<span data-ttu-id="84f14-247">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="84f14-247">F# Language Reference</span></span>](../language-reference/index.md)

[<span data-ttu-id="84f14-248">Funkce</span><span class="sxs-lookup"><span data-stu-id="84f14-248">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="84f14-249">Moduly</span><span class="sxs-lookup"><span data-stu-id="84f14-249">Modules</span></span>](../language-reference/modules.md)

[<span data-ttu-id="84f14-250">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="84f14-250">Namespaces</span></span>](../language-reference/namespaces.md)

[<span data-ttu-id="84f14-251">Ionide VSCode: FSharp</span><span class="sxs-lookup"><span data-stu-id="84f14-251">Ionide-VSCode: FSharp</span></span>](https://github.com/ionide/ionide-vscode-fsharp)

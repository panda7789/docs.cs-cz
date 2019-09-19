---
title: Začínáme s nástrojem F# v Visual Studio Code
description: Naučte se používat F# s Visual Studio Code a sadou modulů plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 2fa0518488d37b2130aaba96028ac92dac77eb97
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082988"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="3c1e9-103">Začínáme s nástrojem F# v Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3c1e9-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="3c1e9-104">Můžete psát F# v [Visual Studio Code](https://code.visualstudio.com) s [modulem plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) a získat tak skvělé prostředí integrovaného vývojového prostředí (IDE) pro více platforem pomocí technologie IntelliSense a refaktoringu kódu Basic.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="3c1e9-105">Další informace o modulu plug-in najdete na [Ionide.IO](http://ionide.io) .</span><span class="sxs-lookup"><span data-stu-id="3c1e9-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="3c1e9-106">Chcete-li začít, ujistěte se, že máte [ F# a modul plug-in Ionide správně nainstalován](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="3c1e9-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

> [!NOTE]
> <span data-ttu-id="3c1e9-107">Ionide vygeneruje .NET Framework F# projekty, nikoli dotnet Core, což může mít problémy s kompatibilitou pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-107">Ionide will generate .NET Framework F# projects, not dotnet core, which can have cross-platform compatibility issues.</span></span> <span data-ttu-id="3c1e9-108">Pokud pracujete v systému **Linux** nebo **OSX**, jednodušší způsob, jak začít, je použít [nástroje příkazového řádku](get-started-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="3c1e9-108">If you are running on **Linux** or **OSX**, a simpler way to get started is to use the [command-line tools](get-started-command-line.md).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="3c1e9-109">Vytvoření prvního projektu pomocí Ionide</span><span class="sxs-lookup"><span data-stu-id="3c1e9-109">Creating your first project with Ionide</span></span>

<span data-ttu-id="3c1e9-110">Chcete-li vytvořit F# nový projekt, otevřete Visual Studio Code v nové složce (můžete si ho pojmenovat podle vaší věci).</span><span class="sxs-lookup"><span data-stu-id="3c1e9-110">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="3c1e9-111">V dalším kroku otevřete paletu příkazů (**zobrazit > paleta příkazů**) a zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-111">Next, open the command palette (**View > Command Palette**) and type the following:</span></span>

```console
> F# new project
```

<span data-ttu-id="3c1e9-112">Používá se v projektu [zfalšovat](https://github.com/fsharp-editing/Forge) .</span><span class="sxs-lookup"><span data-stu-id="3c1e9-112">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
> <span data-ttu-id="3c1e9-113">Pokud nevidíte možnosti šablony, zkuste aktualizace šablon spustit pomocí následujícího příkazu v paletě příkazů: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-113">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="3c1e9-114">VyberteF#: Nový projekt "pomocí možnosti **ENTER**</span><span class="sxs-lookup"><span data-stu-id="3c1e9-114">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="3c1e9-115">Tím přejdete k dalšímu kroku, který je určen pro výběr šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-115">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="3c1e9-116">Vyberte šablonu a stiskněte klávesu **ENTER.** `classlib`</span><span class="sxs-lookup"><span data-stu-id="3c1e9-116">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="3c1e9-117">Pak vyberte adresář, ve kterém se má projekt vytvořit.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-117">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="3c1e9-118">Pokud ponecháte pole prázdné, použije se aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-118">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="3c1e9-119">Nakonec pojmenujte projekt v posledním kroku.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-119">Finally, name your project in the final step.</span></span> <span data-ttu-id="3c1e9-120">F#pro názvy projektů používá [velká písmena jazyka Pascal](http://c2.com/cgi/wiki?PascalCase) .</span><span class="sxs-lookup"><span data-stu-id="3c1e9-120">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="3c1e9-121">Tento článek používá `ClassLibraryDemo` název.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-121">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="3c1e9-122">Až zadáte název, který chcete pro svůj projekt, stiskněte klávesu **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-122">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="3c1e9-123">Pokud jste postupovali podle předchozího kroku, měli byste na levé straně získat Visual Studio Code pracovní prostor, aby se zobrazila následující:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-123">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="3c1e9-124">Samotný F# projekt pod `ClassLibraryDemo` složkou.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-124">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="3c1e9-125">Správná adresářová struktura pro přidávání balíčků prostřednictvím [`Paket`](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="3c1e9-125">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="3c1e9-126">Skript sestavení pro různé platformy s [`FAKE`](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="3c1e9-126">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="3c1e9-127">`paket.exe` Spustitelný soubor, který dokáže načíst balíčky a vyřešit závislosti.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-127">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="3c1e9-128">`.gitignore` Soubor, pokud chcete přidat tento projekt do správy zdrojového kódu založeného na Gitu.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-128">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="3c1e9-129">Psaní kódu</span><span class="sxs-lookup"><span data-stu-id="3c1e9-129">Writing some code</span></span>

<span data-ttu-id="3c1e9-130">Otevřete složku *ClassLibraryDemo* .</span><span class="sxs-lookup"><span data-stu-id="3c1e9-130">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="3c1e9-131">Měli byste vidět následující soubory:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-131">You should see the following files:</span></span>

1. <span data-ttu-id="3c1e9-132">`ClassLibraryDemo.fs`, F# implementační soubor s definovanou třídou.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-132">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="3c1e9-133">`ClassLibraryDemo.fsproj`, soubor F# projektu použitý k sestavení tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-133">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="3c1e9-134">`Script.fsx`, soubor F# skriptu, který načte zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-134">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="3c1e9-135">`paket.references`, soubor paket, který určuje závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-135">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="3c1e9-136">Otevřete `Script.fsx`a na konci tohoto kódu přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-136">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="3c1e9-137">Tato funkce převede slovo na formu [prasečí Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="3c1e9-137">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="3c1e9-138">Dalším krokem je vyhodnotit ho pomocí F# Interactive (fsi).</span><span class="sxs-lookup"><span data-stu-id="3c1e9-138">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="3c1e9-139">Zvýrazněte celou funkci (měla by být 11 řádků dlouhá).</span><span class="sxs-lookup"><span data-stu-id="3c1e9-139">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="3c1e9-140">Až se zvýrazní, podržte klávesu **ALT** a stiskněte **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-140">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="3c1e9-141">Všimněte si, že se zobrazí okno zobrazené níže a mělo by to vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-141">You'll notice a window pop up below, and it should show something like this:</span></span>

![Příklad F# interaktivního výstupu s Ionide](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="3c1e9-143">To mělo tři věci:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-143">This did three things:</span></span>

1. <span data-ttu-id="3c1e9-144">Spustil se proces FSI.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-144">It started the FSI process.</span></span>
2. <span data-ttu-id="3c1e9-145">Odeslali jsme kód, který jste zvýraznili v rámci procesu FSI.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-145">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="3c1e9-146">Proces FSI vyhodnotil kód, který jste odeslali.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-146">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="3c1e9-147">Vzhledem k tomu, že jste přeposlali [funkci](../language-reference/functions/index.md), můžete tuto funkci nyní volat pomocí FSI!</span><span class="sxs-lookup"><span data-stu-id="3c1e9-147">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="3c1e9-148">V interaktivním okně zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-148">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="3c1e9-149">Měl by se zobrazit následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-149">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="3c1e9-150">Teď zkusíme použít samohlásku jako první písmeno.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-150">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="3c1e9-151">Zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-151">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="3c1e9-152">Měl by se zobrazit následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-152">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="3c1e9-153">Zdá se, že funkce funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-153">The function appears to be working as expected.</span></span> <span data-ttu-id="3c1e9-154">Gratulujeme, právě jste napsali F# svou první funkci v Visual Studio Code a vyhodnotili ji pomocí FSI!</span><span class="sxs-lookup"><span data-stu-id="3c1e9-154">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="3c1e9-155">Jak jste si všimli, řádky v FSI se ukončí s `;;`.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-155">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="3c1e9-156">Důvodem je to, že FSI umožňuje zadat více řádků.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-156">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="3c1e9-157">`;;` Na konci umožňuje FSI informace o tom, kdy byl kód dokončen.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-157">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="3c1e9-158">Vysvětlení kódu</span><span class="sxs-lookup"><span data-stu-id="3c1e9-158">Explaining the code</span></span>

<span data-ttu-id="3c1e9-159">Pokud si nejste jistí, co kód skutečně dělá, tady je krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-159">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="3c1e9-160">Jak vidíte, `toPigLatin` je funkce, která jako svůj vstup přebírá slovo, a převede ho na reprezentaci tohoto slova v latince.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-160">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="3c1e9-161">Tato pravidla jsou následující:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-161">The rules for this are as follows:</span></span>

<span data-ttu-id="3c1e9-162">Pokud první znak ve slově začíná znakem samohlásky, přidejte na konec slova "yay".</span><span class="sxs-lookup"><span data-stu-id="3c1e9-162">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="3c1e9-163">Pokud nezačíná znakem samohlásky, přesuňte tento první znak na konec slova a přidejte do něj "Ay".</span><span class="sxs-lookup"><span data-stu-id="3c1e9-163">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="3c1e9-164">Možná jste si všimli, že v FSI máte následující:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-164">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="3c1e9-165">Jedná se o funkci, která přijímá `string` jako vstup (označovaný `word`), a vrátí jinou `string`. `toPigLatin`</span><span class="sxs-lookup"><span data-stu-id="3c1e9-165">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="3c1e9-166">To se označuje jako [Signatura typu funkce](https://fsharpforfunandprofit.com/posts/function-signatures/), základní část klíče F# , která je základem pro porozumění F# kódu.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-166">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="3c1e9-167">Všimněte si také, že najedete myší na funkci v Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-167">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="3c1e9-168">V těle funkce si všimnete dvou různých částí:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-168">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="3c1e9-169">Vnitřní funkce, která je `isVowel`volána, která určuje, zda daný znak`c`() je znak samohlásky pomocí kontroly, zda odpovídá jednomu ze zadaných vzorů přes [porovnávání vzorů](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="3c1e9-169">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="3c1e9-170">[`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) Výraz, který kontroluje, zda je první znak samohlásky, a vytvoří vrácenou hodnotu ze vstupních znaků na základě toho, zda byl první znak samohláskou nebo nikoli:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-170">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="3c1e9-171">Tok `toPigLatin` je tedy:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-171">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="3c1e9-172">Zkontroluje, jestli je první znak vstupního slova samohláskou.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-172">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="3c1e9-173">Pokud je, připojte k konci slova "yay".</span><span class="sxs-lookup"><span data-stu-id="3c1e9-173">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="3c1e9-174">V opačném případě přesuňte tento první znak na konec slova a přidejte do něj "Ay".</span><span class="sxs-lookup"><span data-stu-id="3c1e9-174">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="3c1e9-175">K dispozici je jedno konečné oznámení: neexistuje žádná explicitní instrukce pro návrat z funkce, na rozdíl od mnoha dalších jazyků.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-175">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="3c1e9-176">Důvodem je, F# že je založen na výrazu a poslední výraz v těle funkce je návratová hodnota.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-176">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="3c1e9-177">Vzhledem `if..then..else` k tomu, že se jedná o výraz, `then` bude v závislosti na vstupní hodnotě `else` vrácen text bloku nebo tělo bloku.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-177">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="3c1e9-178">Přesunutí kódu skriptu do implementačního souboru</span><span class="sxs-lookup"><span data-stu-id="3c1e9-178">Moving your script code into the implementation file</span></span>

<span data-ttu-id="3c1e9-179">Předchozí části tohoto článku ukázaly běžný první krok při psaní F# kódu: zápis počáteční funkce a interaktivní spuštění pomocí FSI.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-179">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="3c1e9-180">To se označuje jako vývoj řízený REPL, kde [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) představuje "Read-Evaluate-Print Loop".</span><span class="sxs-lookup"><span data-stu-id="3c1e9-180">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="3c1e9-181">Je to skvělý způsob, jak experimentovat s funkčnostmi, dokud nebudete mít nějakou práci.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-181">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="3c1e9-182">Dalším krokem v REPLém vývojovém prostředí F# je přesun pracovního kódu do implementačního souboru.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-182">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="3c1e9-183">Poté může být zkompilován F# kompilátorem do sestavení, které lze spustit.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-183">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="3c1e9-184">Začněte tím, že `ClassLibraryDemo.fs`otevřete.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-184">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="3c1e9-185">Všimněte si, že v něm už je nějaký kód.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-185">You'll notice that some code is already in there.</span></span> <span data-ttu-id="3c1e9-186">Pokračujte a odstraňte definici třídy, ale zajistěte, aby byla [`namespace`](../language-reference/namespaces.md) deklarace ponechána v horní části.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-186">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="3c1e9-187">V dalším kroku vytvořte nový [`module`](../language-reference/modules.md) `PigLatin` a zkopírujte `toPigLatin` do něj funkci, jako například:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-187">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="3c1e9-188">Dále znovu otevřete `Script.fsx` soubor a odstraňte celou `toPigLatin` funkci, ale nezapomeňte v souboru zachovat následující dva řádky:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-188">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="3c1e9-189">Vyberte oba řádky textu a stisknutím kombinace kláves ALT + ENTER tyto řádky v FSI spusťte.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-189">Select both lines of text and press Alt+Enter to execute these lines in FSI.</span></span> <span data-ttu-id="3c1e9-190">Načte obsah knihovny latince pro vepřové soubory do procesu FSI a `open` `ClassLibraryDemo` oboru názvů, abyste měli přístup k této funkci.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-190">These will load the contents of the Pig Latin library into the FSI process and `open` the `ClassLibraryDemo` namespace so that you have access to the functionality.</span></span>

<span data-ttu-id="3c1e9-191">Dále v okně FSI zavolejte funkci s `PigLatin` modulem, který jste definovali dříve:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-191">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```console
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="3c1e9-192">Nástup!</span><span class="sxs-lookup"><span data-stu-id="3c1e9-192">Success!</span></span> <span data-ttu-id="3c1e9-193">Dostanete stejné výsledky jako předtím, ale nyní se načtou z F# implementačního souboru.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-193">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="3c1e9-194">Hlavní rozdíl je v tom, F# že zdrojové soubory jsou zkompilovány do sestavení, které lze provést kdekoli, nikoli pouze v FSI.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-194">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="3c1e9-195">Souhrn</span><span class="sxs-lookup"><span data-stu-id="3c1e9-195">Summary</span></span>

<span data-ttu-id="3c1e9-196">V tomto článku jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-196">In this article, you've learned:</span></span>

1. <span data-ttu-id="3c1e9-197">Jak nastavit Visual Studio Code pomocí Ionide.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-197">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="3c1e9-198">Jak vytvořit svůj první F# projekt pomocí Ionide.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-198">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="3c1e9-199">Jak použít F# skriptování k zápisu první F# funkce v Ionide a její následné spuštění v FSI.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-199">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="3c1e9-200">Postup migrace kódu skriptu na F# zdroj a následné volání tohoto kódu z FSI.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-200">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="3c1e9-201">Nyní můžete pomocí Visual Studio Code a Ionide zapisovat mnohem F# více kódu.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-201">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="3c1e9-202">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="3c1e9-202">Troubleshooting</span></span>

<span data-ttu-id="3c1e9-203">Tady je několik způsobů, jak můžete řešit některé problémy, se kterými se můžete setkat:</span><span class="sxs-lookup"><span data-stu-id="3c1e9-203">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="3c1e9-204">Chcete-li získat funkce pro úpravu kódu Ionide, F# je třeba uložit soubory na disk a do složky, která je otevřena v pracovním prostoru Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-204">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="3c1e9-205">Pokud jste provedli změny v systému nebo nastavili požadavky Ionide Visual Studio Code otevřít, restartujte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-205">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="3c1e9-206">Ověřte, zda můžete použít F# kompilátor a F# interaktivní z příkazového řádku bez plně kvalifikované cesty.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-206">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="3c1e9-207">To `fsc` lze provést zadáním příkazu do příkazového řádku pro F# kompilátor `fsi` a nebo `fsharpi` pro Visual F# Tools on Windows a mono v systému Mac/Linux v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-207">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="3c1e9-208">Pokud máte v adresářích projektu neplatné znaky, Ionide nemusí fungovat.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-208">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="3c1e9-209">Pokud se jedná o tento případ, přejmenujte adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-209">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="3c1e9-210">Pokud žádný z příkazů Ionide nefunguje, zkontrolujte [Visual Studio Code vazby](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) klíčů a podívejte se, jestli je nepřepisujete havárií.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-210">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="3c1e9-211">Pokud je Ionide na vašem počítači poškozená a žádná z výše uvedených nevyřešila váš problém, zkuste `ionide-fsharp` odebrat adresář na počítači a znovu sadu modulů plug-in.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-211">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="3c1e9-212">Ionide je open source projekt sestavený a spravovaný členy F# komunity.</span><span class="sxs-lookup"><span data-stu-id="3c1e9-212">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="3c1e9-213">Oznamte prosím problémy a nebojte se přispět [na Ionide-VSCode: Úložiště](https://github.com/ionide/ionide-vscode-fsharp)GitHub FSharp</span><span class="sxs-lookup"><span data-stu-id="3c1e9-213">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="3c1e9-214">Pokud máte problém se sestavou, postupujte podle [pokynů pro získání protokolů, které se mají použít při hlášení problému](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="3c1e9-214">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="3c1e9-215">Můžete si také vyžádat další pomoc od vývojářů Ionide a F# komunity v [kanálu gitteru Ionide](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="3c1e9-215">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="3c1e9-216">Další postup</span><span class="sxs-lookup"><span data-stu-id="3c1e9-216">Next steps</span></span>

<span data-ttu-id="3c1e9-217">Chcete-li získat F# Další informace o funkcích jazyka, Projděte si [část F# ](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="3c1e9-217">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

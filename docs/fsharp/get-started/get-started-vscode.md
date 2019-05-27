---
title: Začínáme s F# ve Visual Studio Code
description: Další informace o použití F# s Visual Studio Code a Ionide suite modulu plug-in.
ms.date: 12/23/2018
ms.openlocfilehash: d9d5ed4008f657f956ee7a5611a2f5fdd8e5b44a
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051879"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="dc748-103">Začínáme s F# ve Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dc748-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="dc748-104">Můžete napsat F# v [Visual Studio Code](https://code.visualstudio.com) s [modulu plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) zobrazíte skvělé prostředí integrované vývojové prostředí (IDE) napříč platformami, základní technologie IntelliSense a základní kód refaktoring.</span><span class="sxs-lookup"><span data-stu-id="dc748-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="dc748-105">Navštivte [Ionide.io](http://ionide.io) získat další informace o modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="dc748-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="dc748-106">Pokud chcete začít, ujistěte se, že máte [ F# a modul plug-in Ionide správně nainstalovaný](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="dc748-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

> [!NOTE]
> <span data-ttu-id="dc748-107">Ionide vygeneruje rozhraní .NET Framework F# projekty, není dotnet core, který může mít problémy s kompatibilitou napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="dc748-107">Ionide will generate .NET Framework F# projects, not dotnet core, which can have cross-platform compatibility issues.</span></span> <span data-ttu-id="dc748-108">Pokud používáte **Linux** nebo **OSX**, jednodušší způsob, jak začít, je použít [nástroje příkazového řádku](get-started-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="dc748-108">If you are running on **Linux** or **OSX**, a simpler way to get started is to use the [command-line tools](get-started-command-line.md).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="dc748-109">Vytvoření prvního projektu s Ionide</span><span class="sxs-lookup"><span data-stu-id="dc748-109">Creating your first project with Ionide</span></span>

<span data-ttu-id="dc748-110">Chcete-li vytvořit nový F# projektu, otevřete Visual Studio Code v nové složce (můžete ji nazvat cokoli, co chcete).</span><span class="sxs-lookup"><span data-stu-id="dc748-110">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="dc748-111">Dále otevřete paletu příkazů (**zobrazení > paletu příkazů**) a zadejte následující údaje:</span><span class="sxs-lookup"><span data-stu-id="dc748-111">Next, open the command palette (**View > Command Palette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="dc748-112">Toto využívá k tomu [FORGE](https://github.com/fsharp-editing/Forge) projektu.</span><span class="sxs-lookup"><span data-stu-id="dc748-112">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
> <span data-ttu-id="dc748-113">Pokud nevidíte šablonu možnosti, zkuste aktualizovat šablony spuštěním následujícího příkazu v paletu příkazů: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="dc748-113">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="dc748-114">Vyberte "F#: Nový projekt"tím, že kliknete **Enter**.</span><span class="sxs-lookup"><span data-stu-id="dc748-114">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="dc748-115">Tím přejdete k dalšímu kroku, který je pro výběr šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="dc748-115">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="dc748-116">Vyberte si `classlib` šablony a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="dc748-116">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="dc748-117">V dalším kroku vyberte adresář pro vytvoření projektu v.</span><span class="sxs-lookup"><span data-stu-id="dc748-117">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="dc748-118">Pokud necháte prázdné, použije aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="dc748-118">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="dc748-119">A konečně pojmenujte svůj projekt v posledním kroku.</span><span class="sxs-lookup"><span data-stu-id="dc748-119">Finally, name your project in the final step.</span></span> <span data-ttu-id="dc748-120">F#používá [pascalcase](http://c2.com/cgi/wiki?PascalCase) pro názvy projektů.</span><span class="sxs-lookup"><span data-stu-id="dc748-120">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="dc748-121">Tento článek používá `ClassLibraryDemo` jako název.</span><span class="sxs-lookup"><span data-stu-id="dc748-121">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="dc748-122">Jakmile zadáte název, který chcete pro váš projekt, stiskněte **Enter**.</span><span class="sxs-lookup"><span data-stu-id="dc748-122">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="dc748-123">Pokud jste postupovali podle předchozího kroku, měli byste získat Visual Studio Code pracovního prostoru na levé straně se zobrazí s následujícími možnostmi:</span><span class="sxs-lookup"><span data-stu-id="dc748-123">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="dc748-124">F# Samotný projekt pod ní `ClassLibraryDemo` složky.</span><span class="sxs-lookup"><span data-stu-id="dc748-124">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="dc748-125">Správnou adresářovou strukturu pro přidávání balíčků prostřednictvím [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="dc748-125">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="dc748-126">Různé platformy sestavení skript s [ `FAKE` ](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="dc748-126">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="dc748-127">`paket.exe` Spustitelný soubor, který lze načíst balíčky a vyřešení závislostí pro vás.</span><span class="sxs-lookup"><span data-stu-id="dc748-127">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="dc748-128">A `.gitignore` souboru, pokud chcete přidat tento projekt do správy verzí z Gitu.</span><span class="sxs-lookup"><span data-stu-id="dc748-128">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="dc748-129">Psaním kódu</span><span class="sxs-lookup"><span data-stu-id="dc748-129">Writing some code</span></span>

<span data-ttu-id="dc748-130">Otevřít *ClassLibraryDemo* složky.</span><span class="sxs-lookup"><span data-stu-id="dc748-130">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="dc748-131">Zobrazí se následující soubory:</span><span class="sxs-lookup"><span data-stu-id="dc748-131">You should see the following files:</span></span>

1. <span data-ttu-id="dc748-132">`ClassLibraryDemo.fs`, F# implementační soubor s třídou definované.</span><span class="sxs-lookup"><span data-stu-id="dc748-132">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="dc748-133">`ClassLibraryDemo.fsproj`, F# soubor projektu používá k vytváření buildu tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="dc748-133">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="dc748-134">`Script.fsx`, F# soubor skriptu, který načte zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="dc748-134">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="dc748-135">`paket.references`, stáhnout soubor, který určuje závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="dc748-135">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="dc748-136">Otevřít `Script.fsx`a přidejte následující kód na konci ho:</span><span class="sxs-lookup"><span data-stu-id="dc748-136">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="dc748-137">Tato funkce převede do formy slovo [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="dc748-137">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="dc748-138">Dalším krokem je vyhodnotit pomocí F# interaktivní (soubor FSI).</span><span class="sxs-lookup"><span data-stu-id="dc748-138">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="dc748-139">Zvýrazněte celý – funkce (musí být dlouhý 11 řádky).</span><span class="sxs-lookup"><span data-stu-id="dc748-139">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="dc748-140">Jakmile je zvýrazněn, podržte **Alt** klíče a přístupů **Enter**.</span><span class="sxs-lookup"><span data-stu-id="dc748-140">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="dc748-141">Všimněte si níže překryvné okno a měl by se zobrazit, přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="dc748-141">You'll notice a window pop up below, and it should show something like this:</span></span>

![Příklad F# interaktivní výstup s Ionide](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="dc748-143">To provedl tři věci:</span><span class="sxs-lookup"><span data-stu-id="dc748-143">This did three things:</span></span>

1. <span data-ttu-id="dc748-144">Jeho spuštění procesu FSI.</span><span class="sxs-lookup"><span data-stu-id="dc748-144">It started the FSI process.</span></span>
2. <span data-ttu-id="dc748-145">Kód, který jste zvýraznili se odesílají prostřednictvím procesu FSI.</span><span class="sxs-lookup"><span data-stu-id="dc748-145">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="dc748-146">Proces FSI vyhodnotí kód, který jste odeslali přes.</span><span class="sxs-lookup"><span data-stu-id="dc748-146">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="dc748-147">Vzhledem k tomu, že byl odeslán přes [funkce](../language-reference/functions/index.md), můžete nyní volat tuto funkci s FSI!</span><span class="sxs-lookup"><span data-stu-id="dc748-147">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="dc748-148">V interaktivním okně zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="dc748-148">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="dc748-149">Měli byste vidět následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="dc748-149">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="dc748-150">Teď vyzkoušíme s samohláskou jako první písmeno.</span><span class="sxs-lookup"><span data-stu-id="dc748-150">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="dc748-151">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="dc748-151">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="dc748-152">Měli byste vidět následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="dc748-152">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="dc748-153">Zdá se, že funkce fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="dc748-153">The function appears to be working as expected.</span></span> <span data-ttu-id="dc748-154">Blahopřejeme, jste napsali první F# funkce v aplikaci Visual Studio Code a vyhodnotit s FSI!</span><span class="sxs-lookup"><span data-stu-id="dc748-154">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="dc748-155">Protože jste si všimli, se ukončují vstupující FSI `;;`.</span><span class="sxs-lookup"><span data-stu-id="dc748-155">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="dc748-156">Je to proto, že soubor FSI umožňuje zadat více řádků.</span><span class="sxs-lookup"><span data-stu-id="dc748-156">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="dc748-157">`;;` Na konci umožňuje FSI vědět, kdy je dokončena kód.</span><span class="sxs-lookup"><span data-stu-id="dc748-157">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="dc748-158">Vysvětlení kódu</span><span class="sxs-lookup"><span data-stu-id="dc748-158">Explaining the code</span></span>

<span data-ttu-id="dc748-159">Pokud si nejste jisti, co kód skutečně dělají, tady je krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="dc748-159">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="dc748-160">Jak je vidět, `toPigLatin` je funkce, která přebírá slova jako vstup a převede ho na Pig Latin reprezentace toto slovo.</span><span class="sxs-lookup"><span data-stu-id="dc748-160">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="dc748-161">Pravidla pro to jsou následující:</span><span class="sxs-lookup"><span data-stu-id="dc748-161">The rules for this are as follows:</span></span>

<span data-ttu-id="dc748-162">Pokud první znak v slovo začíná samohláskou, přidáte na konec slovo "yay".</span><span class="sxs-lookup"><span data-stu-id="dc748-162">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="dc748-163">Pokud se nespustí s samohláskou přesunout prvním znaku na konci slovo a "ay" přidejte do ní.</span><span class="sxs-lookup"><span data-stu-id="dc748-163">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="dc748-164">Možná jste si všimli v FSI následující kroky:</span><span class="sxs-lookup"><span data-stu-id="dc748-164">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="dc748-165">Uvádí, že to `toPigLatin` je funkce, která přijímá `string` jako vstup (volá `word`) a vrátí jiný `string`.</span><span class="sxs-lookup"><span data-stu-id="dc748-165">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="dc748-166">To se označuje jako [podpis typu funkce](https://fsharpforfunandprofit.com/posts/function-signatures/), základní část F# , který je klíčem k pochopení F# kódu.</span><span class="sxs-lookup"><span data-stu-id="dc748-166">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="dc748-167">Můžete také všimnout to Pokud najedete myší na funkci v aplikaci Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dc748-167">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="dc748-168">V těle funkce můžete si všimnout dvou samostatných částí:</span><span class="sxs-lookup"><span data-stu-id="dc748-168">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="dc748-169">Vnitřní funkci nazvanou `isVowel`, který určuje, zda daný znak (`c`) je samohláskou kontrolou, jestli odpovídá jednomu ze vzorů poskytnutý prostřednictvím [porovnávání vzorů](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="dc748-169">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="dc748-170">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Výraz, který zkontroluje, jestli je první znak samohláskou a konstrukcí návratová hodnota ze vstupních znaků na základě-li první znak byla samohláskou nebo ne:</span><span class="sxs-lookup"><span data-stu-id="dc748-170">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="dc748-171">Tok `toPigLatin` je takto:</span><span class="sxs-lookup"><span data-stu-id="dc748-171">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="dc748-172">Zkontrolujte, jestli je první znak slova vstupní samohláskou.</span><span class="sxs-lookup"><span data-stu-id="dc748-172">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="dc748-173">Pokud se jedná, připojte na konci slovo "yay".</span><span class="sxs-lookup"><span data-stu-id="dc748-173">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="dc748-174">V opačném případě přesunout prvním znaku na konci slovo a přidejte do ní "ay".</span><span class="sxs-lookup"><span data-stu-id="dc748-174">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="dc748-175">Existuje jedna poslední věc, Všimněte si, že o tomto: neexistuje žádná explicitní instrukce k vrácení z funkce, na rozdíl od mnoha jiných jazycích tam.</span><span class="sxs-lookup"><span data-stu-id="dc748-175">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="dc748-176">Důvodem je, že F# je založené na výrazu, a je návratová hodnota posledního výrazu v těle funkce.</span><span class="sxs-lookup"><span data-stu-id="dc748-176">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="dc748-177">Protože `if..then..else` je samotný výraz text `then` bloku nebo textu `else` bloku se vrátí v závislosti na vstupní hodnota.</span><span class="sxs-lookup"><span data-stu-id="dc748-177">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="dc748-178">Přesunutí kódu skriptu do souboru implementace</span><span class="sxs-lookup"><span data-stu-id="dc748-178">Moving your script code into the implementation file</span></span>

<span data-ttu-id="dc748-179">Předchozích částech tohoto článku jsme vám ukázali běžné prvním krokem při psaní F# kódu: psaní počáteční funkce a interaktivní spuštění pomocí FSI.</span><span class="sxs-lookup"><span data-stu-id="dc748-179">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="dc748-180">To se označuje jako vývoj řízený REPL, kde [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) zastupuje "Čtení-vyhodnocení-Print smyčka".</span><span class="sxs-lookup"><span data-stu-id="dc748-180">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="dc748-181">To je skvělý způsob, jak experimentovat s funkcemi, dokud máte něco, co funguje.</span><span class="sxs-lookup"><span data-stu-id="dc748-181">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="dc748-182">Dalším krokem v vývoj řízený REPL je chcete přesunout pracovní kód do F# implementační soubor.</span><span class="sxs-lookup"><span data-stu-id="dc748-182">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="dc748-183">To může být poté zkompilován pomocí F# kompilátoru do sestavení, které mohou být provedeny.</span><span class="sxs-lookup"><span data-stu-id="dc748-183">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="dc748-184">Pokud chcete začít, otevřete `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="dc748-184">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="dc748-185">Můžete si všimnout, že nějaký kód je již existuje.</span><span class="sxs-lookup"><span data-stu-id="dc748-185">You'll notice that some code is already in there.</span></span> <span data-ttu-id="dc748-186">Pokračujte a odstranit definici třídy, ale ponechte [ `namespace` ](../language-reference/namespaces.md) deklarace v horní části.</span><span class="sxs-lookup"><span data-stu-id="dc748-186">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="dc748-187">Dále vytvořte novou [ `module` ](../language-reference/modules.md) volá `PigLatin` a zkopírujte `toPigLatin` funkce do něj takto:</span><span class="sxs-lookup"><span data-stu-id="dc748-187">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="dc748-188">Dále otevřete `Script.fsx` soubor znovu a odstranit celý `toPigLatin` fungovat, ale ujistěte se, aby následující dva řádky v souboru:</span><span class="sxs-lookup"><span data-stu-id="dc748-188">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="dc748-189">Vyberte obě čáry text a stisknutím kláves Alt + Enter pro spuštění ve FSI tyto řádky.</span><span class="sxs-lookup"><span data-stu-id="dc748-189">Select both lines of text and press Alt+Enter to execute these lines in FSI.</span></span> <span data-ttu-id="dc748-190">Obsah knihovny Pig Latin tyto se načtou do procesu FSI a `open` `ClassLibraryDemo` obor názvů, abyste měli přístup k funkcím.</span><span class="sxs-lookup"><span data-stu-id="dc748-190">These will load the contents of the Pig Latin library into the FSI process and `open` the `ClassLibraryDemo` namespace so that you have access to the functionality.</span></span>

<span data-ttu-id="dc748-191">Pak v okně FSI zavolejte funkci s `PigLatin` modul, který jste definovali dříve:</span><span class="sxs-lookup"><span data-stu-id="dc748-191">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="dc748-192">Úspěch!</span><span class="sxs-lookup"><span data-stu-id="dc748-192">Success!</span></span> <span data-ttu-id="dc748-193">Zobrazí stejné výsledky jako předtím, ale teď načíst ze F# implementační soubor.</span><span class="sxs-lookup"><span data-stu-id="dc748-193">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="dc748-194">Hlavní rozdíl spočívá v tom, který F# zdrojové soubory jsou zkompilovány do sestavení, které lze spustit kdekoli, ne jenom v FSI.</span><span class="sxs-lookup"><span data-stu-id="dc748-194">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="dc748-195">Souhrn</span><span class="sxs-lookup"><span data-stu-id="dc748-195">Summary</span></span>

<span data-ttu-id="dc748-196">V tomto článku jste zjistili:</span><span class="sxs-lookup"><span data-stu-id="dc748-196">In this article, you've learned:</span></span>

1. <span data-ttu-id="dc748-197">Jak nastavit službu Visual Studio Code s Ionide.</span><span class="sxs-lookup"><span data-stu-id="dc748-197">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="dc748-198">Jak vytvořit první F# projekt s Ionide.</span><span class="sxs-lookup"><span data-stu-id="dc748-198">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="dc748-199">Jak používat F# skriptování pro zápis první F# fungovat v Ionide a proveďte jej v FSI.</span><span class="sxs-lookup"><span data-stu-id="dc748-199">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="dc748-200">Jak migrovat kód skriptu do F# zdroje a pak vyvolejte tento kód z FSI.</span><span class="sxs-lookup"><span data-stu-id="dc748-200">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="dc748-201">Jste teď umožňuje psát spoustu dalších věcí F# programování s využitím Visual Studio Code a Ionide.</span><span class="sxs-lookup"><span data-stu-id="dc748-201">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="dc748-202">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="dc748-202">Troubleshooting</span></span>

<span data-ttu-id="dc748-203">Tady je několik způsobů, jak je řešit určité problémy, které můžete narazit na:</span><span class="sxs-lookup"><span data-stu-id="dc748-203">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="dc748-204">Chcete-li získat funkce Ionide, pro úpravu kódu vašeho F# soubory musí být uloženo na disk a ve složce, která je otevřena v pracovním prostoru Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dc748-204">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="dc748-205">Pokud jste provedené změny v systému nebo nainstalované požadavky Ionide pomocí Visual Studio Code, otevřít, restartujte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dc748-205">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="dc748-206">Zkontrolujte, zda můžete použít F# kompilátoru a F# interaktivní z příkazového řádku bez plně kvalifikované cesty.</span><span class="sxs-lookup"><span data-stu-id="dc748-206">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="dc748-207">To lze provést zadáním `fsc` v příkazový řádek, F# kompilátoru, a `fsi` nebo `fsharpi` vizuálu F# nástroje na Windows a Mono na Mac/Linux, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="dc748-207">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="dc748-208">Pokud vaše adresáře projektu obsahuje neplatné znaky, Ionide nemusí fungovat.</span><span class="sxs-lookup"><span data-stu-id="dc748-208">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="dc748-209">Přejmenování adresáře vašeho projektu, pokud tomu tak.</span><span class="sxs-lookup"><span data-stu-id="dc748-209">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="dc748-210">Pokud žádný z příkazů Ionide práci, zkontrolujte vaše [klávesové zkratky pro Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) zobrazíte, pokud jste už je přepsání náhodná.</span><span class="sxs-lookup"><span data-stu-id="dc748-210">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="dc748-211">Pokud Ionide nefunguje na vašem počítači a žádná z výše uvedených vyřešil potíže, zkuste odebrat `ionide-fsharp` adresáře v počítači a znovu nainstalujte modul plug-in.</span><span class="sxs-lookup"><span data-stu-id="dc748-211">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="dc748-212">Ionide je projekt open source integrované a udržován členy F# komunity.</span><span class="sxs-lookup"><span data-stu-id="dc748-212">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="dc748-213">Naleznete hlaste problémy a Nebojte se přispět na [Ionide VSCode: Úložiště FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="dc748-213">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="dc748-214">Pokud máte potíže do sestavy, postupujte prosím podle [pokyny pro získání protokolů pro použití při hlášení](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="dc748-214">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="dc748-215">Můžete také požádat o další pomoc od vývojářů Ionide a F# komunitou v [Ionide Gitteru kanál](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="dc748-215">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="dc748-216">Další kroky</span><span class="sxs-lookup"><span data-stu-id="dc748-216">Next steps</span></span>

<span data-ttu-id="dc748-217">Další informace o F# a funkcí jazyka, podívejte se na [prohlídka F# ](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="dc748-217">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

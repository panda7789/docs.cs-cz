---
title: Začínáme s F# ve Visual Studio Code
description: Další informace o použití F# s Visual Studio Code a Ionide suite modulu plug-in.
ms.date: 05/28/2018
ms.openlocfilehash: 2db587b5614c5a7ca9285cad9b719970d53afd55
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129789"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="d156d-103">Začínáme s F# ve Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d156d-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="d156d-104">Můžete napsat F# v [Visual Studio Code](https://code.visualstudio.com) s [modulu plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) zobrazíte skvělé prostředí integrované vývojové prostředí (IDE) napříč platformami, základní technologie IntelliSense a základní kód refaktoring.</span><span class="sxs-lookup"><span data-stu-id="d156d-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="d156d-105">Navštivte [Ionide.io](http://ionide.io) získat další informace o modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="d156d-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="d156d-106">Pokud chcete začít, ujistěte se, že máte [ F# a modul plug-in Ionide správně nainstalovaný](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="d156d-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="d156d-107">Vytvoření prvního projektu s Ionide</span><span class="sxs-lookup"><span data-stu-id="d156d-107">Creating your first project with Ionide</span></span>

<span data-ttu-id="d156d-108">Chcete-li vytvořit nový F# projektu, otevřete Visual Studio Code v nové složce (můžete ji nazvat cokoli, co chcete).</span><span class="sxs-lookup"><span data-stu-id="d156d-108">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="d156d-109">Dále otevřete paletu příkazů (**zobrazení > paletu příkazů**) a zadejte následující údaje:</span><span class="sxs-lookup"><span data-stu-id="d156d-109">Next, open the command palette (**View > Command Palette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="d156d-110">Toto využívá k tomu [FORGE](https://github.com/fsharp-editing/Forge) projektu.</span><span class="sxs-lookup"><span data-stu-id="d156d-110">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
> <span data-ttu-id="d156d-111">Pokud nevidíte šablonu možnosti, zkuste aktualizovat šablony spuštěním následujícího příkazu v paletu příkazů: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="d156d-111">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="d156d-112">Vyberte "F#: Nový projekt"tím, že kliknete **Enter**.</span><span class="sxs-lookup"><span data-stu-id="d156d-112">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="d156d-113">Tím přejdete k dalšímu kroku, který je pro výběr šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="d156d-113">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="d156d-114">Vyberte si `classlib` šablony a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="d156d-114">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="d156d-115">V dalším kroku vyberte adresář pro vytvoření projektu v.</span><span class="sxs-lookup"><span data-stu-id="d156d-115">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="d156d-116">Pokud necháte prázdné, použije aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="d156d-116">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="d156d-117">A konečně pojmenujte svůj projekt v posledním kroku.</span><span class="sxs-lookup"><span data-stu-id="d156d-117">Finally, name your project in the final step.</span></span> <span data-ttu-id="d156d-118">F#používá [pascalcase](http://c2.com/cgi/wiki?PascalCase) pro názvy projektů.</span><span class="sxs-lookup"><span data-stu-id="d156d-118">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="d156d-119">Tento článek používá `ClassLibraryDemo` jako název.</span><span class="sxs-lookup"><span data-stu-id="d156d-119">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="d156d-120">Jakmile zadáte název, který chcete pro váš projekt, stiskněte **Enter**.</span><span class="sxs-lookup"><span data-stu-id="d156d-120">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="d156d-121">Pokud jste postupovali podle předchozího kroku, měli byste získat Visual Studio Code pracovního prostoru na levé straně se zobrazí s následujícími možnostmi:</span><span class="sxs-lookup"><span data-stu-id="d156d-121">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="d156d-122">F# Samotný projekt pod ní `ClassLibraryDemo` složky.</span><span class="sxs-lookup"><span data-stu-id="d156d-122">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="d156d-123">Správnou adresářovou strukturu pro přidávání balíčků prostřednictvím [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="d156d-123">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="d156d-124">Různé platformy sestavení skript s [ `FAKE` ](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="d156d-124">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="d156d-125">`paket.exe` Spustitelný soubor, který lze načíst balíčky a vyřešení závislostí pro vás.</span><span class="sxs-lookup"><span data-stu-id="d156d-125">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="d156d-126">A `.gitignore` souboru, pokud chcete přidat tento projekt do správy verzí z Gitu.</span><span class="sxs-lookup"><span data-stu-id="d156d-126">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="d156d-127">Psaním kódu</span><span class="sxs-lookup"><span data-stu-id="d156d-127">Writing some code</span></span>

<span data-ttu-id="d156d-128">Otevřít *ClassLibraryDemo* složky.</span><span class="sxs-lookup"><span data-stu-id="d156d-128">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="d156d-129">Zobrazí se následující soubory:</span><span class="sxs-lookup"><span data-stu-id="d156d-129">You should see the following files:</span></span>

1. <span data-ttu-id="d156d-130">`ClassLibraryDemo.fs`, F# implementační soubor s třídou definované.</span><span class="sxs-lookup"><span data-stu-id="d156d-130">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="d156d-131">`ClassLibraryDemo.fsproj`, F# soubor projektu používá k vytváření buildu tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="d156d-131">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="d156d-132">`Script.fsx`, F# soubor skriptu, který načte zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="d156d-132">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="d156d-133">`paket.references`, stáhnout soubor, který určuje závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="d156d-133">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="d156d-134">Otevřít `Script.fsx`a přidejte následující kód na konci ho:</span><span class="sxs-lookup"><span data-stu-id="d156d-134">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="d156d-135">Tato funkce převede do formy slovo [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="d156d-135">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="d156d-136">Dalším krokem je vyhodnotit pomocí F# interaktivní (soubor FSI).</span><span class="sxs-lookup"><span data-stu-id="d156d-136">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="d156d-137">Zvýrazněte celý – funkce (musí být dlouhý 11 řádky).</span><span class="sxs-lookup"><span data-stu-id="d156d-137">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="d156d-138">Jakmile je zvýrazněn, podržte **Alt** klíče a přístupů **Enter**.</span><span class="sxs-lookup"><span data-stu-id="d156d-138">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="d156d-139">Všimněte si níže překryvné okno a měl by se zobrazit, přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="d156d-139">You'll notice a window pop up below, and it should show something like this:</span></span>

![Příklad F# interaktivní výstup s Ionide](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="d156d-141">To provedl tři věci:</span><span class="sxs-lookup"><span data-stu-id="d156d-141">This did three things:</span></span>

1. <span data-ttu-id="d156d-142">Jeho spuštění procesu FSI.</span><span class="sxs-lookup"><span data-stu-id="d156d-142">It started the FSI process.</span></span>
2. <span data-ttu-id="d156d-143">Kód, který jste zvýraznili se odesílají prostřednictvím procesu FSI.</span><span class="sxs-lookup"><span data-stu-id="d156d-143">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="d156d-144">Proces FSI vyhodnotí kód, který jste odeslali přes.</span><span class="sxs-lookup"><span data-stu-id="d156d-144">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="d156d-145">Vzhledem k tomu, že byl odeslán přes [funkce](../language-reference/functions/index.md), můžete nyní volat tuto funkci s FSI!</span><span class="sxs-lookup"><span data-stu-id="d156d-145">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="d156d-146">V interaktivním okně zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d156d-146">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="d156d-147">Měli byste vidět následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="d156d-147">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="d156d-148">Teď vyzkoušíme s samohláskou jako první písmeno.</span><span class="sxs-lookup"><span data-stu-id="d156d-148">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="d156d-149">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d156d-149">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="d156d-150">Měli byste vidět následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="d156d-150">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="d156d-151">Zdá se, že funkce fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="d156d-151">The function appears to be working as expected.</span></span> <span data-ttu-id="d156d-152">Blahopřejeme, jste napsali první F# funkce v aplikaci Visual Studio Code a vyhodnotit s FSI!</span><span class="sxs-lookup"><span data-stu-id="d156d-152">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="d156d-153">Protože jste si všimli, se ukončují vstupující FSI `;;`.</span><span class="sxs-lookup"><span data-stu-id="d156d-153">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="d156d-154">Je to proto, že soubor FSI umožňuje zadat více řádků.</span><span class="sxs-lookup"><span data-stu-id="d156d-154">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="d156d-155">`;;` Na konci umožňuje FSI vědět, kdy je dokončena kód.</span><span class="sxs-lookup"><span data-stu-id="d156d-155">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="d156d-156">Vysvětlení kódu</span><span class="sxs-lookup"><span data-stu-id="d156d-156">Explaining the code</span></span>

<span data-ttu-id="d156d-157">Pokud si nejste jisti, co kód skutečně dělají, tady je krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="d156d-157">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="d156d-158">Jak je vidět, `toPigLatin` je funkce, která přebírá slova jako vstup a převede ho na Pig Latin reprezentace toto slovo.</span><span class="sxs-lookup"><span data-stu-id="d156d-158">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="d156d-159">Pravidla pro to jsou následující:</span><span class="sxs-lookup"><span data-stu-id="d156d-159">The rules for this are as follows:</span></span>

<span data-ttu-id="d156d-160">Pokud první znak v slovo začíná samohláskou, přidáte na konec slovo "yay".</span><span class="sxs-lookup"><span data-stu-id="d156d-160">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="d156d-161">Pokud se nespustí s samohláskou přesunout prvním znaku na konci slovo a "ay" přidejte do ní.</span><span class="sxs-lookup"><span data-stu-id="d156d-161">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="d156d-162">Možná jste si všimli v FSI následující kroky:</span><span class="sxs-lookup"><span data-stu-id="d156d-162">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="d156d-163">Uvádí, že to `toPigLatin` je funkce, která přijímá `string` jako vstup (volá `word`) a vrátí jiný `string`.</span><span class="sxs-lookup"><span data-stu-id="d156d-163">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="d156d-164">To se označuje jako [podpis typu funkce](https://fsharpforfunandprofit.com/posts/function-signatures/), základní část F# , který je klíčem k pochopení F# kódu.</span><span class="sxs-lookup"><span data-stu-id="d156d-164">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="d156d-165">Můžete také všimnout to Pokud najedete myší na funkci v aplikaci Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="d156d-165">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="d156d-166">V těle funkce můžete si všimnout dvou samostatných částí:</span><span class="sxs-lookup"><span data-stu-id="d156d-166">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="d156d-167">Vnitřní funkci nazvanou `isVowel`, který určuje, zda daný znak (`c`) je samohláskou kontrolou, jestli odpovídá jednomu ze vzorů poskytnutý prostřednictvím [porovnávání vzorů](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="d156d-167">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="d156d-168">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Výraz, který zkontroluje, jestli je první znak samohláskou a konstrukcí návratová hodnota ze vstupních znaků na základě-li první znak byla samohláskou nebo ne:</span><span class="sxs-lookup"><span data-stu-id="d156d-168">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="d156d-169">Tok `toPigLatin` je takto:</span><span class="sxs-lookup"><span data-stu-id="d156d-169">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="d156d-170">Zkontrolujte, jestli je první znak slova vstupní samohláskou.</span><span class="sxs-lookup"><span data-stu-id="d156d-170">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="d156d-171">Pokud se jedná, připojte na konci slovo "yay".</span><span class="sxs-lookup"><span data-stu-id="d156d-171">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="d156d-172">V opačném případě přesunout prvním znaku na konci slovo a přidejte do ní "ay".</span><span class="sxs-lookup"><span data-stu-id="d156d-172">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="d156d-173">Existuje jedna poslední věc, Všimněte si, že o tomto: neexistuje žádná explicitní instrukce k vrácení z funkce, na rozdíl od mnoha jiných jazycích tam.</span><span class="sxs-lookup"><span data-stu-id="d156d-173">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="d156d-174">Důvodem je, že F# je založené na výrazu, a je návratová hodnota posledního výrazu v těle funkce.</span><span class="sxs-lookup"><span data-stu-id="d156d-174">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="d156d-175">Protože `if..then..else` je samotný výraz text `then` bloku nebo textu `else` bloku se vrátí v závislosti na vstupní hodnota.</span><span class="sxs-lookup"><span data-stu-id="d156d-175">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="d156d-176">Přesunutí kódu skriptu do souboru implementace</span><span class="sxs-lookup"><span data-stu-id="d156d-176">Moving your script code into the implementation file</span></span>

<span data-ttu-id="d156d-177">Předchozích částech tohoto článku jsme vám ukázali běžné prvním krokem při psaní F# kódu: psaní počáteční funkce a interaktivní spuštění pomocí FSI.</span><span class="sxs-lookup"><span data-stu-id="d156d-177">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="d156d-178">To se označuje jako vývoj řízený REPL, kde [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) zastupuje "Čtení-vyhodnocení-Print smyčka".</span><span class="sxs-lookup"><span data-stu-id="d156d-178">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="d156d-179">To je skvělý způsob, jak experimentovat s funkcemi, dokud máte něco, co funguje.</span><span class="sxs-lookup"><span data-stu-id="d156d-179">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="d156d-180">Dalším krokem v vývoj řízený REPL je chcete přesunout pracovní kód do F# implementační soubor.</span><span class="sxs-lookup"><span data-stu-id="d156d-180">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="d156d-181">To může být poté zkompilován pomocí F# kompilátoru do sestavení, které mohou být provedeny.</span><span class="sxs-lookup"><span data-stu-id="d156d-181">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="d156d-182">Pokud chcete začít, otevřete `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="d156d-182">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="d156d-183">Můžete si všimnout, že nějaký kód je již existuje.</span><span class="sxs-lookup"><span data-stu-id="d156d-183">You'll notice that some code is already in there.</span></span> <span data-ttu-id="d156d-184">Pokračujte a odstranit definici třídy, ale ponechte [ `namespace` ](../language-reference/namespaces.md) deklarace v horní části.</span><span class="sxs-lookup"><span data-stu-id="d156d-184">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="d156d-185">Dále vytvořte novou [ `module` ](../language-reference/modules.md) volá `PigLatin` a zkopírujte `toPigLatin` funkce do něj takto:</span><span class="sxs-lookup"><span data-stu-id="d156d-185">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="d156d-186">Dále otevřete `Script.fsx` soubor znovu a odstranit celý `toPigLatin` fungovat, ale ujistěte se, aby následující dva řádky v souboru:</span><span class="sxs-lookup"><span data-stu-id="d156d-186">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="d156d-187">První řádek je potřeba pro FSI skriptování pro načtení `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="d156d-187">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span> <span data-ttu-id="d156d-188">Druhý řádek je usnadnění: ho vynechání je volitelný, ale budete muset zadat `open ClassLibraryDemo` v okně FSI-li přenést `ToPigLatin` modulu do oboru.</span><span class="sxs-lookup"><span data-stu-id="d156d-188">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="d156d-189">Pak v okně FSI zavolejte funkci s `PigLatin` modul, který jste definovali dříve:</span><span class="sxs-lookup"><span data-stu-id="d156d-189">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="d156d-190">Úspěch!</span><span class="sxs-lookup"><span data-stu-id="d156d-190">Success!</span></span> <span data-ttu-id="d156d-191">Zobrazí stejné výsledky jako předtím, ale teď načíst ze F# implementační soubor.</span><span class="sxs-lookup"><span data-stu-id="d156d-191">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="d156d-192">Hlavní rozdíl spočívá v tom, který F# zdrojové soubory jsou zkompilovány do sestavení, které lze spustit kdekoli, ne jenom v FSI.</span><span class="sxs-lookup"><span data-stu-id="d156d-192">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="d156d-193">Souhrn</span><span class="sxs-lookup"><span data-stu-id="d156d-193">Summary</span></span>

<span data-ttu-id="d156d-194">V tomto článku jste zjistili:</span><span class="sxs-lookup"><span data-stu-id="d156d-194">In this article, you've learned:</span></span>

1. <span data-ttu-id="d156d-195">Jak nastavit službu Visual Studio Code s Ionide.</span><span class="sxs-lookup"><span data-stu-id="d156d-195">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="d156d-196">Jak vytvořit první F# projekt s Ionide.</span><span class="sxs-lookup"><span data-stu-id="d156d-196">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="d156d-197">Jak používat F# skriptování pro zápis první F# fungovat v Ionide a proveďte jej v FSI.</span><span class="sxs-lookup"><span data-stu-id="d156d-197">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="d156d-198">Jak migrovat kód skriptu do F# zdroje a pak vyvolejte tento kód z FSI.</span><span class="sxs-lookup"><span data-stu-id="d156d-198">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="d156d-199">Jste teď umožňuje psát spoustu dalších věcí F# programování s využitím Visual Studio Code a Ionide.</span><span class="sxs-lookup"><span data-stu-id="d156d-199">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="d156d-200">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="d156d-200">Troubleshooting</span></span>

<span data-ttu-id="d156d-201">Tady je několik způsobů, jak je řešit určité problémy, které můžete narazit na:</span><span class="sxs-lookup"><span data-stu-id="d156d-201">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="d156d-202">Chcete-li získat funkce Ionide, pro úpravu kódu vašeho F# soubory musí být uloženo na disk a ve složce, která je otevřena v pracovním prostoru Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="d156d-202">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="d156d-203">Pokud jste provedené změny v systému nebo nainstalované požadavky Ionide pomocí Visual Studio Code, otevřít, restartujte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="d156d-203">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="d156d-204">Zkontrolujte, zda můžete použít F# kompilátoru a F# interaktivní z příkazového řádku bez plně kvalifikované cesty.</span><span class="sxs-lookup"><span data-stu-id="d156d-204">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="d156d-205">To lze provést zadáním `fsc` v příkazový řádek, F# kompilátoru, a `fsi` nebo `fsharpi` vizuálu F# nástroje na Windows a Mono na Mac/Linux, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d156d-205">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="d156d-206">Pokud vaše adresáře projektu obsahuje neplatné znaky, Ionide nemusí fungovat.</span><span class="sxs-lookup"><span data-stu-id="d156d-206">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="d156d-207">Přejmenování adresáře vašeho projektu, pokud tomu tak.</span><span class="sxs-lookup"><span data-stu-id="d156d-207">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="d156d-208">Pokud žádný z příkazů Ionide práci, zkontrolujte vaše [klávesové zkratky pro Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) zobrazíte, pokud jste už je přepsání náhodná.</span><span class="sxs-lookup"><span data-stu-id="d156d-208">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="d156d-209">Pokud Ionide nefunguje na vašem počítači a žádná z výše uvedených vyřešil potíže, zkuste odebrat `ionide-fsharp` adresáře v počítači a znovu nainstalujte modul plug-in.</span><span class="sxs-lookup"><span data-stu-id="d156d-209">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="d156d-210">Ionide je projekt open source integrované a udržován členy F# komunity.</span><span class="sxs-lookup"><span data-stu-id="d156d-210">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="d156d-211">Naleznete hlaste problémy a Nebojte se přispět na [Ionide VSCode: Úložiště FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="d156d-211">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="d156d-212">Pokud máte potíže do sestavy, postupujte prosím podle [pokyny pro získání protokolů pro použití při hlášení](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="d156d-212">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="d156d-213">Můžete také požádat o další pomoc od vývojářů Ionide a F# komunitou v [Ionide Gitteru kanál](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="d156d-213">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d156d-214">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d156d-214">Next steps</span></span>

<span data-ttu-id="d156d-215">Další informace o F# a funkcí jazyka, podívejte se na [prohlídka F# ](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="d156d-215">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

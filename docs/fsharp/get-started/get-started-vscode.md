---
title: Začínáme s jazykem F# v editoru Visual Studio Code
description: Naučte se používat F# s Visual Studio Code a sadou modulů plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 2802438144eb2352c3abeeccfc126b16c6a87d8f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204916"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="dd60b-103">Začínáme s jazykem F# v editoru Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dd60b-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="dd60b-104">Můžete psát F# v [Visual Studio Code](https://code.visualstudio.com) s [modulem plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) a získat tak skvělé prostředí integrovaného vývojového prostředí (IDE) pro více platforem pomocí technologie IntelliSense a refaktoringu kódu.</span><span class="sxs-lookup"><span data-stu-id="dd60b-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and code refactorings.</span></span> <span data-ttu-id="dd60b-105">Další informace o modulu plug-in najdete na [Ionide.IO](http://ionide.io) .</span><span class="sxs-lookup"><span data-stu-id="dd60b-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="dd60b-106">Chcete-li začít, ujistěte se, že máte [ F# a modul plug-in Ionide správně nainstalován](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="dd60b-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="create-your-first-project-with-ionide"></a><span data-ttu-id="dd60b-107">Vytvoření prvního projektu pomocí Ionide</span><span class="sxs-lookup"><span data-stu-id="dd60b-107">Create your first project with Ionide</span></span>

<span data-ttu-id="dd60b-108">Chcete-li vytvořit F# nový projekt, otevřete příkazový řádek a vytvořte nový projekt s .NET Core CLI:</span><span class="sxs-lookup"><span data-stu-id="dd60b-108">To create a new F# project, open a command line and create a new project with the .NET Core CLI:</span></span>

```dotnetcli
dotnet new console -lang F# -o FirstIonideProject
```

<span data-ttu-id="dd60b-109">Po dokončení změňte adresář na projekt a otevřete Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="dd60b-109">Once it completes, change directory to the project and open Visual Studio Code:</span></span>

```console
cd FirstIonideProject
code .
```

<span data-ttu-id="dd60b-110">Po načtení projektu na Visual Studio Code byste měli vidět podokno F# Průzkumník řešení na levé straně okna otevřené.</span><span class="sxs-lookup"><span data-stu-id="dd60b-110">After the project loads on Visual Studio Code, you should see the F# Solution Explorer pane on the left-hand side of your window open.</span></span> <span data-ttu-id="dd60b-111">To znamená, že Ionide úspěšně zavedl projekt, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="dd60b-111">This means Ionide has successfully loaded the project you just created.</span></span> <span data-ttu-id="dd60b-112">Můžete napsat kód v editoru před tímto bodem v čase, ale jakmile k tomu dojde, všechno se načetlo.</span><span class="sxs-lookup"><span data-stu-id="dd60b-112">You can write code in the editor before this point in time, but once this happens, everything has finished loading.</span></span>

## <a name="configure-f-interactive"></a><span data-ttu-id="dd60b-113">Konfigurovat F# interaktivní</span><span class="sxs-lookup"><span data-stu-id="dd60b-113">Configure F# interactive</span></span>

<span data-ttu-id="dd60b-114">Nejdřív zajistěte, aby bylo skriptování .NET Core výchozím skriptovacím prostředím:</span><span class="sxs-lookup"><span data-stu-id="dd60b-114">First, ensure that .NET Core scripting is your default scripting environment:</span></span>

1. <span data-ttu-id="dd60b-115">Otevřete nastavení Visual Studio Code ( **předvolby** > **kódu** > **Nastavení**).</span><span class="sxs-lookup"><span data-stu-id="dd60b-115">Open the Visual Studio Code settings (**Code** > **Preferences** > **Settings**).</span></span>
1. <span data-ttu-id="dd60b-116">Vyhledejte termín  **F# skriptu**.</span><span class="sxs-lookup"><span data-stu-id="dd60b-116">Search for the term **F# Script**.</span></span>
1. <span data-ttu-id="dd60b-117">Klikněte na zaškrtávací políčko, které říká **FSharp: použijte skripty sady SDK**.</span><span class="sxs-lookup"><span data-stu-id="dd60b-117">Click the checkbox that says **FSharp: use SDK scripts**.</span></span>

<span data-ttu-id="dd60b-118">V současné době je to nezbytné kvůli tomu, že v .NET Framework skriptování založeném na, které nefungují s skriptováním .NET Core, se v současnosti vyžaduje, aby služba Ionide v současné době zajistila tuto zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="dd60b-118">This is currently necessary due to some legacy behaviors in .NET Framework-based scripting that don't work with .NET Core scripting, and Ionide is currently striving for that backwards compatibility.</span></span> <span data-ttu-id="dd60b-119">V budoucnu se skriptování .NET Core stane výchozím nastavením.</span><span class="sxs-lookup"><span data-stu-id="dd60b-119">In the future, .NET Core scripting will become the default.</span></span>

### <a name="write-your-first-script"></a><span data-ttu-id="dd60b-120">Napište svůj první skript.</span><span class="sxs-lookup"><span data-stu-id="dd60b-120">Write your first script</span></span>

<span data-ttu-id="dd60b-121">Jakmile nakonfigurujete Visual Studio Code pro použití skriptování .NET Core, přejděte do zobrazení Průzkumníka v Visual Studio Code a vytvořte nový soubor.</span><span class="sxs-lookup"><span data-stu-id="dd60b-121">Once you've configured Visual Studio Code to use .NET Core scripting, navigate to the Explorer view in Visual Studio Code and create a new file.</span></span> <span data-ttu-id="dd60b-122">Pojmenujte ho *MyFirstScript. fsx*.</span><span class="sxs-lookup"><span data-stu-id="dd60b-122">Name it *MyFirstScript.fsx*.</span></span>

<span data-ttu-id="dd60b-123">Nyní do něj přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="dd60b-123">Now add the following code to it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="dd60b-124">Tato funkce převede slovo na formu [prasečí Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="dd60b-124">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="dd60b-125">Dalším krokem je vyhodnotit ho pomocí F# Interactive (fsi).</span><span class="sxs-lookup"><span data-stu-id="dd60b-125">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="dd60b-126">Zvýrazněte celou funkci (měla by být 11 řádků dlouhá).</span><span class="sxs-lookup"><span data-stu-id="dd60b-126">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="dd60b-127">Až se zvýrazní, stiskněte klávesu **ALT** a stiskněte **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="dd60b-127">Once it's highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="dd60b-128">Všimněte si, že se v dolní části obrazovky zobrazí okno terminálu, které by mělo vypadat podobně jako toto:</span><span class="sxs-lookup"><span data-stu-id="dd60b-128">You'll notice a terminal window pop up on the bottom of the screen, and it should look similar to this:</span></span>

![Příklad F# interaktivního výstupu s Ionide](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="dd60b-130">To mělo tři věci:</span><span class="sxs-lookup"><span data-stu-id="dd60b-130">This did three things:</span></span>

1. <span data-ttu-id="dd60b-131">Spustil se proces FSI.</span><span class="sxs-lookup"><span data-stu-id="dd60b-131">It started the FSI process.</span></span>
2. <span data-ttu-id="dd60b-132">Odeslali jsme kód, který jste zvýraznili v rámci procesu FSI.</span><span class="sxs-lookup"><span data-stu-id="dd60b-132">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="dd60b-133">Proces FSI vyhodnotil kód, který jste odeslali.</span><span class="sxs-lookup"><span data-stu-id="dd60b-133">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="dd60b-134">Vzhledem k tomu, že jste přeposlali [funkci](../language-reference/functions/index.md), můžete tuto funkci nyní volat pomocí FSI!</span><span class="sxs-lookup"><span data-stu-id="dd60b-134">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="dd60b-135">V interaktivním okně zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="dd60b-135">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="dd60b-136">Měl by se zobrazit následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="dd60b-136">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="dd60b-137">Teď zkusíme použít samohlásku jako první písmeno.</span><span class="sxs-lookup"><span data-stu-id="dd60b-137">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="dd60b-138">Zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="dd60b-138">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="dd60b-139">Měl by se zobrazit následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="dd60b-139">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="dd60b-140">Zdá se, že funkce funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="dd60b-140">The function appears to be working as expected.</span></span> <span data-ttu-id="dd60b-141">Gratulujeme, právě jste napsali F# svou první funkci v Visual Studio Code a vyhodnotili ji pomocí FSI!</span><span class="sxs-lookup"><span data-stu-id="dd60b-141">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="dd60b-142">Jak jste si všimli, řádky v FSI se ukončí s `;;`.</span><span class="sxs-lookup"><span data-stu-id="dd60b-142">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="dd60b-143">Důvodem je to, že FSI umožňuje zadat více řádků.</span><span class="sxs-lookup"><span data-stu-id="dd60b-143">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="dd60b-144">`;;` na konci umožňuje FSI ví, že je kód dokončen.</span><span class="sxs-lookup"><span data-stu-id="dd60b-144">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="dd60b-145">Vysvětlení kódu</span><span class="sxs-lookup"><span data-stu-id="dd60b-145">Explaining the code</span></span>

<span data-ttu-id="dd60b-146">Pokud si nejste jistí, co kód skutečně dělá, tady je krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="dd60b-146">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="dd60b-147">Jak vidíte, `toPigLatin` je funkce, která jako svůj vstup přebírá slovo, a převede ho na reprezentaci tohoto slova v latince.</span><span class="sxs-lookup"><span data-stu-id="dd60b-147">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="dd60b-148">Tato pravidla jsou následující:</span><span class="sxs-lookup"><span data-stu-id="dd60b-148">The rules for this are as follows:</span></span>

<span data-ttu-id="dd60b-149">Pokud první znak ve slově začíná znakem samohlásky, přidejte na konec slova "yay".</span><span class="sxs-lookup"><span data-stu-id="dd60b-149">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="dd60b-150">Pokud nezačíná znakem samohlásky, přesuňte tento první znak na konec slova a přidejte do něj "Ay".</span><span class="sxs-lookup"><span data-stu-id="dd60b-150">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="dd60b-151">Možná jste si všimli, že v FSI máte následující:</span><span class="sxs-lookup"><span data-stu-id="dd60b-151">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="dd60b-152">To uvádí, že `toPigLatin` je funkce, která přebírá `string` jako vstup (nazývaný `word`), a vrací další `string`.</span><span class="sxs-lookup"><span data-stu-id="dd60b-152">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="dd60b-153">To se označuje jako [Signatura typu funkce](https://fsharpforfunandprofit.com/posts/function-signatures/), základní část klíče F# , která je základem pro porozumění F# kódu.</span><span class="sxs-lookup"><span data-stu-id="dd60b-153">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="dd60b-154">Všimněte si také, že najedete myší na funkci v Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dd60b-154">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="dd60b-155">V těle funkce si všimnete dvou různých částí:</span><span class="sxs-lookup"><span data-stu-id="dd60b-155">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="dd60b-156">Vnitřní funkce označovaná jako `isVowel`, která určuje, zda daný znak (`c`) je znak samohlásky kontrolou, pokud odpovídá jednomu ze zadaných vzorů přes [porovnávání vzorů](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="dd60b-156">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="dd60b-157">Výraz [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) , který kontroluje, zda je první znak samohlásky, a vytvoří vrácenou hodnotu ze vstupních znaků na základě toho, zda byl první znak samohláskou nebo nikoli:</span><span class="sxs-lookup"><span data-stu-id="dd60b-157">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="dd60b-158">Tok `toPigLatin` je tedy:</span><span class="sxs-lookup"><span data-stu-id="dd60b-158">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="dd60b-159">Zkontroluje, jestli je první znak vstupního slova samohláskou.</span><span class="sxs-lookup"><span data-stu-id="dd60b-159">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="dd60b-160">Pokud je, připojte k konci slova "yay".</span><span class="sxs-lookup"><span data-stu-id="dd60b-160">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="dd60b-161">V opačném případě přesuňte tento první znak na konec slova a přidejte do něj "Ay".</span><span class="sxs-lookup"><span data-stu-id="dd60b-161">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="dd60b-162">K dispozici je jedno konečné oznámení: neexistuje žádná explicitní instrukce pro návrat z funkce, na rozdíl od mnoha dalších jazyků.</span><span class="sxs-lookup"><span data-stu-id="dd60b-162">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="dd60b-163">Důvodem je, F# že je založen na výrazu a poslední výraz v těle funkce je návratová hodnota.</span><span class="sxs-lookup"><span data-stu-id="dd60b-163">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="dd60b-164">Vzhledem k tomu, že `if..then..else` je sama o sobě výraz, v závislosti na vstupní hodnotě se vrátí tělo bloku `then` nebo tělo `else` bloku.</span><span class="sxs-lookup"><span data-stu-id="dd60b-164">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a><span data-ttu-id="dd60b-165">Vypnutí konzolové aplikace na prasečí generátor v latince</span><span class="sxs-lookup"><span data-stu-id="dd60b-165">Turn the console app into a Pig Latin generator</span></span>

<span data-ttu-id="dd60b-166">Předchozí části tohoto článku ukázaly běžný první krok při psaní F# kódu: zápis počáteční funkce a interaktivní spuštění pomocí FSI.</span><span class="sxs-lookup"><span data-stu-id="dd60b-166">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="dd60b-167">To se označuje jako vývoj řízený REPL, kde [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) představuje "Read-Evaluate-Print Loop".</span><span class="sxs-lookup"><span data-stu-id="dd60b-167">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="dd60b-168">Je to skvělý způsob, jak experimentovat s funkčnostmi, dokud nebudete mít nějakou práci.</span><span class="sxs-lookup"><span data-stu-id="dd60b-168">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="dd60b-169">Dalším krokem v REPLém vývojovém prostředí F# je přesun pracovního kódu do implementačního souboru.</span><span class="sxs-lookup"><span data-stu-id="dd60b-169">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="dd60b-170">Poté může být zkompilován F# kompilátorem do sestavení, které lze spustit.</span><span class="sxs-lookup"><span data-stu-id="dd60b-170">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="dd60b-171">Začněte tím, že otevřete soubor *program. FS* , který jste vytvořili dříve, pomocí .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="dd60b-171">To begin, open the *Program.fs* file that you created earlier with the .NET Core CLI.</span></span> <span data-ttu-id="dd60b-172">Všimněte si, že v něm už je nějaký kód.</span><span class="sxs-lookup"><span data-stu-id="dd60b-172">You'll notice that some code is already in there.</span></span>

<span data-ttu-id="dd60b-173">Dále vytvořte nový [`module`](../language-reference/modules.md) nazvaný `PigLatin` a zkopírujte `toPigLatin` funkci, kterou jste předtím vytvořili.</span><span class="sxs-lookup"><span data-stu-id="dd60b-173">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function you created earlier into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="dd60b-174">Tento modul by měl být nad `main`ovou funkcí a pod deklarací `open System`.</span><span class="sxs-lookup"><span data-stu-id="dd60b-174">This module should be above the `main` function and below the `open System` declaration.</span></span> <span data-ttu-id="dd60b-175">Pořadí deklarací v F#nástroji, takže je nutné definovat funkci před jejich voláním v souboru.</span><span class="sxs-lookup"><span data-stu-id="dd60b-175">Order of declarations matters in F#, so you'll need to define the function before you call it in a file.</span></span>

<span data-ttu-id="dd60b-176">Nyní ve funkci `main` volejte funkci generátoru latince pro prase na argumenty:</span><span class="sxs-lookup"><span data-stu-id="dd60b-176">Now, in the `main` function, call your Pig Latin generator function on the arguments:</span></span>

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

<span data-ttu-id="dd60b-177">Nyní můžete spustit konzolovou aplikaci z příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="dd60b-177">Now you can run your console app from the command line:</span></span>

```console
dotnet run apple banana
```

<span data-ttu-id="dd60b-178">A uvidíte, že výstup má stejný výsledek jako soubor skriptu, ale tentokrát jako běžící program.</span><span class="sxs-lookup"><span data-stu-id="dd60b-178">And you'll see that it outputs the same result as your script file, but this time as a running program!</span></span>

## <a name="troubleshooting-ionide"></a><span data-ttu-id="dd60b-179">Řešení potíží s Ionide</span><span class="sxs-lookup"><span data-stu-id="dd60b-179">Troubleshooting Ionide</span></span>

<span data-ttu-id="dd60b-180">Tady je několik způsobů, jak můžete řešit některé problémy, se kterými se můžete setkat:</span><span class="sxs-lookup"><span data-stu-id="dd60b-180">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="dd60b-181">Chcete-li získat funkce pro úpravu kódu Ionide, F# je třeba uložit soubory na disk a do složky, která je otevřena v pracovním prostoru Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dd60b-181">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
1. <span data-ttu-id="dd60b-182">Pokud jste provedli změny v systému nebo nastavili požadavky Ionide Visual Studio Code otevřít, restartujte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dd60b-182">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
1. <span data-ttu-id="dd60b-183">Pokud máte v adresářích projektu neplatné znaky, Ionide nemusí fungovat.</span><span class="sxs-lookup"><span data-stu-id="dd60b-183">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="dd60b-184">Pokud se jedná o tento případ, přejmenujte adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="dd60b-184">Rename your project directories if this is the case.</span></span>
1. <span data-ttu-id="dd60b-185">Pokud žádný z příkazů Ionide nefunguje, zkontrolujte [Visual Studio Code vazby](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) klíčů a podívejte se, jestli je nepřepisujete havárií.</span><span class="sxs-lookup"><span data-stu-id="dd60b-185">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
1. <span data-ttu-id="dd60b-186">Pokud je Ionide na vašem počítači poškozená a žádná z výše uvedených kroků nevyřešila váš problém, zkuste na svém počítači odebrat `ionide-fsharp` adresář a znovu sadu modulů plug-in.</span><span class="sxs-lookup"><span data-stu-id="dd60b-186">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>
1. <span data-ttu-id="dd60b-187">Pokud se projekt nepovedlo načíst ( F# Průzkumník řešení to uvidí), klikněte pravým tlačítkem na tento projekt a kliknutím na **Zobrazit podrobnosti** Získejte další diagnostické informace.</span><span class="sxs-lookup"><span data-stu-id="dd60b-187">If a project failed to load (the F# Solution Explorer will show this), right-click on that project and click **See details** to get more diagnostic info.</span></span>

<span data-ttu-id="dd60b-188">Ionide je open source projekt sestavený a spravovaný členy F# komunity.</span><span class="sxs-lookup"><span data-stu-id="dd60b-188">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="dd60b-189">Oznamte prosím problémy a nebojte se přispět v [úložišti GitHub ionide-VSCode-FSharp](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="dd60b-189">Please report issues and feel free to contribute at the [ionide-vscode-fsharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="dd60b-190">Můžete si také vyžádat další pomoc od vývojářů Ionide a F# komunity v [kanálu gitteru Ionide](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="dd60b-190">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="dd60b-191">Další kroky</span><span class="sxs-lookup"><span data-stu-id="dd60b-191">Next steps</span></span>

<span data-ttu-id="dd60b-192">Chcete-li získat F# Další informace o funkcích jazyka, Projděte si [část F# ](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="dd60b-192">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

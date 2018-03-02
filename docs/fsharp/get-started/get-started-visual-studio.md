---
title: "Začínáme s F # v sadě Visual Studio"
description: "Další informace o použití F # pomocí sady Visual Studio."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: 818bf50507a88e1d765da8d0505ed8da4790b71f
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="58f5e-104">Začínáme s F # v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="58f5e-104">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="58f5e-105">F # a nástrojů Visual F # jsou podporovány v prostředí Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="58f5e-105">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>  <span data-ttu-id="58f5e-106">Pokud chcete začít, měli byste [Visual Studio Stáhnout](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), pokud jste tak ještě neučinili.</span><span class="sxs-lookup"><span data-stu-id="58f5e-106">To begin, you should [download Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), if you haven't already.</span></span>  <span data-ttu-id="58f5e-107">Tento článek používá Visual Studio 2017 Community Edition, ale můžete použít F # verzí podle svého výběru.</span><span class="sxs-lookup"><span data-stu-id="58f5e-107">This article uses the Visual Studio 2017 Community Edition, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="58f5e-108">Instalace F #</span><span class="sxs-lookup"><span data-stu-id="58f5e-108">Installing F#</span></span> #

<span data-ttu-id="58f5e-109">Pokud probíhá stahování programu sady Visual Studio poprvé, bude nejprve nainstalovat Instalační program sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="58f5e-109">If you're downloading Visual Studio for the first time, it will first install the Visual Studio installer.</span></span>  <span data-ttu-id="58f5e-110">Všechny verze aplikace Visual Studio 2017 nainstalujte z instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="58f5e-110">Install any version of Visual Studio 2017 from the installer.</span></span> <span data-ttu-id="58f5e-111">Pokud je již nainstalováno, klikněte na tlačítko **upravit**.</span><span class="sxs-lookup"><span data-stu-id="58f5e-111">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="58f5e-112">Dále se zobrazí seznam úloh.</span><span class="sxs-lookup"><span data-stu-id="58f5e-112">You'll next see a list of Workloads.</span></span> <span data-ttu-id="58f5e-113">Můžete nainstalovat F # do některého z následujících úloh:</span><span class="sxs-lookup"><span data-stu-id="58f5e-113">You can install F# through any of the following workloads:</span></span>

|<span data-ttu-id="58f5e-114">zatížení</span><span class="sxs-lookup"><span data-stu-id="58f5e-114">Workload</span></span>|<span data-ttu-id="58f5e-115">Akce</span><span class="sxs-lookup"><span data-stu-id="58f5e-115">Action</span></span>|
|--------|------|
| <span data-ttu-id="58f5e-116">Vývoj pro různé platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="58f5e-116">.NET Core cross-platform development</span></span> | <span data-ttu-id="58f5e-117">Ve výchozím nastavení je nainstalovaná žádná akce - F #</span><span class="sxs-lookup"><span data-stu-id="58f5e-117">No action - F# is installed by default</span></span> |
| <span data-ttu-id="58f5e-118">ASP.NET a vývoje</span><span class="sxs-lookup"><span data-stu-id="58f5e-118">ASP.NET and web development</span></span> | <span data-ttu-id="58f5e-119">Ve výchozím nastavení je nainstalovaná žádná akce - F #</span><span class="sxs-lookup"><span data-stu-id="58f5e-119">No action - F# is installed by default</span></span> |
| <span data-ttu-id="58f5e-120">Vývoj pro Azure</span><span class="sxs-lookup"><span data-stu-id="58f5e-120">Azure development</span></span> | <span data-ttu-id="58f5e-121">Ve výchozím nastavení je nainstalovaná žádná akce - F #</span><span class="sxs-lookup"><span data-stu-id="58f5e-121">No action - F# is installed by default</span></span> |
| <span data-ttu-id="58f5e-122">Mobilní vývoj pomocí rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="58f5e-122">Mobile development with .NET</span></span> | <span data-ttu-id="58f5e-123">Ve výchozím nastavení je nainstalovaná žádná akce - F #</span><span class="sxs-lookup"><span data-stu-id="58f5e-123">No action - F# is installed by default</span></span> |
| <span data-ttu-id="58f5e-124">Aplikace pro datové vědy a analýzy</span><span class="sxs-lookup"><span data-stu-id="58f5e-124">Data science and analytical applications</span></span> | <span data-ttu-id="58f5e-125">Ve výchozím nastavení je nainstalovaná žádná akce - F #</span><span class="sxs-lookup"><span data-stu-id="58f5e-125">No action - F# is installed by default</span></span> |
| <span data-ttu-id="58f5e-126">Vývoj aplikací rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="58f5e-126">.NET desktop development</span></span> | <span data-ttu-id="58f5e-127">Vyberte **podporu klientů jazyka F #** z pravé strany</span><span class="sxs-lookup"><span data-stu-id="58f5e-127">Select **F# desktop language support** from the right-hand side</span></span> |
| <span data-ttu-id="58f5e-128">Ukládání a zpracování dat</span><span class="sxs-lookup"><span data-stu-id="58f5e-128">Data storage and processing</span></span> | <span data-ttu-id="58f5e-129">Vyberte **podporu klientů jazyka F #** z pravé strany</span><span class="sxs-lookup"><span data-stu-id="58f5e-129">Select **F# desktop language support** from the right-hand side</span></span> |

<span data-ttu-id="58f5e-130">Klikněte na tlačítko **upravit** v pravé straně dole.</span><span class="sxs-lookup"><span data-stu-id="58f5e-130">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="58f5e-131">Nainstaluje všechny objekty, které jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="58f5e-131">This will install everything you have selected.</span></span>  <span data-ttu-id="58f5e-132">Pak můžete otevřít Visual Studio 2017 s podporou jazyka F # kliknutím **spusťte**.</span><span class="sxs-lookup"><span data-stu-id="58f5e-132">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="58f5e-133">Vytvoření aplikace konzoly</span><span class="sxs-lookup"><span data-stu-id="58f5e-133">Creating a console application</span></span>

<span data-ttu-id="58f5e-134">Jeden z nejzákladnější projektů v sadě Visual Studio je konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="58f5e-134">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="58f5e-135">Chcete-li to provést.</span><span class="sxs-lookup"><span data-stu-id="58f5e-135">Here's how to do it.</span></span>  <span data-ttu-id="58f5e-136">Po otevřete Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="58f5e-136">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="58f5e-137">Na **soubor** nabídky, přejděte na příkaz **nový**a potom zvolte **projektu**.</span><span class="sxs-lookup"><span data-stu-id="58f5e-137">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="58f5e-138">V nový projekt dialogové okno, v části **šablony**, měli byste vidět **Visual F #**.</span><span class="sxs-lookup"><span data-stu-id="58f5e-138">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="58f5e-139">Výběrem této zobrazíte šablony F #.</span><span class="sxs-lookup"><span data-stu-id="58f5e-139">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="58f5e-140">Vyberte buď **.NET základní konzolovou aplikaci** nebo **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="58f5e-140">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="58f5e-141">Vyberte **nevadí** tlačítko pro vytvoření projektu F #!</span><span class="sxs-lookup"><span data-stu-id="58f5e-141">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="58f5e-142">Teď byste měli vidět projektu F # v Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="58f5e-142">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="58f5e-143">Psaní kódu</span><span class="sxs-lookup"><span data-stu-id="58f5e-143">Writing your code</span></span>

<span data-ttu-id="58f5e-144">Můžeme začít napsáním nějakého kódu.</span><span class="sxs-lookup"><span data-stu-id="58f5e-144">Let's get started by writing some code first.</span></span>  <span data-ttu-id="58f5e-145">Ujistěte se, že `Program.fs` soubor je otevřený a poté nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="58f5e-145">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="58f5e-146">V předchozí ukázce kódu, funkce `square` byla definována což trvá vstup s názvem `x` a vynásobí samostatně.</span><span class="sxs-lookup"><span data-stu-id="58f5e-146">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="58f5e-147">Protože F # používá [odvození typu](../language-reference/type-inference.md), typ `x` není potřeba zadat.</span><span class="sxs-lookup"><span data-stu-id="58f5e-147">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="58f5e-148">Kompilátor jazyka F # rozumí typy, kde je platný násobení a přiřadí typ k `x` podle toho, jaký `square` je volána.</span><span class="sxs-lookup"><span data-stu-id="58f5e-148">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="58f5e-149">Pokud se ukazatel myši přesunete `square`, měli byste vidět následující:</span><span class="sxs-lookup"><span data-stu-id="58f5e-149">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="58f5e-150">Toto je, co se označuje jako typ podpis funkce.</span><span class="sxs-lookup"><span data-stu-id="58f5e-150">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="58f5e-151">Může být číst takto: "čtvercovou je funkce, která přebírá celé číslo s názvem x a vytváří celé číslo".</span><span class="sxs-lookup"><span data-stu-id="58f5e-151">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="58f5e-152">Všimněte si, že jste dali kompilátor `square` `int` typ prozatím - totiž násobení není obecná napříč *všechny* typy, ale spíše je obecný napříč uzavřené sadu typů.</span><span class="sxs-lookup"><span data-stu-id="58f5e-152">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="58f5e-153">Zaznamenání kompilátoru F # `int` na tomto bodu, ale upraví podpis typu při volání `square` s jiným typ vstupu, například `float`.</span><span class="sxs-lookup"><span data-stu-id="58f5e-153">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="58f5e-154">Jiné funkce, `main`, je definován, který je upraven pomocí `EntryPoint` atribut říct kompilátor jazyka F # spuštění tohoto programu by se měl spustit existuje.</span><span class="sxs-lookup"><span data-stu-id="58f5e-154">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="58f5e-155">Postupuje stejné konvence jako ostatní [programovací jazyky C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde argumenty příkazového řádku se dá předat do této funkce a je vrácen kód celé číslo (obvykle `0`).</span><span class="sxs-lookup"><span data-stu-id="58f5e-155">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="58f5e-156">Je v této funkci, která se nazývá `square` funkce s argument `12`.</span><span class="sxs-lookup"><span data-stu-id="58f5e-156">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="58f5e-157">Kompilátor jazyka F # poté přiřadí typ `square` být `int -> int` (to znamená, funkci, která přebírá `int` a vytváří `int`).</span><span class="sxs-lookup"><span data-stu-id="58f5e-157">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="58f5e-158">Volání `printfn` je formátovaný tisk funkci, která používá řetězec formátu, podobně jako programovací jazyky C-style, parametry, které odpovídá platformám zadaným v řetězec formátu a potom zobrazí výsledek a nový řádek.</span><span class="sxs-lookup"><span data-stu-id="58f5e-158">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="58f5e-159">Spuštěním kódu</span><span class="sxs-lookup"><span data-stu-id="58f5e-159">Running your code</span></span>

<span data-ttu-id="58f5e-160">Můžete spustit kód a zobrazte výsledky stisknutím **ctrl + f5**.</span><span class="sxs-lookup"><span data-stu-id="58f5e-160">You can run the code and see results by pressing **ctrl-f5**.</span></span>  <span data-ttu-id="58f5e-161">Tento program se spustí bez ladění a umožňuje zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="58f5e-161">This will run the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="58f5e-162">Alternativně můžete **ladění** nabídka nejvyšší položku v sadě Visual Studio a zvolte **spustit bez ladění**.</span><span class="sxs-lookup"><span data-stu-id="58f5e-162">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="58f5e-163">Teď byste měli vidět následující vytisknout do okna konzoly, která sada Visual Studio odebrány až:</span><span class="sxs-lookup"><span data-stu-id="58f5e-163">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="58f5e-164">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="58f5e-164">Congratulations!</span></span>  <span data-ttu-id="58f5e-165">Jste vytvořili svůj první projekt F # v sadě Visual Studio, zapisovat že funkce F # vytisknout výsledky volání této funkce a spusťte projekt zobrazíte některé výsledky.</span><span class="sxs-lookup"><span data-stu-id="58f5e-165">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="58f5e-166">Pomocí F # interaktivní</span><span class="sxs-lookup"><span data-stu-id="58f5e-166">Using F# Interactive</span></span>

<span data-ttu-id="58f5e-167">Jedním z nejlepší funkce z Visual F # nástrojů v sadě Visual Studio je interaktivních okna F #.</span><span class="sxs-lookup"><span data-stu-id="58f5e-167">One of the best features of the Visual F# tooling in Visual Studio is the F# Interactive Window.</span></span>  <span data-ttu-id="58f5e-168">Umožňuje odeslat kód prostřednictvím procesu, kde můžete volat tento kód a zobrazit výsledky interaktivně.</span><span class="sxs-lookup"><span data-stu-id="58f5e-168">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="58f5e-169">Chcete-li začít používat ji, zvýrazněte `square` funkci definovanou v kódu.</span><span class="sxs-lookup"><span data-stu-id="58f5e-169">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="58f5e-170">V dalším kroku uložení **Alt** klíč a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="58f5e-170">Next, hold the **Alt** key and press **Enter**.</span></span>  <span data-ttu-id="58f5e-171">To spustí kód v okně interaktivní F #.</span><span class="sxs-lookup"><span data-stu-id="58f5e-171">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="58f5e-172">Měli byste vidět F # interaktivních okna zobrazují se v něm následující:</span><span class="sxs-lookup"><span data-stu-id="58f5e-172">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="58f5e-173">Zobrazí se stejným podpisem funkce pro `square` funkce, které jste předtím viděli při při přechodu myší nad funkce.</span><span class="sxs-lookup"><span data-stu-id="58f5e-173">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="58f5e-174">Protože `square` je nyní definována v F # interaktivní proces, můžete ji volat s různými hodnotami:</span><span class="sxs-lookup"><span data-stu-id="58f5e-174">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="58f5e-175">Tato funkce spustí, váže výsledek na nový název `it`a zobrazí typu a hodnoty `it`.</span><span class="sxs-lookup"><span data-stu-id="58f5e-175">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="58f5e-176">Všimněte si, že musí být ukončen každý řádek s `;;`.</span><span class="sxs-lookup"><span data-stu-id="58f5e-176">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="58f5e-177">Toto je, jak F # interaktivní zná dokončení volání funkce.</span><span class="sxs-lookup"><span data-stu-id="58f5e-177">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="58f5e-178">Můžete také definovat nové funkce v F # interaktivní:</span><span class="sxs-lookup"><span data-stu-id="58f5e-178">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="58f5e-179">Výše definuje novou funkci, `isOdd`, které trvá `int` a kontroluje, zda se jedná o liché!</span><span class="sxs-lookup"><span data-stu-id="58f5e-179">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span> <span data-ttu-id="58f5e-180">Můžete volat této funkci můžete zjistit, co vrací s různými vstupy.</span><span class="sxs-lookup"><span data-stu-id="58f5e-180">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="58f5e-181">Můžete volat funkce v rámci volání funkce:</span><span class="sxs-lookup"><span data-stu-id="58f5e-181">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="58f5e-182">Můžete také [operátor kanálu dopředného](../language-reference/symbol-and-operator-reference/index.md) do kanálu hodnotu do dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="58f5e-182">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="58f5e-183">Operátor kanálu dopředného a další, jsou popsané v dalších kurzech.</span><span class="sxs-lookup"><span data-stu-id="58f5e-183">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="58f5e-184">Toto je pouze balíčku glimpse do co můžete dělat s F # interaktivní.</span><span class="sxs-lookup"><span data-stu-id="58f5e-184">This is only a glimpse into what you can do with F# Interactive.</span></span> <span data-ttu-id="58f5e-185">Další informace, podívejte se na [interaktivní programování s F #](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="58f5e-185">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="58f5e-186">Další kroky</span><span class="sxs-lookup"><span data-stu-id="58f5e-186">Next steps</span></span>

<span data-ttu-id="58f5e-187">Pokud jste to ještě neudělali, podívejte se [prohlídka z F #](../tour.md), které zahrnuje některé základní funkce jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="58f5e-187">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="58f5e-188">Bude vám poskytl přehled některých možností F # a zadejte ukázky dostatečným kódu, které můžete zkopírovat do sady Visual Studio a spustit.</span><span class="sxs-lookup"><span data-stu-id="58f5e-188">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="58f5e-189">Existují také některé skvělé externím prostředkům, můžete použít, showcased v [Průvodce F #](../index.md).</span><span class="sxs-lookup"><span data-stu-id="58f5e-189">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="58f5e-190">Viz také</span><span class="sxs-lookup"><span data-stu-id="58f5e-190">See also</span></span>
 [<span data-ttu-id="58f5e-191">Visual F#</span><span class="sxs-lookup"><span data-stu-id="58f5e-191">Visual F#</span></span>](index.md)  
 [<span data-ttu-id="58f5e-192">Prohlídka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="58f5e-192">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="58f5e-193">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="58f5e-193">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="58f5e-194">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="58f5e-194">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="58f5e-195">Referenční dokumentace symbolů a – operátor</span><span class="sxs-lookup"><span data-stu-id="58f5e-195">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  

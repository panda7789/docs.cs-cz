---
title: 'Začínáme s F # v sadě Visual Studio pro Mac'
description: 'Další informace o použití F # pomocí sady Visual Studio for Mac.'
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 232235952ec43f682dc21de4ef7dde9c1b553364
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="193b4-103">Začínáme s F # v sadě Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="193b4-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="193b4-104">F # a nástrojů Visual F # jsou podporovány v sadě Visual Studio pro Mac IDE.</span><span class="sxs-lookup"><span data-stu-id="193b4-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span>  <span data-ttu-id="193b4-105">Pokud chcete začít, měli byste [stažení sady Visual Studio pro Mac](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), pokud jste tak ještě neučinili.</span><span class="sxs-lookup"><span data-stu-id="193b4-105">To begin, you should [download Visual Studio for Mac](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), if you haven't already.</span></span>  <span data-ttu-id="193b4-106">Tento článek používá 2017 pro komunity Visual Studio pro Mac, ale můžete použít F # verzí podle svého výběru.</span><span class="sxs-lookup"><span data-stu-id="193b4-106">This article uses the Visual Studio Community 2017 for Mac, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="193b4-107">Instalace F #</span><span class="sxs-lookup"><span data-stu-id="193b4-107">Installing F#</span></span> #

<span data-ttu-id="193b4-108">Po stažení sady Visual Studio pro Mac, vás vyzve k výběru chcete nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="193b4-108">After downloading Visual Studio for Mac, it will prompt you to choose what you want to install.</span></span>  <span data-ttu-id="193b4-109">Pro účely tohoto článku jsme se ponechat výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="193b4-109">For the purposes of this article we will be leaving the defaults.</span></span>  <span data-ttu-id="193b4-110">Na rozdíl od Visual Studio pro Windows není potřeba konkrétně nainstalovat podporu F #.</span><span class="sxs-lookup"><span data-stu-id="193b4-110">In contrast to Visual Studio for Windows, you do not need to specifically install F# support.</span></span>  <span data-ttu-id="193b4-111">Stiskněte klávesu "Instalaci", aby bylo možné pokračovat.</span><span class="sxs-lookup"><span data-stu-id="193b4-111">Press "Install" to proceed.</span></span>

<span data-ttu-id="193b4-112">Po dokončení instalace, vyberte "Spusťte Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="193b4-112">After the install completes, choose "Start Visual Studio".</span></span>  <span data-ttu-id="193b4-113">Také ho můžete spustit v systému macOS prostřednictvím funkce hledání.</span><span class="sxs-lookup"><span data-stu-id="193b4-113">You can also launch it through Finder on macOS.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="193b4-114">Vytvoření aplikace konzoly</span><span class="sxs-lookup"><span data-stu-id="193b4-114">Creating a console application</span></span>

<span data-ttu-id="193b4-115">Jeden z nejzákladnější projektů v sadě Visual Studio pro Mac je konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="193b4-115">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="193b4-116">Chcete-li to provést.</span><span class="sxs-lookup"><span data-stu-id="193b4-116">Here's how to do it.</span></span>  <span data-ttu-id="193b4-117">Po otevřete Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="193b4-117">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="193b4-118">Na **soubor** nabídky, přejděte na příkaz **nové řešení**.</span><span class="sxs-lookup"><span data-stu-id="193b4-118">On the **File** menu, point to **New Solution**.</span></span>

2.  <span data-ttu-id="193b4-119">V dialogovém okně Nový projekt jsou 2 různé šablony pro konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="193b4-119">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="193b4-120">Je v části Další -> .NET, která cílí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="193b4-120">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="193b4-121">Jiné šablony je pod .NET Core -> aplikace, která cílí na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="193b4-121">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="193b4-122">Buď šablona by měla fungovat pro účely tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="193b4-122">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="193b4-123">V části konzolovou aplikaci změňte C# na F # v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="193b4-123">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="193b4-124">Vyberte **Další** tlačítko Předat dál přesunout!</span><span class="sxs-lookup"><span data-stu-id="193b4-124">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="193b4-125">Pojmenujte projekt a zvolte možnosti, které chcete pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="193b4-125">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="193b4-126">Všimněte si, v podokně náhledu na stranu obrazovky, který se zobrazí strukturu adresáře, který bude vytvořen založené na vybrané možnosti.</span><span class="sxs-lookup"><span data-stu-id="193b4-126">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="193b4-127">Klikněte na tlačítko **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="193b4-127">Click **Create**.</span></span>  <span data-ttu-id="193b4-128">Teď byste měli vidět projektu F # v Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="193b4-128">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="193b4-129">Psaní kódu</span><span class="sxs-lookup"><span data-stu-id="193b4-129">Writing your code</span></span>

<span data-ttu-id="193b4-130">Můžeme začít napsáním nějakého kódu.</span><span class="sxs-lookup"><span data-stu-id="193b4-130">Let's get started by writing some code first.</span></span>  <span data-ttu-id="193b4-131">Ujistěte se, že `Program.fs` soubor je otevřený a poté nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="193b4-131">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="193b4-132">V předchozí ukázce kódu, funkce `square` byla definována což trvá vstup s názvem `x` a vynásobí samostatně.</span><span class="sxs-lookup"><span data-stu-id="193b4-132">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="193b4-133">Protože F # používá [odvození typu](../language-reference/type-inference.md), typ `x` není potřeba zadat.</span><span class="sxs-lookup"><span data-stu-id="193b4-133">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="193b4-134">Kompilátor jazyka F # rozumí typy, kde je platný násobení a přiřadí typ k `x` podle toho, jaký `square` je volána.</span><span class="sxs-lookup"><span data-stu-id="193b4-134">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="193b4-135">Pokud se ukazatel myši přesunete `square`, měli byste vidět následující:</span><span class="sxs-lookup"><span data-stu-id="193b4-135">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="193b4-136">Toto je, co se označuje jako typ podpis funkce.</span><span class="sxs-lookup"><span data-stu-id="193b4-136">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="193b4-137">Může být číst takto: "čtvercovou je funkce, která přebírá celé číslo s názvem x a vytváří celé číslo".</span><span class="sxs-lookup"><span data-stu-id="193b4-137">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="193b4-138">Všimněte si, že jste dali kompilátor `square` `int` typ prozatím - totiž násobení není obecná napříč *všechny* typy, ale spíše je obecný napříč uzavřené sadu typů.</span><span class="sxs-lookup"><span data-stu-id="193b4-138">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="193b4-139">Zaznamenání kompilátoru F # `int` na tomto bodu, ale upraví podpis typu při volání `square` s jiným typ vstupu, například `float`.</span><span class="sxs-lookup"><span data-stu-id="193b4-139">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="193b4-140">Jiné funkce, `main`, je definován, který je upraven pomocí `EntryPoint` atribut říct kompilátor jazyka F # spuštění tohoto programu by se měl spustit existuje.</span><span class="sxs-lookup"><span data-stu-id="193b4-140">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="193b4-141">Postupuje stejné konvence jako ostatní [programovací jazyky C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde argumenty příkazového řádku se dá předat do této funkce a je vrácen kód celé číslo (obvykle `0`).</span><span class="sxs-lookup"><span data-stu-id="193b4-141">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="193b4-142">Je v této funkci, která se nazývá `square` funkce s argument `12`.</span><span class="sxs-lookup"><span data-stu-id="193b4-142">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="193b4-143">Kompilátor jazyka F # poté přiřadí typ `square` být `int -> int` (to znamená, funkci, která přebírá `int` a vytváří `int`).</span><span class="sxs-lookup"><span data-stu-id="193b4-143">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="193b4-144">Volání `printfn` je formátovaný tisk funkci, která používá řetězec formátu, podobně jako programovací jazyky C-style, parametry, které odpovídá platformám zadaným v řetězec formátu a potom zobrazí výsledek a nový řádek.</span><span class="sxs-lookup"><span data-stu-id="193b4-144">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="193b4-145">Spuštěním kódu</span><span class="sxs-lookup"><span data-stu-id="193b4-145">Running your code</span></span>

<span data-ttu-id="193b4-146">Můžete spustit kód a zobrazit výsledky, klikněte na **spustit** z nabídky nejvyšší úrovně a potom **spustit bez ladění**.</span><span class="sxs-lookup"><span data-stu-id="193b4-146">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="193b4-147">Tento program se spustí bez ladění a umožňuje zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="193b4-147">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="193b4-148">Teď byste měli vidět následující vytisknout do okna konzoly, která Visual Studio pro Mac odebrány až:</span><span class="sxs-lookup"><span data-stu-id="193b4-148">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="193b4-149">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="193b4-149">Congratulations!</span></span>  <span data-ttu-id="193b4-150">Jste vytvořili svůj první projekt F # v sadě Visual Studio pro Mac, zapisovat že funkce F # vytisknout výsledky volání této funkce a spusťte projekt zobrazíte některé výsledky.</span><span class="sxs-lookup"><span data-stu-id="193b4-150">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="193b4-151">Pomocí F # interaktivní</span><span class="sxs-lookup"><span data-stu-id="193b4-151">Using F# Interactive</span></span>

<span data-ttu-id="193b4-152">Jedním z nejlepší funkce z Visual F # nástrojů v sadě Visual Studio pro Mac je interaktivních okna F #.</span><span class="sxs-lookup"><span data-stu-id="193b4-152">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="193b4-153">Umožňuje odeslat kód prostřednictvím procesu, kde můžete volat tento kód a zobrazit výsledky interaktivně.</span><span class="sxs-lookup"><span data-stu-id="193b4-153">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="193b4-154">Chcete-li začít používat ji, zvýrazněte `square` funkci definovanou v kódu.</span><span class="sxs-lookup"><span data-stu-id="193b4-154">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="193b4-155">Klikněte na tlačítko na **upravit** z nabídky nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="193b4-155">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="193b4-156">Dále vyberte **poslat výběr F # interaktivní**.</span><span class="sxs-lookup"><span data-stu-id="193b4-156">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="193b4-157">To spustí kód v okně interaktivní F #.</span><span class="sxs-lookup"><span data-stu-id="193b4-157">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="193b4-158">Alternativně můžete klikněte pravým tlačítkem na výběr a zvolte **poslat výběr F # interaktivní**.</span><span class="sxs-lookup"><span data-stu-id="193b4-158">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="193b4-159">Měli byste vidět F # interaktivních okna zobrazují se v něm následující:</span><span class="sxs-lookup"><span data-stu-id="193b4-159">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="193b4-160">Zobrazí se stejným podpisem funkce pro `square` funkce, které jste předtím viděli při při přechodu myší nad funkce.</span><span class="sxs-lookup"><span data-stu-id="193b4-160">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="193b4-161">Protože `square` je nyní definována v F # interaktivní proces, můžete ji volat s různými hodnotami:</span><span class="sxs-lookup"><span data-stu-id="193b4-161">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="193b4-162">Tato funkce spustí, váže výsledek na nový název `it`a zobrazí typu a hodnoty `it`.</span><span class="sxs-lookup"><span data-stu-id="193b4-162">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="193b4-163">Všimněte si, že musí být ukončen každý řádek s `;;`.</span><span class="sxs-lookup"><span data-stu-id="193b4-163">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="193b4-164">Toto je, jak F # interaktivní zná dokončení volání funkce.</span><span class="sxs-lookup"><span data-stu-id="193b4-164">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="193b4-165">Můžete také definovat nové funkce v F # interaktivní:</span><span class="sxs-lookup"><span data-stu-id="193b4-165">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="193b4-166">Výše definuje novou funkci, `isOdd`, které trvá `int` a kontroluje, zda se jedná o liché!</span><span class="sxs-lookup"><span data-stu-id="193b4-166">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="193b4-167">Můžete volat této funkci můžete zjistit, co vrací s různými vstupy.</span><span class="sxs-lookup"><span data-stu-id="193b4-167">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="193b4-168">Můžete volat funkce v rámci volání funkce:</span><span class="sxs-lookup"><span data-stu-id="193b4-168">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="193b4-169">Můžete také [operátor kanálu dopředného](../language-reference/symbol-and-operator-reference/index.md) do kanálu hodnotu do dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="193b4-169">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="193b4-170">Operátor kanálu dopředného a další, jsou popsané v dalších kurzech.</span><span class="sxs-lookup"><span data-stu-id="193b4-170">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="193b4-171">Toto je pouze balíčku glimpse do co můžete dělat s F # interaktivní.</span><span class="sxs-lookup"><span data-stu-id="193b4-171">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="193b4-172">Další informace, podívejte se na [interaktivní programování s F #](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="193b4-172">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="193b4-173">Další kroky</span><span class="sxs-lookup"><span data-stu-id="193b4-173">Next steps</span></span>

<span data-ttu-id="193b4-174">Pokud jste to ještě neudělali, podívejte se [prohlídka z F #](../tour.md), které zahrnuje některé základní funkce jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="193b4-174">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="193b4-175">Bude vám poskytl přehled některých možností F # a zadejte ukázky dostatečným kódu, které můžete zkopírovat do sady Visual Studio pro Mac a spustit.</span><span class="sxs-lookup"><span data-stu-id="193b4-175">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="193b4-176">Existují také některé skvělé externím prostředkům, můžete použít, showcased v [Průvodce F #](../index.md).</span><span class="sxs-lookup"><span data-stu-id="193b4-176">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="193b4-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="193b4-177">See also</span></span>
 [<span data-ttu-id="193b4-178">Visual F#</span><span class="sxs-lookup"><span data-stu-id="193b4-178">Visual F#</span></span>](../index.md)  
 [<span data-ttu-id="193b4-179">Prohlídka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="193b4-179">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="193b4-180">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="193b4-180">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="193b4-181">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="193b4-181">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="193b4-182">Referenční dokumentace symbolů a – operátor</span><span class="sxs-lookup"><span data-stu-id="193b4-182">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  

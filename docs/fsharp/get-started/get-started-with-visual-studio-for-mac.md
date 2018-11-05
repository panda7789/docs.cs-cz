---
title: Začínáme s jazykem F# v sadě Visual Studio pro Mac
description: Další informace o použití F# pomocí sady Visual Studio pro Mac.
ms.date: 07/03/2018
ms.openlocfilehash: 6aceec299c29e04aecd7999cd1dda6a56dd2779a
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44042320"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="2dee7-103">Začínáme s jazykem F# v sadě Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="2dee7-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="2dee7-104">F# a nástrojů Visual F# jsou podporovány v sadě Visual Studio pro Mac integrovaného vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="2dee7-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span> <span data-ttu-id="2dee7-105">Ujistěte se, že máte [Visual Studio for Mac nainstalovat](install-fsharp.md#install-f-with-visual-studio-for-mac).</span><span class="sxs-lookup"><span data-stu-id="2dee7-105">Ensure that you have [Visual Studio for Mac installed](install-fsharp.md#install-f-with-visual-studio-for-mac).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="2dee7-106">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="2dee7-106">Creating a console application</span></span>

<span data-ttu-id="2dee7-107">Jeden z nejzákladnější projektů v sadě Visual Studio for Mac je konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="2dee7-107">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="2dee7-108">Tady je postup.</span><span class="sxs-lookup"><span data-stu-id="2dee7-108">Here's how to do it.</span></span>  <span data-ttu-id="2dee7-109">Jakmile se otevře Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="2dee7-109">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="2dee7-110">Na **souboru** nabídky, přejděte k **nové řešení**.</span><span class="sxs-lookup"><span data-stu-id="2dee7-110">On the **File** menu, point to **New Solution**.</span></span>

2.  <span data-ttu-id="2dee7-111">V dialogovém okně Nový projekt existují 2 různé šablony služby pro konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="2dee7-111">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="2dee7-112">V části Další existuje -> .NET, který cílí na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2dee7-112">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="2dee7-113">Druhá šablona se v .NET Core -> aplikace, které cílí na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2dee7-113">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="2dee7-114">Buď šablona by měla fungovat pro účely tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="2dee7-114">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="2dee7-115">V části konzolovou aplikaci C# do jazyka F# potřeby změňte.</span><span class="sxs-lookup"><span data-stu-id="2dee7-115">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="2dee7-116">Zvolte **Další** tlačítka vpřed!</span><span class="sxs-lookup"><span data-stu-id="2dee7-116">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="2dee7-117">Pojmenujte svůj projekt a zvolte možnosti, které chcete pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2dee7-117">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="2dee7-118">Všimněte si, v podokně náhledu na okraji obrazovky, který se zobrazí adresářovou strukturu, která bude vytvořena podle vybrané možnosti.</span><span class="sxs-lookup"><span data-stu-id="2dee7-118">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="2dee7-119">Klikněte na tlačítko **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="2dee7-119">Click **Create**.</span></span>  <span data-ttu-id="2dee7-120">Teď byste měli vidět projektu F# v Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="2dee7-120">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="2dee7-121">Psaní kódu</span><span class="sxs-lookup"><span data-stu-id="2dee7-121">Writing your code</span></span>

<span data-ttu-id="2dee7-122">Začněme napsáním nějakého kódu.</span><span class="sxs-lookup"><span data-stu-id="2dee7-122">Let's get started by writing some code first.</span></span>  <span data-ttu-id="2dee7-123">Ujistěte se, že `Program.fs` soubor je otevřený a potom nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="2dee7-123">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="2dee7-124">V předchozí ukázce kódu, funkce `square` byla definována desetinný vstup s názvem `x` a vynásobí samostatně.</span><span class="sxs-lookup"><span data-stu-id="2dee7-124">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="2dee7-125">Vzhledem k tomu F# používá [odvození typu](../language-reference/type-inference.md), typ `x` nemusí být zadán.</span><span class="sxs-lookup"><span data-stu-id="2dee7-125">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="2dee7-126">Kompilátor F# rozumí typy, kde je platný násobení a to typu `x` podle toho, jak `square` je volána.</span><span class="sxs-lookup"><span data-stu-id="2dee7-126">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="2dee7-127">Pokud najedete myší `square`, byste měli vidět následující:</span><span class="sxs-lookup"><span data-stu-id="2dee7-127">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="2dee7-128">Je to, co se označuje jako typ signatury funkce.</span><span class="sxs-lookup"><span data-stu-id="2dee7-128">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="2dee7-129">Může být číst takto: "čtverec je funkce, která přebírá celočíselným parametrem s názvem x a vytváří integer".</span><span class="sxs-lookup"><span data-stu-id="2dee7-129">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="2dee7-130">Všimněte si, že kompilátor přiřadil `square` `int` typ prozatím - totiž násobení není obecná napříč *všechny* typy, ale místo toho je obecný zavřené sadě typy.</span><span class="sxs-lookup"><span data-stu-id="2dee7-130">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="2dee7-131">Kompilátor F# vyberou `int` v tomto bodu, ale budou upraveny podpis typu při volání `square` s jiným typ vstupu, například `float`.</span><span class="sxs-lookup"><span data-stu-id="2dee7-131">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="2dee7-132">Další funkci `main`, je definován, která je upravena pomocí `EntryPoint` atribut spuštění tohoto programu předat kompilátor F# by se měl spustit existuje.</span><span class="sxs-lookup"><span data-stu-id="2dee7-132">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="2dee7-133">Řídí stejnou konvencí jako ostatní [programovacích jazyků C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde můžete předávat argumenty příkazového řádku pro tuto funkci a vrátí kód celé číslo (obvykle `0`).</span><span class="sxs-lookup"><span data-stu-id="2dee7-133">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="2dee7-134">Je v této funkce, které označujeme jako `square` funkci s argumentem `12`.</span><span class="sxs-lookup"><span data-stu-id="2dee7-134">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="2dee7-135">Poté přiřadí typ kompilátoru jazyka F# `square` bude `int -> int` (to znamená, funkce, která přebírá `int` a vytváří `int`).</span><span class="sxs-lookup"><span data-stu-id="2dee7-135">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="2dee7-136">Volání `printfn` je formátovaný tisk funkci, která používá řetězec formátu, podobně jako C-style programovacích jazyků, parametry, které odpovídají jsou uvedeny ve formátovacím řetězci a potom zobrazí výsledek a nový řádek.</span><span class="sxs-lookup"><span data-stu-id="2dee7-136">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="2dee7-137">Spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="2dee7-137">Running your code</span></span>

<span data-ttu-id="2dee7-138">Můžete spustit kód a zobrazit výsledky kliknutím na **spustit** z nabídky na nejvyšší úrovni a následně **spustit bez ladění**.</span><span class="sxs-lookup"><span data-stu-id="2dee7-138">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="2dee7-139">Tím se spustí program bez ladění a vám umožní vidět výsledky.</span><span class="sxs-lookup"><span data-stu-id="2dee7-139">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="2dee7-140">Teď byste měli vidět následující zobrazeny v okně konzoly, který Visual Studio for Mac odebrány nahoru:</span><span class="sxs-lookup"><span data-stu-id="2dee7-140">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="2dee7-141">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="2dee7-141">Congratulations!</span></span>  <span data-ttu-id="2dee7-142">Jste vytvořit svůj první projekt F# v sadě Visual Studio pro Mac, zapsat, že funkce jazyka F# Tisk výsledků volání této funkce a spuštění projektu zobrazíte některé výsledky.</span><span class="sxs-lookup"><span data-stu-id="2dee7-142">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="2dee7-143">Používání jazyka F# Interactive</span><span class="sxs-lookup"><span data-stu-id="2dee7-143">Using F# Interactive</span></span>

<span data-ttu-id="2dee7-144">Jedním z nejlepších funkcí nástroje Visual F# nástroje v sadě Visual Studio pro Mac je F# interaktivní okno.</span><span class="sxs-lookup"><span data-stu-id="2dee7-144">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="2dee7-145">Umožňuje poslat kód prostřednictvím procesu, kde můžete tento kód a interaktivně zobrazit výsledek.</span><span class="sxs-lookup"><span data-stu-id="2dee7-145">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="2dee7-146">Chcete-li začít s používáním, zvýrazněte `square` funkci definovanou ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="2dee7-146">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="2dee7-147">Pak klikněte na **upravit** z nabídky nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="2dee7-147">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="2dee7-148">Dále vyberte **odeslat výběr do F# Interactive**.</span><span class="sxs-lookup"><span data-stu-id="2dee7-148">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="2dee7-149">To spustí kód v interaktivním okně F#.</span><span class="sxs-lookup"><span data-stu-id="2dee7-149">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="2dee7-150">Alternativně klikněte pravým tlačítkem na výběr a zvolte **odeslat výběr do F# Interactive**.</span><span class="sxs-lookup"><span data-stu-id="2dee7-150">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="2dee7-151">Měli byste vidět F# interaktivního okna následující v něm se zobrazí:</span><span class="sxs-lookup"><span data-stu-id="2dee7-151">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="2dee7-152">Zobrazí se stejným podpisem funkce pro `square` funkci, kterou jste předtím viděli při přechodu myši nad funkce.</span><span class="sxs-lookup"><span data-stu-id="2dee7-152">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="2dee7-153">Protože `square` je nyní definována v F# interaktivní proces, můžete ji volat s různými hodnotami:</span><span class="sxs-lookup"><span data-stu-id="2dee7-153">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="2dee7-154">To spustí funkci, sváže výsledek s novým názvem `it`a zobrazí se typ a hodnotu `it`.</span><span class="sxs-lookup"><span data-stu-id="2dee7-154">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="2dee7-155">Všimněte si, že každý řádek musí být ukončen `;;`.</span><span class="sxs-lookup"><span data-stu-id="2dee7-155">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="2dee7-156">To je, jak F# Interactive ví dokončení volání funkce.</span><span class="sxs-lookup"><span data-stu-id="2dee7-156">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="2dee7-157">Můžete také definovat nové funkce v jazyce F# Interactive:</span><span class="sxs-lookup"><span data-stu-id="2dee7-157">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="2dee7-158">Výše uvedené definuje novou funkci, `isOdd`, který přebírá `int` a kontroluje, jestli je liché!</span><span class="sxs-lookup"><span data-stu-id="2dee7-158">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="2dee7-159">Můžete volat tuto funkci chcete zobrazit, co vrátí s různými vstupy.</span><span class="sxs-lookup"><span data-stu-id="2dee7-159">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="2dee7-160">Bude možné volat funkce v rámci volání funkce:</span><span class="sxs-lookup"><span data-stu-id="2dee7-160">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="2dee7-161">Můžete také použít [operátor kanálu vpřed](../language-reference/symbol-and-operator-reference/index.md) do kanálu hodnotu do dvou funkcí:</span><span class="sxs-lookup"><span data-stu-id="2dee7-161">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="2dee7-162">Operátor kanálu vpřed a další, jsou popsané v dalších kurzech.</span><span class="sxs-lookup"><span data-stu-id="2dee7-162">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="2dee7-163">Toto je pouze se stručně zmíníme co můžete dělat s F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="2dee7-163">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="2dee7-164">Další informace, podívejte se na [interaktivní programování s F#](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="2dee7-164">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2dee7-165">Další kroky</span><span class="sxs-lookup"><span data-stu-id="2dee7-165">Next steps</span></span>

<span data-ttu-id="2dee7-166">Pokud jste to ještě neudělali, podívejte se [Tour F#](../tour.md), která uvádí i některé základní funkce jazyka F#.</span><span class="sxs-lookup"><span data-stu-id="2dee7-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="2dee7-167">Bude vám poskytnou přehled o některé funkce jazyka F# a poskytovat ukázky ukázku kódu, které můžete zkopírovat do sady Visual Studio pro Mac a spustit.</span><span class="sxs-lookup"><span data-stu-id="2dee7-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="2dee7-168">Existují také některé skvělé externí prostředky můžete použít, zobrazují v [Průvodce jazykem F#](../index.md).</span><span class="sxs-lookup"><span data-stu-id="2dee7-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2dee7-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2dee7-169">See also</span></span>

- [<span data-ttu-id="2dee7-170">Visual F#</span><span class="sxs-lookup"><span data-stu-id="2dee7-170">Visual F#</span></span>](../index.md)  
- [<span data-ttu-id="2dee7-171">Prohlídka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="2dee7-171">Tour of F#</span></span>](../tour.md)  
- [<span data-ttu-id="2dee7-172">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="2dee7-172">F# language reference</span></span>](../language-reference/index.md)  
- [<span data-ttu-id="2dee7-173">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="2dee7-173">Type inference</span></span>](../language-reference/type-inference.md)  
- [<span data-ttu-id="2dee7-174">Referenční dokumentace symbolů a – operátor</span><span class="sxs-lookup"><span data-stu-id="2dee7-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  

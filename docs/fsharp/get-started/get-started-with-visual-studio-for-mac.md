---
title: Začínáme s nástrojem F# v Visual Studio pro Mac
description: Naučte se používat F# s Visual Studio pro Mac.
ms.date: 07/03/2018
ms.openlocfilehash: d3604178f93cf17d21f25b09084be7e7977378b5
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082980"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="8e615-103">Začínáme s nástrojem F# v Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="8e615-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="8e615-104">F#a vizuální F# nástroje jsou podporovány v Visual Studio pro Mac integrovaném vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="8e615-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span> <span data-ttu-id="8e615-105">Ujistěte se, že máte [nainstalovanou Visual Studio pro Mac](install-fsharp.md#install-f-with-visual-studio-for-mac).</span><span class="sxs-lookup"><span data-stu-id="8e615-105">Ensure that you have [Visual Studio for Mac installed](install-fsharp.md#install-f-with-visual-studio-for-mac).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="8e615-106">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="8e615-106">Creating a console application</span></span>

<span data-ttu-id="8e615-107">Jedním z nejvíce základních projektů v Visual Studio pro Mac je Konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="8e615-107">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="8e615-108">Tady je postup, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="8e615-108">Here's how to do it.</span></span>  <span data-ttu-id="8e615-109">Jakmile Visual Studio pro Mac otevřete:</span><span class="sxs-lookup"><span data-stu-id="8e615-109">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="8e615-110">V nabídce **soubor** přejděte na příkaz **nové řešení**.</span><span class="sxs-lookup"><span data-stu-id="8e615-110">On the **File** menu, point to **New Solution**.</span></span>

2. <span data-ttu-id="8e615-111">V dialogovém okně Nový projekt existují 2 různé šablony pro konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8e615-111">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="8e615-112">Existuje jeden pod > .NET, který cílí na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e615-112">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="8e615-113">Druhá šablona je v rámci aplikace .NET Core->, která cílí na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e615-113">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="8e615-114">Každá šablona by měla fungovat pro účely tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="8e615-114">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="8e615-115">V části Konzolová aplikace C# v F# případě potřeby změňte na.</span><span class="sxs-lookup"><span data-stu-id="8e615-115">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="8e615-116">Kliknutím na tlačítko **Další** přesunete vpřed.</span><span class="sxs-lookup"><span data-stu-id="8e615-116">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="8e615-117">Zadejte název vašeho projektu a vyberte požadované možnosti pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8e615-117">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="8e615-118">Všimněte si, že podokno náhledu na stranu obrazovky, ve kterém se zobrazí struktura adresáře, která bude vytvořena na základě vybraných možností.</span><span class="sxs-lookup"><span data-stu-id="8e615-118">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="8e615-119">Klikněte na možnost **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="8e615-119">Click **Create**.</span></span>  <span data-ttu-id="8e615-120">V Průzkumník řešení by se teď F# měl zobrazit projekt.</span><span class="sxs-lookup"><span data-stu-id="8e615-120">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="8e615-121">Psaní kódu</span><span class="sxs-lookup"><span data-stu-id="8e615-121">Writing your code</span></span>

<span data-ttu-id="8e615-122">Pojďme začít vytvořením kódu jako prvního.</span><span class="sxs-lookup"><span data-stu-id="8e615-122">Let's get started by writing some code first.</span></span>  <span data-ttu-id="8e615-123">Ujistěte se, že `Program.fs` je soubor otevřený, a pak jeho obsah nahraďte následujícím:</span><span class="sxs-lookup"><span data-stu-id="8e615-123">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="8e615-124">V předchozím příkladu kódu byla definována funkce `square` , která přebírá vstup s názvem `x` a násobí ho sám sebou.</span><span class="sxs-lookup"><span data-stu-id="8e615-124">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="8e615-125">F# Vzhledem`x` k tomu, že používá [odvození typu](../language-reference/type-inference.md), není třeba zadávat typ.</span><span class="sxs-lookup"><span data-stu-id="8e615-125">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="8e615-126">F# Kompilátor rozumí typům, kde je násobení platné, a přiřadí typ `x` podle toho, jak `square` je volána.</span><span class="sxs-lookup"><span data-stu-id="8e615-126">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="8e615-127">Pokud najedete `square`myší na, měli byste vidět následující:</span><span class="sxs-lookup"><span data-stu-id="8e615-127">If you hover over `square`, you should see the following:</span></span>

```console
val square: x:int -> int
```

<span data-ttu-id="8e615-128">Jedná se o to, co se říká signatura typu funkce.</span><span class="sxs-lookup"><span data-stu-id="8e615-128">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="8e615-129">Dá se číst takto: "Square je funkce, která přebírá celé číslo s názvem x a vytvoří celé číslo".</span><span class="sxs-lookup"><span data-stu-id="8e615-129">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="8e615-130">Všimněte si, že kompilátor `square` tento `int` typ nyní přiřadil – je to proto, že násobení není obecné napříč *všemi* typy, ale spíše je obecné napříč uzavřenou sadou typů.</span><span class="sxs-lookup"><span data-stu-id="8e615-130">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="8e615-131">F# Kompilátor vybral `int` v tomto okamžiku, ale upraví signaturu typu, pokud voláte `square` s jiným typem vstupu, jako je `float`například.</span><span class="sxs-lookup"><span data-stu-id="8e615-131">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="8e615-132">Je definována jiná `main`funkce,,, která je upravena `EntryPoint` s atributem, aby F# informovala kompilátor, že by měl spustit program, který by měl spustit.</span><span class="sxs-lookup"><span data-stu-id="8e615-132">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="8e615-133">Odpovídá stejné konvenci jako jiné [programovací jazyky ve stylu jazyka C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde argumenty příkazového řádku lze předat této funkci a je vrácen celočíselný kód (obvykle `0`).</span><span class="sxs-lookup"><span data-stu-id="8e615-133">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="8e615-134">Je touto funkcí, která volá `square` funkci s `12`argumentem.</span><span class="sxs-lookup"><span data-stu-id="8e615-134">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="8e615-135">F# Kompilátor potom `square` přiřadí typ `int -> int` , který `int` je (to znamená `int`funkce, která přijímá a vytvoří).</span><span class="sxs-lookup"><span data-stu-id="8e615-135">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="8e615-136">Volání je naformátovaná funkce pro `printfn` tisk, která používá formátovací řetězec, podobně jako programovací jazyky ve stylu jazyka C, parametry, které odpovídají těm, které jsou zadány ve formátu řetězce, a pak vytiskne výsledek a nový řádek.</span><span class="sxs-lookup"><span data-stu-id="8e615-136">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="8e615-137">Spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="8e615-137">Running your code</span></span>

<span data-ttu-id="8e615-138">Můžete spustit kód a zobrazit výsledky kliknutím na **Spustit** v nabídce nejvyšší úrovně a pak **Spustit bez ladění**.</span><span class="sxs-lookup"><span data-stu-id="8e615-138">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="8e615-139">Tím se spustí program bez ladění a umožní vám zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="8e615-139">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="8e615-140">Nyní byste měli vidět následující vytištěné okno konzoly, které Visual Studio pro Mac odebráno:</span><span class="sxs-lookup"><span data-stu-id="8e615-140">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```console
12 squared is 144!
```

<span data-ttu-id="8e615-141">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="8e615-141">Congratulations!</span></span>  <span data-ttu-id="8e615-142">Vytvořili jste svůj první F# projekt v Visual Studio pro Mac, napsali jste F# funkci, která vytiskla výsledky volání funkce a spustí projekt, aby se zobrazily nějaké výsledky.</span><span class="sxs-lookup"><span data-stu-id="8e615-142">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="8e615-143">Pomocí F# Interactive</span><span class="sxs-lookup"><span data-stu-id="8e615-143">Using F# Interactive</span></span>

<span data-ttu-id="8e615-144">Jednou z nejlepších funkcí vizuálních F# nástrojů v Visual Studio pro Mac je F# interaktivní okno.</span><span class="sxs-lookup"><span data-stu-id="8e615-144">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="8e615-145">Umožňuje odeslat kód do procesu, kde můžete zavolat tento kód a interaktivně zobrazit výsledek.</span><span class="sxs-lookup"><span data-stu-id="8e615-145">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="8e615-146">Pokud ho chcete začít používat, zvýrazněte `square` funkci definovanou ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="8e615-146">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="8e615-147">Potom v nabídce nejvyšší úrovně klikněte na **Upravit** .</span><span class="sxs-lookup"><span data-stu-id="8e615-147">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="8e615-148">V dalším kroku vyberte **Odeslat F# výběr do interaktivního**.</span><span class="sxs-lookup"><span data-stu-id="8e615-148">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="8e615-149">Tím se spustí kód v F# interaktivním okně.</span><span class="sxs-lookup"><span data-stu-id="8e615-149">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="8e615-150">Případně můžete kliknout pravým tlačítkem na výběr a vybrat **Odeslat výběr do F# interaktivní**.</span><span class="sxs-lookup"><span data-stu-id="8e615-150">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="8e615-151">Mělo by se zobrazit F# interaktivní okno s následujícím:</span><span class="sxs-lookup"><span data-stu-id="8e615-151">You should see the F# Interactive Window appear with the following in it:</span></span>

```console
>

val square : x:int -> int

>
```

<span data-ttu-id="8e615-152">To ukazuje stejnou signaturu funkce pro `square` funkci, kterou jste viděli dříve při přechodu na funkci.</span><span class="sxs-lookup"><span data-stu-id="8e615-152">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="8e615-153">Vzhledem `square` k tomu, že je F# nyní definováno v interaktivním procesu, můžete ho zavolat s různými hodnotami:</span><span class="sxs-lookup"><span data-stu-id="8e615-153">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="8e615-154">Tím se spustí funkce, vytvoří se výsledek k novému názvu `it`a zobrazí typ a `it`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8e615-154">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="8e615-155">Všimněte si, že je nutné ukončit každý `;;`řádek pomocí.</span><span class="sxs-lookup"><span data-stu-id="8e615-155">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="8e615-156">To je způsob F# , jak interaktivní ví, kdy bylo volání funkce dokončeno.</span><span class="sxs-lookup"><span data-stu-id="8e615-156">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="8e615-157">Můžete také definovat nové funkce v F# Interactive:</span><span class="sxs-lookup"><span data-stu-id="8e615-157">You can also define new functions in F# Interactive:</span></span>

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="8e615-158">Výše uvedený postup definuje novou funkci, `isOdd`která `int` přijímá a kontroluje, jestli je lichá.</span><span class="sxs-lookup"><span data-stu-id="8e615-158">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="8e615-159">Voláním této funkce můžete zjistit, co se vrátí s různými vstupy.</span><span class="sxs-lookup"><span data-stu-id="8e615-159">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="8e615-160">Můžete volat funkce v volání funkce:</span><span class="sxs-lookup"><span data-stu-id="8e615-160">You can call functions within function calls:</span></span>

```console
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="8e615-161">K zřetězení hodnoty do dvou funkcí můžete použít také [operátor předávání kanálu](../language-reference/symbol-and-operator-reference/index.md) :</span><span class="sxs-lookup"><span data-stu-id="8e615-161">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="8e615-162">Operátor s přesměrováním na kanál a další jsou uvedené v dalších kurzech.</span><span class="sxs-lookup"><span data-stu-id="8e615-162">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="8e615-163">To je jenom nakoukněte, co můžete dělat s F# interaktivními.</span><span class="sxs-lookup"><span data-stu-id="8e615-163">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="8e615-164">Pokud se chcete dozvědět víc, podívejte [se na F#interaktivní programování pomocí ](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e615-164">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8e615-165">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8e615-165">Next steps</span></span>

<span data-ttu-id="8e615-166">Pokud jste to ještě neudělali, podívejte se na [prohlídku F# ](../tour.md), která se zabývá některými základními F# funkcemi daného jazyka.</span><span class="sxs-lookup"><span data-stu-id="8e615-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="8e615-167">Poskytne vám přehled některých možností F#nástroje a poskytne vám podrobné ukázky kódu, které můžete zkopírovat do Visual Studio pro Mac a spustit.</span><span class="sxs-lookup"><span data-stu-id="8e615-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="8e615-168">K dispozici jsou také některé skvělé externí prostředky, které můžete použít v [ F# průvodci](../index.md).</span><span class="sxs-lookup"><span data-stu-id="8e615-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8e615-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e615-169">See also</span></span>

- [<span data-ttu-id="8e615-170">Visual F#</span><span class="sxs-lookup"><span data-stu-id="8e615-170">Visual F#</span></span>](../index.md)
- [<span data-ttu-id="8e615-171">Prohlídka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="8e615-171">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="8e615-172">F#Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="8e615-172">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="8e615-173">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="8e615-173">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="8e615-174">Reference k symbolům a operátorovi</span><span class="sxs-lookup"><span data-stu-id="8e615-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)

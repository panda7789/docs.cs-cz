---
title: Začínáme s nástrojem F# v aplikaci Visual Studio
description: Naučte se používat F# se sadou Visual Studio.
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337346"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="eca02-103">Začínáme s nástrojem F# v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eca02-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="eca02-104">F#a vizuální F# nástroje jsou podporovány v integrovaném vývojovém prostředí (IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eca02-104">F# and the Visual F# tooling are supported in the Visual Studio integrated development environment (IDE).</span></span>

<span data-ttu-id="eca02-105">Pokud chcete začít, ujistěte se, že máte [nainstalovanou F# aplikaci Visual Studio s podporou](install-fsharp.md#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="eca02-105">To begin, ensure that you have [Visual Studio installed with F# support](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="eca02-106">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="eca02-106">Create a console application</span></span>

<span data-ttu-id="eca02-107">Jedním z nejvíc základních projektů v aplikaci Visual Studio je aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="eca02-107">One of the most basic projects in Visual Studio is the console app.</span></span> <span data-ttu-id="eca02-108">Tady je postup, jak ho vytvořit:</span><span class="sxs-lookup"><span data-stu-id="eca02-108">Here's how to create one:</span></span>

1. <span data-ttu-id="eca02-109">Otevřete Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="eca02-109">Open Visual Studio 2019.</span></span>

2. <span data-ttu-id="eca02-110">V okně Start vyberte možnost **vytvořit nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="eca02-110">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="eca02-111">Na stránce **vytvořit nový projekt** vyberte **F#** ze seznamu jazyk.</span><span class="sxs-lookup"><span data-stu-id="eca02-111">On the **Create a new project** page, choose **F#** from the Language list.</span></span>

4. <span data-ttu-id="eca02-112">Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="eca02-112">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

5. <span data-ttu-id="eca02-113">Na stránce **Konfigurovat nový projekt** zadejte název do pole **název projektu** .</span><span class="sxs-lookup"><span data-stu-id="eca02-113">On the **Configure your new project** page, enter a name in the **Project name** box.</span></span> <span data-ttu-id="eca02-114">Pak zvolte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="eca02-114">Then, choose **Create**.</span></span>

   <span data-ttu-id="eca02-115">Visual Studio vytvoří nový F# projekt.</span><span class="sxs-lookup"><span data-stu-id="eca02-115">Visual Studio creates the new F# project.</span></span> <span data-ttu-id="eca02-116">Můžete ji zobrazit v okně Průzkumník řešení.</span><span class="sxs-lookup"><span data-stu-id="eca02-116">You can see it in the Solution Explorer window.</span></span>

## <a name="write-the-code"></a><span data-ttu-id="eca02-117">Zadejte kód</span><span class="sxs-lookup"><span data-stu-id="eca02-117">Write the code</span></span>

<span data-ttu-id="eca02-118">Pojďme začít psaním kódu.</span><span class="sxs-lookup"><span data-stu-id="eca02-118">Let's get started by writing some code.</span></span> <span data-ttu-id="eca02-119">Ujistěte se, že je soubor `Program.fs` otevřený, a pak jeho obsah nahraďte následujícím:</span><span class="sxs-lookup"><span data-stu-id="eca02-119">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="eca02-120">Předchozí ukázka kódu definuje funkci s názvem `square`, která přebírá vstup s názvem `x` a vynásobí ho samotným.</span><span class="sxs-lookup"><span data-stu-id="eca02-120">The previous code sample defines a function called `square` that takes an input named `x` and multiplies it by itself.</span></span> <span data-ttu-id="eca02-121">Vzhledem F# k tomu, že používá [odvození typu](../language-reference/type-inference.md), není nutné zadat typ `x`.</span><span class="sxs-lookup"><span data-stu-id="eca02-121">Because F# uses [Type inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span> <span data-ttu-id="eca02-122">F# Kompilátor rozumí typům, kde je násobení platné, a přiřadí typ, který `x` na základě toho, jak je `square` volána.</span><span class="sxs-lookup"><span data-stu-id="eca02-122">The F# compiler understands the types where multiplication is valid and assigns a type to `x` based on how `square` is called.</span></span> <span data-ttu-id="eca02-123">Pokud najedete myší na `square`, měli byste vidět následující:</span><span class="sxs-lookup"><span data-stu-id="eca02-123">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="eca02-124">Jedná se o to, co se říká signatura typu funkce.</span><span class="sxs-lookup"><span data-stu-id="eca02-124">This is what is known as the function's type signature.</span></span> <span data-ttu-id="eca02-125">Dá se číst takto: "čtvercem je funkce, která přebírá celé číslo s názvem x a vytváří celé číslo".</span><span class="sxs-lookup"><span data-stu-id="eca02-125">It can be read like this: "Square is a function that takes an integer named x and produces an integer".</span></span> <span data-ttu-id="eca02-126">Kompilátor poskytl `square` `int` typ pro teď; Důvodem je, že násobení není obecné napříč *všemi* typy, ale spíše uzavřenou sadou typů.</span><span class="sxs-lookup"><span data-stu-id="eca02-126">The compiler gave `square` the `int` type for now; this is because multiplication is not generic across *all* types but rather a closed set of types.</span></span> <span data-ttu-id="eca02-127">F# Kompilátor upraví signaturu typu při volání `square` s jiným typem vstupu, jako je například `float`.</span><span class="sxs-lookup"><span data-stu-id="eca02-127">The F# compiler will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="eca02-128">Je definována jiná funkce, `main`, která je upravena atributem `EntryPoint`.</span><span class="sxs-lookup"><span data-stu-id="eca02-128">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute.</span></span> <span data-ttu-id="eca02-129">Tento atribut oznamuje F# kompilátoru, že by měl spustit program pro spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="eca02-129">This attribute tells the F# compiler that program execution should start there.</span></span> <span data-ttu-id="eca02-130">Řídí se stejnou konvencí jako jiné [programovací jazyky ve stylu jazyka C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde argumenty příkazového řádku lze předat této funkci a je vrácen celočíselný kód (obvykle `0`).</span><span class="sxs-lookup"><span data-stu-id="eca02-130">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="eca02-131">Je ve funkci vstupního bodu, `main`, která volá funkci `square` s argumentem `12`.</span><span class="sxs-lookup"><span data-stu-id="eca02-131">It is in the entry point function, `main`, that you call the `square` function with an argument of `12`.</span></span> <span data-ttu-id="eca02-132">F# Kompilátor potom přiřadí typ `square`, který se má `int -> int` (to znamená funkce, která přebírá `int` a vytvoří `int`).</span><span class="sxs-lookup"><span data-stu-id="eca02-132">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function that takes an `int` and produces an `int`).</span></span> <span data-ttu-id="eca02-133">Volání `printfn` je naformátovaná funkce pro tisk, která používá formátovací řetězec a tiskne výsledek (a nový řádek).</span><span class="sxs-lookup"><span data-stu-id="eca02-133">The call to `printfn` is a formatted printing function that uses a format string and prints the result (and a new line).</span></span> <span data-ttu-id="eca02-134">Řetězec formátu, podobně jako programovací jazyky ve stylu jazyka C, má parametry (`%d`), které odpovídají argumentům, které jsou předány, v tomto případě `12` a `(square 12)`.</span><span class="sxs-lookup"><span data-stu-id="eca02-134">The format string, similar to C-style programming languages, has parameters (`%d`) that correspond to the arguments that are passed to it, in this case, `12` and `(square 12)`.</span></span>

## <a name="run-the-code"></a><span data-ttu-id="eca02-135">Spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="eca02-135">Run the code</span></span>

<span data-ttu-id="eca02-136">Můžete spustit kód a zobrazit výsledky stisknutím **kombinace kláves Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="eca02-136">You can run the code and see the results by pressing **Ctrl**+**F5**.</span></span> <span data-ttu-id="eca02-137">Alternativně můžete zvolit > **ladění** **Spustit bez ladění** z panelu nabídek nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="eca02-137">Alternatively, you can choose the **Debug** > **Start Without Debugging** from the top-level menu bar.</span></span> <span data-ttu-id="eca02-138">Tím se spustí program bez ladění.</span><span class="sxs-lookup"><span data-stu-id="eca02-138">This runs the program without debugging.</span></span>

<span data-ttu-id="eca02-139">Následující výstup vytiskne okno konzoly, které se otevřelo v aplikaci Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="eca02-139">The following output prints to the console window that Visual Studio opened:</span></span>

```console
12 squared is: 144!
```

<span data-ttu-id="eca02-140">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="eca02-140">Congratulations!</span></span> <span data-ttu-id="eca02-141">Vytvořili jste svůj první F# projekt v aplikaci Visual Studio, napsali jste F# funkci, která vypočítá a vytiskne hodnotu a spustí projekt, aby se zobrazily výsledky.</span><span class="sxs-lookup"><span data-stu-id="eca02-141">You've created your first F# project in Visual Studio, written an F# function that calculates and prints a value, and run the project to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="eca02-142">Další kroky</span><span class="sxs-lookup"><span data-stu-id="eca02-142">Next steps</span></span>

<span data-ttu-id="eca02-143">Pokud jste to ještě neudělali, podívejte se na [prohlídku F# ](../tour.md), která se zabývá některými základními F# funkcemi daného jazyka.</span><span class="sxs-lookup"><span data-stu-id="eca02-143">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span> <span data-ttu-id="eca02-144">Poskytuje přehled některých funkcí a všech F# ukázek kódu, které můžete zkopírovat do sady Visual Studio a spustit.</span><span class="sxs-lookup"><span data-stu-id="eca02-144">It provides an overview of some of the capabilities of F# and ample code samples that you can copy into Visual Studio and run.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eca02-145">Prohlídka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="eca02-145">Tour of F#</span></span>](../tour.md)

## <a name="see-also"></a><span data-ttu-id="eca02-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eca02-146">See also</span></span>

- [<span data-ttu-id="eca02-147">F#Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="eca02-147">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="eca02-148">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="eca02-148">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="eca02-149">Reference k symbolům a operátorovi</span><span class="sxs-lookup"><span data-stu-id="eca02-149">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)

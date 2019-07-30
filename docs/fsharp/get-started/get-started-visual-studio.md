---
title: Začínáme s nástrojem F# v aplikaci Visual Studio
description: Naučte se používat F# se sadou Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 24c9a81cfa61dc904db9b2213224677696d7eb9b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629765"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="fc519-103">Začínáme s nástrojem F# v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fc519-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="fc519-104">F#a vizuální F# nástroje jsou podporovány v integrovaném vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fc519-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="fc519-105">Chcete-li začít, ujistěte se, že je [nainstalována F#aplikace Visual Studio s nástrojem ](install-fsharp.md#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="fc519-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="fc519-106">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="fc519-106">Creating a console application</span></span>

<span data-ttu-id="fc519-107">Jedním z nejběžnějších projektů v aplikaci Visual Studio je Konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc519-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="fc519-108">Tady je postup, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="fc519-108">Here's how to do it.</span></span>  <span data-ttu-id="fc519-109">Po otevření sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="fc519-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="fc519-110">V nabídce **soubor** přejděte na příkaz **Nový**a zvolte možnost **projekt**.</span><span class="sxs-lookup"><span data-stu-id="fc519-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2. <span data-ttu-id="fc519-111">V dialogovém okně Nový projekt, v části **šablony**byste měli vidět **vizuál F#** .</span><span class="sxs-lookup"><span data-stu-id="fc519-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="fc519-112">Tuto možnost vyberte, pokud F# chcete zobrazit šablony.</span><span class="sxs-lookup"><span data-stu-id="fc519-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="fc519-113">Vyberte buď **konzolovou aplikaci .NET Core** , nebo **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="fc519-113">Select either **.NET Core Console app** or **Console app**.</span></span>

4. <span data-ttu-id="fc519-114">Kliknutím na tlačítko **OK** vytvořte F# projekt.</span><span class="sxs-lookup"><span data-stu-id="fc519-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="fc519-115">V Průzkumník řešení by se teď F# měl zobrazit projekt.</span><span class="sxs-lookup"><span data-stu-id="fc519-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="fc519-116">Psaní kódu</span><span class="sxs-lookup"><span data-stu-id="fc519-116">Writing your code</span></span>

<span data-ttu-id="fc519-117">Pojďme začít vytvořením kódu jako prvního.</span><span class="sxs-lookup"><span data-stu-id="fc519-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="fc519-118">Ujistěte se, že `Program.fs` je soubor otevřený, a pak jeho obsah nahraďte následujícím:</span><span class="sxs-lookup"><span data-stu-id="fc519-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="fc519-119">V předchozím příkladu kódu byla definována funkce `square` , která přebírá vstup s názvem `x` a násobí ho sám sebou.</span><span class="sxs-lookup"><span data-stu-id="fc519-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="fc519-120">Vzhledem F# [k tomu](../language-reference/type-inference.md), že používá odvození typu, nenítřebazadávattyp.`x`</span><span class="sxs-lookup"><span data-stu-id="fc519-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="fc519-121">F# Kompilátor rozumí typům, kde je násobení platné, a přiřadí typ `x` podle toho, jak `square` je volána.</span><span class="sxs-lookup"><span data-stu-id="fc519-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="fc519-122">Pokud najedete `square`myší na, měli byste vidět následující:</span><span class="sxs-lookup"><span data-stu-id="fc519-122">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="fc519-123">Jedná se o to, co se říká signatura typu funkce.</span><span class="sxs-lookup"><span data-stu-id="fc519-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="fc519-124">Dá se číst takto: "Square je funkce, která přebírá celé číslo s názvem x a vytvoří celé číslo".</span><span class="sxs-lookup"><span data-stu-id="fc519-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="fc519-125">Všimněte si, že kompilátor `square` tento `int` typ nyní přiřadil – je to proto, že násobení není obecné napříč *všemi* typy, ale spíše je obecné napříč uzavřenou sadou typů.</span><span class="sxs-lookup"><span data-stu-id="fc519-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="fc519-126">F# Kompilátor vybral `int` v tomto okamžiku, ale upraví signaturu typu, pokud voláte `square` s jiným typem vstupu, jako je `float`například.</span><span class="sxs-lookup"><span data-stu-id="fc519-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="fc519-127">Je definována jiná `main`funkce,,, která je upravena `EntryPoint` s atributem, aby F# informovala kompilátor, že by měl spustit program, který by měl spustit.</span><span class="sxs-lookup"><span data-stu-id="fc519-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="fc519-128">Odpovídá stejné konvenci jako jiné [programovací jazyky ve stylu jazyka C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde argumenty příkazového řádku lze předat této funkci a je vrácen celočíselný kód (obvykle `0`).</span><span class="sxs-lookup"><span data-stu-id="fc519-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="fc519-129">Je touto funkcí, která volá `square` funkci s `12`argumentem.</span><span class="sxs-lookup"><span data-stu-id="fc519-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="fc519-130">F# Kompilátor potom `square` přiřadí typ `int -> int` , který `int` je (to znamená `int`funkce, která přijímá a vytvoří).</span><span class="sxs-lookup"><span data-stu-id="fc519-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="fc519-131">Volání je naformátovaná funkce pro `printfn` tisk, která používá formátovací řetězec, podobně jako programovací jazyky ve stylu jazyka C, parametry, které odpovídají těm, které jsou zadány ve formátu řetězce, a pak vytiskne výsledek a nový řádek.</span><span class="sxs-lookup"><span data-stu-id="fc519-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="fc519-132">Spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="fc519-132">Running your code</span></span>

<span data-ttu-id="fc519-133">Můžete spustit kód a zobrazit výsledky stisknutím klávesy **CTRL**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="fc519-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="fc519-134">Tím se spustí program bez ladění a umožní vám zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="fc519-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="fc519-135">Alternativně můžete zvolit položku nabídky nejvyšší úrovně **ladění** v aplikaci Visual Studio a zvolit možnost **Spustit bez ladění**.</span><span class="sxs-lookup"><span data-stu-id="fc519-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="fc519-136">Nyní byste měli vidět následující vytištěné okno konzoly, ve kterém se zobrazila aplikace Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="fc519-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="fc519-137">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="fc519-137">Congratulations!</span></span>  <span data-ttu-id="fc519-138">Vytvořili jste svůj první F# projekt v aplikaci Visual Studio, napsali F# jste funkci, která vytiskla výsledky volání této funkce, a spustí projekt, aby se zobrazily nějaké výsledky.</span><span class="sxs-lookup"><span data-stu-id="fc519-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fc519-139">Další postup</span><span class="sxs-lookup"><span data-stu-id="fc519-139">Next steps</span></span>

<span data-ttu-id="fc519-140">Pokud jste to ještě neudělali, podívejte se na prohlídku [ F# ](../tour.md), která se zabývá některými základními F# funkcemi daného jazyka.</span><span class="sxs-lookup"><span data-stu-id="fc519-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="fc519-141">Poskytne vám přehled o některých možnostech aplikace F#a poskytuje podrobné ukázky kódu, které můžete zkopírovat do sady Visual Studio a spustit.</span><span class="sxs-lookup"><span data-stu-id="fc519-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="fc519-142">K dispozici jsou také některé skvělé externí prostředky, které můžete použít v [ F# průvodci](../index.md).</span><span class="sxs-lookup"><span data-stu-id="fc519-142">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fc519-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc519-143">See also</span></span>

- [<span data-ttu-id="fc519-144">Prohlídka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="fc519-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="fc519-145">F#Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="fc519-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="fc519-146">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="fc519-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="fc519-147">Reference k symbolům a operátorovi</span><span class="sxs-lookup"><span data-stu-id="fc519-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)

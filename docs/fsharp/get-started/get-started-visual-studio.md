---
title: Začínáme s F# v sadě Visual Studio
description: Další informace o použití F# pomocí sady Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 9b02a5d295f982b1911dab567213fa9a2b6c4304
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "63808021"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="85eaf-103">Začínáme s F# v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="85eaf-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="85eaf-104">F#a vizuál F# nástroje jsou podporovány v integrovaném vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85eaf-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="85eaf-105">Pokud chcete začít, ujistěte se, že máte [nainstalované sady Visual Studio s F# ](install-fsharp.md#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="85eaf-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="85eaf-106">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="85eaf-106">Creating a console application</span></span>

<span data-ttu-id="85eaf-107">Jeden z nejzákladnější projektů v sadě Visual Studio je konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="85eaf-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="85eaf-108">Tady je postup.</span><span class="sxs-lookup"><span data-stu-id="85eaf-108">Here's how to do it.</span></span>  <span data-ttu-id="85eaf-109">Jakmile se Visual Studio otevře:</span><span class="sxs-lookup"><span data-stu-id="85eaf-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="85eaf-110">Na **souboru** nabídky, přejděte k **nový**a klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="85eaf-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2. <span data-ttu-id="85eaf-111">V nový projekt dialogového okna, v části **šablony**, měli byste vidět **Visual F#** .</span><span class="sxs-lookup"><span data-stu-id="85eaf-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="85eaf-112">Chcete-li zobrazit tuto možnost zvolte, F# šablony.</span><span class="sxs-lookup"><span data-stu-id="85eaf-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="85eaf-113">Vyberte buď **.NET Core konzolovou aplikaci** nebo **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="85eaf-113">Select either **.NET Core Console app** or **Console app**.</span></span>

4. <span data-ttu-id="85eaf-114">Zvolte **dobře** tlačítko vytvoříte F# projekt!</span><span class="sxs-lookup"><span data-stu-id="85eaf-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="85eaf-115">Teď byste měli vidět F# projekt v Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="85eaf-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="85eaf-116">Psaní kódu</span><span class="sxs-lookup"><span data-stu-id="85eaf-116">Writing your code</span></span>

<span data-ttu-id="85eaf-117">Začněme napsáním nějakého kódu.</span><span class="sxs-lookup"><span data-stu-id="85eaf-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="85eaf-118">Ujistěte se, že `Program.fs` soubor je otevřený a potom nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="85eaf-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="85eaf-119">V předchozí ukázce kódu, funkce `square` byla definována desetinný vstup s názvem `x` a vynásobí samostatně.</span><span class="sxs-lookup"><span data-stu-id="85eaf-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="85eaf-120">Protože F# používá [odvození typu](../language-reference/type-inference.md), typ `x` nemusí být zadán.</span><span class="sxs-lookup"><span data-stu-id="85eaf-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="85eaf-121">F# Kompilátoru rozumí typy, kde je platný násobení a to typu `x` podle toho, jak `square` je volána.</span><span class="sxs-lookup"><span data-stu-id="85eaf-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="85eaf-122">Pokud najedete myší `square`, byste měli vidět následující:</span><span class="sxs-lookup"><span data-stu-id="85eaf-122">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="85eaf-123">Je to, co se označuje jako typ signatury funkce.</span><span class="sxs-lookup"><span data-stu-id="85eaf-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="85eaf-124">Najdete takto: "Čtverec je funkce, která přebírá celočíselným parametrem s názvem x a vytváří integer".</span><span class="sxs-lookup"><span data-stu-id="85eaf-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="85eaf-125">Všimněte si, že kompilátor přiřadil `square` `int` typ prozatím - totiž násobení není obecná napříč *všechny* typy, ale místo toho je obecný zavřené sadě typy.</span><span class="sxs-lookup"><span data-stu-id="85eaf-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="85eaf-126">F# Kompilátoru vyberou `int` v tomto bodu, ale budou upraveny podpis typu při volání `square` s jiným typ vstupu, například `float`.</span><span class="sxs-lookup"><span data-stu-id="85eaf-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="85eaf-127">Další funkci `main`, je definován, která je upravena pomocí `EntryPoint` atribut říct F# kompilátor, který provádění programu by se měl spustit existuje.</span><span class="sxs-lookup"><span data-stu-id="85eaf-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="85eaf-128">Řídí stejnou konvencí jako ostatní [programovacích jazyků C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde můžete předávat argumenty příkazového řádku pro tuto funkci a vrátí kód celé číslo (obvykle `0`).</span><span class="sxs-lookup"><span data-stu-id="85eaf-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="85eaf-129">Je v této funkce, které označujeme jako `square` funkci s argumentem `12`.</span><span class="sxs-lookup"><span data-stu-id="85eaf-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="85eaf-130">F# Kompilátor poté přiřadí typu `square` bude `int -> int` (to znamená, funkce, která přebírá `int` a vytváří `int`).</span><span class="sxs-lookup"><span data-stu-id="85eaf-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="85eaf-131">Volání `printfn` je formátovaný tisk funkci, která používá řetězec formátu, podobně jako C-style programovacích jazyků, parametry, které odpovídají jsou uvedeny ve formátovacím řetězci a potom zobrazí výsledek a nový řádek.</span><span class="sxs-lookup"><span data-stu-id="85eaf-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="85eaf-132">Spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="85eaf-132">Running your code</span></span>

<span data-ttu-id="85eaf-133">Můžete spustit kód a zobrazit výsledky stisknutím kombinace kláves **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="85eaf-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="85eaf-134">To spustí program bez ladění a vám umožní vidět výsledky.</span><span class="sxs-lookup"><span data-stu-id="85eaf-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="85eaf-135">Alternativně můžete použít **ladění** nabídek nejvyšší úrovně položku v sadě Visual Studio a zvolte **spustit bez ladění**.</span><span class="sxs-lookup"><span data-stu-id="85eaf-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="85eaf-136">Teď byste měli vidět následující zobrazeny v okně konzoly, který Visual Studio odebrány nahoru:</span><span class="sxs-lookup"><span data-stu-id="85eaf-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="85eaf-137">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="85eaf-137">Congratulations!</span></span>  <span data-ttu-id="85eaf-138">Vytvoření vaší první F# projektu v sadě Visual Studio, zapisovat F# funkce vytisknout výsledky volání funkce, které funkce a spuštění projektu zobrazíte některé výsledky.</span><span class="sxs-lookup"><span data-stu-id="85eaf-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="85eaf-139">Další kroky</span><span class="sxs-lookup"><span data-stu-id="85eaf-139">Next steps</span></span>

<span data-ttu-id="85eaf-140">Pokud jste to ještě neudělali, podívejte se [prohlídka F# ](../tour.md), která uvádí i některé základní funkce F# jazyka.</span><span class="sxs-lookup"><span data-stu-id="85eaf-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="85eaf-141">Poskytne vám přehled některých možností F#a poskytnout ukázky ukázku kódu, které můžete zkopírovat do sady Visual Studio a spustit.</span><span class="sxs-lookup"><span data-stu-id="85eaf-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="85eaf-142">Existují také některé skvělé externí prostředky můžete použít, zobrazují v [ F# průvodce](../index.md).</span><span class="sxs-lookup"><span data-stu-id="85eaf-142">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85eaf-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85eaf-143">See also</span></span>

- [<span data-ttu-id="85eaf-144">Prohlídka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="85eaf-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="85eaf-145">F#referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="85eaf-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="85eaf-146">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="85eaf-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="85eaf-147">Referenční dokumentace symbolů a – operátor</span><span class="sxs-lookup"><span data-stu-id="85eaf-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)

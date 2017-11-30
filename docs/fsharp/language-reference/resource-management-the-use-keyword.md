---
title: "Správa prostředků: Klíčové slovo use (F#)"
description: "Další informace o F # – klíčové slovo 'použití' a 'pomocí, funkce, která můžete ovládat inicializace a verzi zdroje."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 00c3040e-859f-4dad-a7b5-7b8d44dc232c
ms.openlocfilehash: d4e8626f07f1c77e52e8fabd5ccc07dbf1fa8ddd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="resource-management-the-use-keyword"></a><span data-ttu-id="2116f-104">Správa prostředků: Klíčové slovo use</span><span class="sxs-lookup"><span data-stu-id="2116f-104">Resource Management: The use Keyword</span></span>

<span data-ttu-id="2116f-105">Toto téma popisuje klíčové slovo `use` a `using` funkce, které můžete ovládat inicializace a verzi zdroje.</span><span class="sxs-lookup"><span data-stu-id="2116f-105">This topic describes the keyword `use` and the `using` function, which can control the initialization and release of resources.</span></span>

## <a name="resources"></a><span data-ttu-id="2116f-106">Prostředky</span><span class="sxs-lookup"><span data-stu-id="2116f-106">Resources</span></span>
<span data-ttu-id="2116f-107">Termín *prostředků* se používá více než jedním způsobem.</span><span class="sxs-lookup"><span data-stu-id="2116f-107">The term *resource* is used in more than one way.</span></span> <span data-ttu-id="2116f-108">Ano, prostředky mohou být data, která používá aplikace, jako je například řetězce, grafiky a podobně, ale v tomto kontextu *prostředky* odkazuje na prostředky softwaru nebo operačního systému, například kontexty zařízení grafiky, obslužných rutin souborů síť a databáze připojení, objekty souběžnosti jako obslužné rutiny čekání atd.</span><span class="sxs-lookup"><span data-stu-id="2116f-108">Yes, resources can be data that an application uses, such as strings, graphics, and the like, but in this context, *resources* refers to software or operating system resources, such as graphics device contexts, file handles, network and database connections, concurrency objects such as wait handles, and so on.</span></span> <span data-ttu-id="2116f-109">Použití těchto prostředků ve aplikace zahrnuje získání prostředků z operačního systému nebo jiných prostředků poskytovatele, následuje v novějších verzích prostředku do fondu, aby ho lze zadat do jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="2116f-109">The use of these resources by applications involves the acquisition of the resource from the operating system or other resource provider, followed by the later release of the resource to the pool so that it can be provided to another application.</span></span> <span data-ttu-id="2116f-110">Pokud aplikace není uvolnění prostředků zpět do fondu běžné dojde k problémům.</span><span class="sxs-lookup"><span data-stu-id="2116f-110">Problems occur when applications do not release resources back to the common pool.</span></span>

## <a name="managing-resources"></a><span data-ttu-id="2116f-111">Správa prostředků</span><span class="sxs-lookup"><span data-stu-id="2116f-111">Managing Resources</span></span>
<span data-ttu-id="2116f-112">Efektivní a jeho zodpovědné spravovat prostředky v aplikaci, je nutné uvolnit prostředky okamžitě a předvídatelný způsobem.</span><span class="sxs-lookup"><span data-stu-id="2116f-112">To efficiently and responsibly manage resources in an application, you must release resources promptly and in a predictable manner.</span></span> <span data-ttu-id="2116f-113">Rozhraní .NET Framework, pomůže vám to tím, že poskytuje `System.IDisposable` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2116f-113">The .NET Framework helps you do this by providing the `System.IDisposable` interface.</span></span> <span data-ttu-id="2116f-114">Typ, který implementuje `System.IDisposable` má `System.IDisposable.Dispose` metodu, která správně uvolní prostředky.</span><span class="sxs-lookup"><span data-stu-id="2116f-114">A type that implements `System.IDisposable` has the `System.IDisposable.Dispose` method, which correctly frees resources.</span></span> <span data-ttu-id="2116f-115">Správně vytvořené aplikace zaručit, že `System.IDisposable.Dispose` je volána okamžitě, když libovolný objekt, který obsahuje omezené prostředek již není potřeba.</span><span class="sxs-lookup"><span data-stu-id="2116f-115">Well-written applications guarantee that `System.IDisposable.Dispose` is called promptly when any object that holds a limited resource is no longer needed.</span></span> <span data-ttu-id="2116f-116">Naštěstí většině jazyků .NET poskytuje podporu pro zjednodušení a F # není žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="2116f-116">Fortunately, most .NET languages provide support to make this easier, and F# is no exception.</span></span> <span data-ttu-id="2116f-117">Existují dva užitečné jazykové konstrukty, které podporují vzor uvolnění: `use` vazby a `using` funkce.</span><span class="sxs-lookup"><span data-stu-id="2116f-117">There are two useful language constructs that support the dispose pattern: the `use` binding and the `using` function.</span></span>

## <a name="use-binding"></a><span data-ttu-id="2116f-118">Vazbu používají</span><span class="sxs-lookup"><span data-stu-id="2116f-118">use Binding</span></span>
<span data-ttu-id="2116f-119">`use` – Klíčové slovo má formulář, který se podobá se `let` vazby:</span><span class="sxs-lookup"><span data-stu-id="2116f-119">The `use` keyword has a form that resembles that of the `let` binding:</span></span>

<span data-ttu-id="2116f-120">použít *hodnotu* = *výraz*</span><span class="sxs-lookup"><span data-stu-id="2116f-120">use *value* = *expression*</span></span>

<span data-ttu-id="2116f-121">Poskytuje stejné funkce jako `let` vazby, ale přidá volání `Dispose` na hodnotu, pokud hodnota mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="2116f-121">It provides the same functionality as a `let` binding but adds a call to `Dispose` on the value when the value goes out of scope.</span></span> <span data-ttu-id="2116f-122">Všimněte si, že kompilátor vloží kontrolu hodnotu null na základě hodnoty, že pokud je hodnota `null`, volání `Dispose` není pokus.</span><span class="sxs-lookup"><span data-stu-id="2116f-122">Note that the compiler inserts a null check on the value, so that if the value is `null`, the call to `Dispose` is not attempted.</span></span>

<span data-ttu-id="2116f-123">Následující příklad ukazuje, jak zavřít soubor automaticky pomocí `use` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2116f-123">The following example shows how to close a file automatically by using the `use` keyword.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
<span data-ttu-id="2116f-124">Můžete použít `use` v výpočetní výrazy, v takovém případě přizpůsobená verze `use` použit výraz.</span><span class="sxs-lookup"><span data-stu-id="2116f-124">You can use `use` in computation expressions, in which case a customized version of the `use` expression is used.</span></span> <span data-ttu-id="2116f-125">Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výpočetní výrazy](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2116f-125">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="using-function"></a><span data-ttu-id="2116f-126">pomocí funkce</span><span class="sxs-lookup"><span data-stu-id="2116f-126">using Function</span></span>
<span data-ttu-id="2116f-127">`using` Funkce má následující formát:</span><span class="sxs-lookup"><span data-stu-id="2116f-127">The `using` function has the following form:</span></span>

<span data-ttu-id="2116f-128">`using`(*expression1*) *funkce nebo lambda*</span><span class="sxs-lookup"><span data-stu-id="2116f-128">`using` (*expression1*) *function-or-lambda*</span></span>

<span data-ttu-id="2116f-129">V `using` výrazu *expression1* vytvoří objekt, který je nutné odstranit.</span><span class="sxs-lookup"><span data-stu-id="2116f-129">In a `using` expression, *expression1* creates the object that must be disposed.</span></span> <span data-ttu-id="2116f-130">Výsledek *expression1* (objekt, který je nutné odstranit) se změní na argument, *hodnotu*do *funkce nebo lambda*, který je buď funkci, která očekává jedné argument typu, který odpovídá hodnotě zbývající vyprodukované *expression1*, nebo výrazu lambda, která očekává argument daného typu.</span><span class="sxs-lookup"><span data-stu-id="2116f-130">The result of *expression1* (the object that must be disposed) becomes an argument, *value*, to *function-or-lambda*, which is either a function that expects a single remaining argument of a type that matches the value produced by *expression1*, or a lambda expression that expects an argument of that type.</span></span> <span data-ttu-id="2116f-131">Na konci provádění funkce volá modul runtime `Dispose` a uvolní prostředky (Pokud není hodnota `null`, v takovém případě není pokus o volání metody Dispose).</span><span class="sxs-lookup"><span data-stu-id="2116f-131">At the end of the execution of the function, the runtime calls `Dispose` and frees the resources (unless the value is `null`, in which case the call to Dispose is not attempted).</span></span>

<span data-ttu-id="2116f-132">Následující příklad ukazuje `using` výraz s výrazem lambda.</span><span class="sxs-lookup"><span data-stu-id="2116f-132">The following example demonstrates the `using` expression with a lambda expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

<span data-ttu-id="2116f-133">Další příklad ukazuje `using` výraz obsahující funkci.</span><span class="sxs-lookup"><span data-stu-id="2116f-133">The next example shows the `using` expression with a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

<span data-ttu-id="2116f-134">Upozorňujeme, že funkce může být funkci, která má některé argumenty již použita.</span><span class="sxs-lookup"><span data-stu-id="2116f-134">Note that the function could be a function that has some arguments applied already.</span></span> <span data-ttu-id="2116f-135">Následující příklad kódu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="2116f-135">The following code example demonstrates this.</span></span> <span data-ttu-id="2116f-136">Vytvoří soubor, který obsahuje řetězec `XYZ`.</span><span class="sxs-lookup"><span data-stu-id="2116f-136">It creates a file that contains the string `XYZ`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

<span data-ttu-id="2116f-137">`using` Funkce a `use` vazby způsoby téměř ekvivalentní totéž provést.</span><span class="sxs-lookup"><span data-stu-id="2116f-137">The `using` function and the `use` binding are nearly equivalent ways to accomplish the same thing.</span></span> <span data-ttu-id="2116f-138">`using` – Klíčové slovo poskytuje větší kontrolu nad tím, kdy `Dispose` je volána.</span><span class="sxs-lookup"><span data-stu-id="2116f-138">The `using` keyword provides more control over when `Dispose` is called.</span></span> <span data-ttu-id="2116f-139">Při použití `using`, `Dispose` nazývá na konci výrazu funkce nebo lambda; při použití `use` – klíčové slovo, `Dispose` nazývá na konci jsou obsaženy v bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="2116f-139">When you use `using`, `Dispose` is called at the end of the function or lambda expression; when you use the `use` keyword, `Dispose` is called at the end of the containing code block.</span></span> <span data-ttu-id="2116f-140">Obecně platí, měli byste radši chtěli použít `use` místo `using` funkce.</span><span class="sxs-lookup"><span data-stu-id="2116f-140">In general, you should prefer to use `use` instead of the `using` function.</span></span>


## <a name="see-also"></a><span data-ttu-id="2116f-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="2116f-141">See Also</span></span>
[<span data-ttu-id="2116f-142">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="2116f-142">F# Language Reference</span></span>](index.md)

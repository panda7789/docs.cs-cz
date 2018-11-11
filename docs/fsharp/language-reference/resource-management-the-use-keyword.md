---
title: 'Správa prostředků: Klíčové slovo use (F#)'
description: Další informace o F# – klíčové slovo "použití" a "pomocí" funkce, která můžete řídit, inicializace a uvolnění prostředků.
ms.date: 05/16/2016
ms.openlocfilehash: ffa1cb515139a3705920d9d9f79be1a69602f7d8
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "45616059"
---
# <a name="resource-management-the-use-keyword"></a><span data-ttu-id="b7128-103">Správa prostředků: Klíčové slovo use</span><span class="sxs-lookup"><span data-stu-id="b7128-103">Resource Management: The use Keyword</span></span>

<span data-ttu-id="b7128-104">Toto téma popisuje klíčové slovo `use` a `using` funkce, která můžete řídit, inicializace a uvolnění prostředků.</span><span class="sxs-lookup"><span data-stu-id="b7128-104">This topic describes the keyword `use` and the `using` function, which can control the initialization and release of resources.</span></span>

## <a name="resources"></a><span data-ttu-id="b7128-105">Prostředky</span><span class="sxs-lookup"><span data-stu-id="b7128-105">Resources</span></span>

<span data-ttu-id="b7128-106">Termín *prostředků* se používá více než jedním způsobem.</span><span class="sxs-lookup"><span data-stu-id="b7128-106">The term *resource* is used in more than one way.</span></span> <span data-ttu-id="b7128-107">Ano, prostředky můžou být data, která aplikace používá, jako jsou řetězce, grafiku a podobně, ale v tomto kontextu *prostředky* odkazuje na software nebo operační systém prostředky, jako je například kontexty zařízení grafiky, popisovače souborů, sítě a databáze připojení, objekty souběžnosti, jako je například obslužné rutiny čekání a tak dále.</span><span class="sxs-lookup"><span data-stu-id="b7128-107">Yes, resources can be data that an application uses, such as strings, graphics, and the like, but in this context, *resources* refers to software or operating system resources, such as graphics device contexts, file handles, network and database connections, concurrency objects such as wait handles, and so on.</span></span> <span data-ttu-id="b7128-108">Využívání těchto prostředků v aplikacích zahrnuje získání prostředku z operačního systému nebo jiné poskytovatele prostředků, za nímž následuje v novějších verzích prostředku do fondu tak, aby je poskytnout jiná aplikace.</span><span class="sxs-lookup"><span data-stu-id="b7128-108">The use of these resources by applications involves the acquisition of the resource from the operating system or other resource provider, followed by the later release of the resource to the pool so that it can be provided to another application.</span></span> <span data-ttu-id="b7128-109">Když aplikace není uvolnit prostředky zpět do společného fondu dojít k problémům.</span><span class="sxs-lookup"><span data-stu-id="b7128-109">Problems occur when applications do not release resources back to the common pool.</span></span>

## <a name="managing-resources"></a><span data-ttu-id="b7128-110">Správa prostředků</span><span class="sxs-lookup"><span data-stu-id="b7128-110">Managing Resources</span></span>

<span data-ttu-id="b7128-111">Pokud chcete efektivně a zodpovědně spravovat prostředky v aplikaci, musí uvolnit prostředky o tom bezodkladně informuje a předvídatelným způsobem.</span><span class="sxs-lookup"><span data-stu-id="b7128-111">To efficiently and responsibly manage resources in an application, you must release resources promptly and in a predictable manner.</span></span> <span data-ttu-id="b7128-112">Můžete to provést tím, že poskytuje rozhraní .NET Framework pomáhá `System.IDisposable` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b7128-112">The .NET Framework helps you do this by providing the `System.IDisposable` interface.</span></span> <span data-ttu-id="b7128-113">Typ, který implementuje `System.IDisposable` má `System.IDisposable.Dispose` metodu, která správně uvolní prostředky.</span><span class="sxs-lookup"><span data-stu-id="b7128-113">A type that implements `System.IDisposable` has the `System.IDisposable.Dispose` method, which correctly frees resources.</span></span> <span data-ttu-id="b7128-114">Kvalitně napsané aplikace zaručit, že `System.IDisposable.Dispose` se okamžitě volá, když už nepotřebujete libovolný objekt, který obsahuje prostředek omezený.</span><span class="sxs-lookup"><span data-stu-id="b7128-114">Well-written applications guarantee that `System.IDisposable.Dispose` is called promptly when any object that holds a limited resource is no longer needed.</span></span> <span data-ttu-id="b7128-115">Naštěstí Většina jazyků .NET poskytují podporu pro lepší pochopení a F# není žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="b7128-115">Fortunately, most .NET languages provide support to make this easier, and F# is no exception.</span></span> <span data-ttu-id="b7128-116">Existují dvě užitečné jazykovým konstrukcím, které podporují vzor dispose: `use` vazby a `using` funkce.</span><span class="sxs-lookup"><span data-stu-id="b7128-116">There are two useful language constructs that support the dispose pattern: the `use` binding and the `using` function.</span></span>

## <a name="use-binding"></a><span data-ttu-id="b7128-117">Použít vazbu</span><span class="sxs-lookup"><span data-stu-id="b7128-117">use Binding</span></span>

<span data-ttu-id="b7128-118">`use` – Klíčové slovo má formulář, který vypadá podobně jako u `let` vazby:</span><span class="sxs-lookup"><span data-stu-id="b7128-118">The `use` keyword has a form that resembles that of the `let` binding:</span></span>

<span data-ttu-id="b7128-119">použít *hodnotu* = *výraz*</span><span class="sxs-lookup"><span data-stu-id="b7128-119">use *value* = *expression*</span></span>

<span data-ttu-id="b7128-120">Funguje stejně jako `let` vazby, ale přidá volání `Dispose` na hodnotu, pokud hodnota dostane mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="b7128-120">It provides the same functionality as a `let` binding but adds a call to `Dispose` on the value when the value goes out of scope.</span></span> <span data-ttu-id="b7128-121">Všimněte si, že kompilátor vloží kontrolu hodnot null na základě hodnoty tak, že pokud je hodnota `null`, volání `Dispose` nebyl prováděn.</span><span class="sxs-lookup"><span data-stu-id="b7128-121">Note that the compiler inserts a null check on the value, so that if the value is `null`, the call to `Dispose` is not attempted.</span></span>

<span data-ttu-id="b7128-122">Následující příklad ukazuje, jak automaticky zavřete soubor stisknutím kombinace kláves `use` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b7128-122">The following example shows how to close a file automatically by using the `use` keyword.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
<span data-ttu-id="b7128-123">Můžete použít `use` ve výrazech výpočtu. v takovém případě přizpůsobenou verzi `use` výraz je použit.</span><span class="sxs-lookup"><span data-stu-id="b7128-123">You can use `use` in computation expressions, in which case a customized version of the `use` expression is used.</span></span> <span data-ttu-id="b7128-124">Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výrazech výpočtu](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b7128-124">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="using-function"></a><span data-ttu-id="b7128-125">pomocí funkce</span><span class="sxs-lookup"><span data-stu-id="b7128-125">using Function</span></span>

<span data-ttu-id="b7128-126">`using` Funkce má následující formát:</span><span class="sxs-lookup"><span data-stu-id="b7128-126">The `using` function has the following form:</span></span>

<span data-ttu-id="b7128-127">`using` (*expression1*) *lambda nebo funkce*</span><span class="sxs-lookup"><span data-stu-id="b7128-127">`using` (*expression1*) *function-or-lambda*</span></span>

<span data-ttu-id="b7128-128">V `using` výrazu, *expression1* vytvoří objekt, který musí být odstraněn.</span><span class="sxs-lookup"><span data-stu-id="b7128-128">In a `using` expression, *expression1* creates the object that must be disposed.</span></span> <span data-ttu-id="b7128-129">Výsledek *expression1* (objekt, který musí být uvolněn) stane argument, *hodnotu*do *funkce nebo lambda*, což je buď funkci, která očekává, že jeden Zbývající argument typu, který se shoduje s hodnotou vytvářených *expression1*, nebo výraz lambda, který očekává argument daného typu.</span><span class="sxs-lookup"><span data-stu-id="b7128-129">The result of *expression1* (the object that must be disposed) becomes an argument, *value*, to *function-or-lambda*, which is either a function that expects a single remaining argument of a type that matches the value produced by *expression1*, or a lambda expression that expects an argument of that type.</span></span> <span data-ttu-id="b7128-130">Na konci spuštění funkce, modul runtime volá `Dispose` a uvolní prostředky (Pokud není hodnota `null`, v takovém případě se pokus o volání metody Dispose).</span><span class="sxs-lookup"><span data-stu-id="b7128-130">At the end of the execution of the function, the runtime calls `Dispose` and frees the resources (unless the value is `null`, in which case the call to Dispose is not attempted).</span></span>

<span data-ttu-id="b7128-131">Následující příklad ukazuje, `using` výrazem lambda výraz.</span><span class="sxs-lookup"><span data-stu-id="b7128-131">The following example demonstrates the `using` expression with a lambda expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

<span data-ttu-id="b7128-132">Další příklad ukazuje `using` výraz s funkcí.</span><span class="sxs-lookup"><span data-stu-id="b7128-132">The next example shows the `using` expression with a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

<span data-ttu-id="b7128-133">Všimněte si, že funkce může být funkce, která obsahuje některé argumenty již použity.</span><span class="sxs-lookup"><span data-stu-id="b7128-133">Note that the function could be a function that has some arguments applied already.</span></span> <span data-ttu-id="b7128-134">Následující příklad kódu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="b7128-134">The following code example demonstrates this.</span></span> <span data-ttu-id="b7128-135">Vytvoří soubor, který obsahuje řetězec `XYZ`.</span><span class="sxs-lookup"><span data-stu-id="b7128-135">It creates a file that contains the string `XYZ`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

<span data-ttu-id="b7128-136">`using` Funkce a `use` vazby jsou téměř ekvivalentní způsoby, jak provést totéž.</span><span class="sxs-lookup"><span data-stu-id="b7128-136">The `using` function and the `use` binding are nearly equivalent ways to accomplish the same thing.</span></span> <span data-ttu-id="b7128-137">`using` – Klíčové slovo poskytuje větší kontrolu nad tím, kdy `Dispose` je volána.</span><span class="sxs-lookup"><span data-stu-id="b7128-137">The `using` keyword provides more control over when `Dispose` is called.</span></span> <span data-ttu-id="b7128-138">Při použití `using`, `Dispose` je volána na konci funkce nebo lambda výraz; při použití `use` – klíčové slovo, `Dispose` je volána na konci bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="b7128-138">When you use `using`, `Dispose` is called at the end of the function or lambda expression; when you use the `use` keyword, `Dispose` is called at the end of the containing code block.</span></span> <span data-ttu-id="b7128-139">Obecně platí, měli byste radši chtěli použít `use` místo `using` funkce.</span><span class="sxs-lookup"><span data-stu-id="b7128-139">In general, you should prefer to use `use` instead of the `using` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7128-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7128-140">See also</span></span>

- [<span data-ttu-id="b7128-141">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="b7128-141">F# Language Reference</span></span>](index.md)

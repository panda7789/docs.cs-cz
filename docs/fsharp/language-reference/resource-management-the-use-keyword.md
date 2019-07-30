---
title: 'Správa prostředků: Klíčové slovo use'
description: Přečtěte si F# o klíčovém slově use a funkci using, která může řídit inicializaci a vydání prostředků.
ms.date: 05/16/2016
ms.openlocfilehash: 5e0838401bee02050343b2f6dcc646a8dc8b4dc0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627254"
---
# <a name="resource-management-the-use-keyword"></a><span data-ttu-id="4a20b-103">Správa prostředků: Klíčové slovo use</span><span class="sxs-lookup"><span data-stu-id="4a20b-103">Resource Management: The use Keyword</span></span>

<span data-ttu-id="4a20b-104">Toto téma popisuje klíčové slovo `use` `using` a funkci, která může řídit inicializaci a vydání prostředků.</span><span class="sxs-lookup"><span data-stu-id="4a20b-104">This topic describes the keyword `use` and the `using` function, which can control the initialization and release of resources.</span></span>

## <a name="resources"></a><span data-ttu-id="4a20b-105">Prostředky</span><span class="sxs-lookup"><span data-stu-id="4a20b-105">Resources</span></span>

<span data-ttu-id="4a20b-106">Pojem *prostředku* je používán více než jedním způsobem.</span><span class="sxs-lookup"><span data-stu-id="4a20b-106">The term *resource* is used in more than one way.</span></span> <span data-ttu-id="4a20b-107">Ano, prostředky mohou být data, která aplikace používá, jako jsou například řetězce, grafika a podobně, ale v tomto kontextu *prostředky* odkazují na prostředky softwaru nebo operačního systému, jako jsou například kontexty grafických zařízení, popisovače souborů, síť a databáze. připojení, objekty souběžnosti, například obslužné rutiny čekání a tak dále.</span><span class="sxs-lookup"><span data-stu-id="4a20b-107">Yes, resources can be data that an application uses, such as strings, graphics, and the like, but in this context, *resources* refers to software or operating system resources, such as graphics device contexts, file handles, network and database connections, concurrency objects such as wait handles, and so on.</span></span> <span data-ttu-id="4a20b-108">Použití těchto prostředků podle aplikací zahrnuje získání prostředku z operačního systému nebo jiného poskytovatele prostředků, za nímž následuje pozdější vydání prostředku, aby bylo možné ho poskytnout jiné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4a20b-108">The use of these resources by applications involves the acquisition of the resource from the operating system or other resource provider, followed by the later release of the resource to the pool so that it can be provided to another application.</span></span> <span data-ttu-id="4a20b-109">K problémům dochází, když aplikace neuvolní prostředky zpátky do společného fondu.</span><span class="sxs-lookup"><span data-stu-id="4a20b-109">Problems occur when applications do not release resources back to the common pool.</span></span>

## <a name="managing-resources"></a><span data-ttu-id="4a20b-110">Správa prostředků</span><span class="sxs-lookup"><span data-stu-id="4a20b-110">Managing Resources</span></span>

<span data-ttu-id="4a20b-111">Aby bylo možné efektivně a zodpovědnou spravovat prostředky v aplikaci, je třeba uvolnit prostředky bez výzvy a předvídatelným způsobem.</span><span class="sxs-lookup"><span data-stu-id="4a20b-111">To efficiently and responsibly manage resources in an application, you must release resources promptly and in a predictable manner.</span></span> <span data-ttu-id="4a20b-112">.NET Framework to usnadňuje tím, že poskytuje `System.IDisposable` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4a20b-112">The .NET Framework helps you do this by providing the `System.IDisposable` interface.</span></span> <span data-ttu-id="4a20b-113">Typ, který implementuje `System.IDisposable` , `System.IDisposable.Dispose` má metodu, která správně uvolňuje prostředky.</span><span class="sxs-lookup"><span data-stu-id="4a20b-113">A type that implements `System.IDisposable` has the `System.IDisposable.Dispose` method, which correctly frees resources.</span></span> <span data-ttu-id="4a20b-114">Správné zapsané aplikace zaručují, `System.IDisposable.Dispose` že se říká výzva, když už nebude potřeba libovolný objekt, který obsahuje omezený prostředek.</span><span class="sxs-lookup"><span data-stu-id="4a20b-114">Well-written applications guarantee that `System.IDisposable.Dispose` is called promptly when any object that holds a limited resource is no longer needed.</span></span> <span data-ttu-id="4a20b-115">Naštěstí většina jazyků .NET poskytuje podporu, aby to bylo snazší, a F# nejedná se o žádnou výjimku.</span><span class="sxs-lookup"><span data-stu-id="4a20b-115">Fortunately, most .NET languages provide support to make this easier, and F# is no exception.</span></span> <span data-ttu-id="4a20b-116">Existují dvě užitečné jazykové konstrukce, které podporují vzor Dispose: `use` vazbu `using` a funkci.</span><span class="sxs-lookup"><span data-stu-id="4a20b-116">There are two useful language constructs that support the dispose pattern: the `use` binding and the `using` function.</span></span>

## <a name="use-binding"></a><span data-ttu-id="4a20b-117">použití vazby</span><span class="sxs-lookup"><span data-stu-id="4a20b-117">use Binding</span></span>

<span data-ttu-id="4a20b-118">Klíčové slovo má formulář, který se podobá `let` vazbě: `use`</span><span class="sxs-lookup"><span data-stu-id="4a20b-118">The `use` keyword has a form that resembles that of the `let` binding:</span></span>

<span data-ttu-id="4a20b-119">*výraz* použití *hodnoty* = </span><span class="sxs-lookup"><span data-stu-id="4a20b-119">use *value* = *expression*</span></span>

<span data-ttu-id="4a20b-120">Poskytuje stejné funkce jako `let` vazby, ale přidává `Dispose` volání na hodnotu, když se hodnota překročí rozsahu.</span><span class="sxs-lookup"><span data-stu-id="4a20b-120">It provides the same functionality as a `let` binding but adds a call to `Dispose` on the value when the value goes out of scope.</span></span> <span data-ttu-id="4a20b-121">Všimněte si, že kompilátor vloží u hodnoty hodnotu null, takže pokud je `null`hodnota, `Dispose` volání není prováděno.</span><span class="sxs-lookup"><span data-stu-id="4a20b-121">Note that the compiler inserts a null check on the value, so that if the value is `null`, the call to `Dispose` is not attempted.</span></span>

<span data-ttu-id="4a20b-122">Následující příklad ukazuje, jak automaticky zavřít soubor pomocí `use` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="4a20b-122">The following example shows how to close a file automatically by using the `use` keyword.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> <span data-ttu-id="4a20b-123">Můžete použít `use` ve výrazech výpočtu. v takovém případě se používá přizpůsobená verze `use` výrazu.</span><span class="sxs-lookup"><span data-stu-id="4a20b-123">You can use `use` in computation expressions, in which case a customized version of the `use` expression is used.</span></span> <span data-ttu-id="4a20b-124">Další informace najdete v tématu [sekvence](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md)a [výpočetní výrazy](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4a20b-124">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="using-function"></a><span data-ttu-id="4a20b-125">použití funkce</span><span class="sxs-lookup"><span data-stu-id="4a20b-125">using Function</span></span>

<span data-ttu-id="4a20b-126">`using` Funkce má následující tvar:</span><span class="sxs-lookup"><span data-stu-id="4a20b-126">The `using` function has the following form:</span></span>

<span data-ttu-id="4a20b-127">`using`(*expression1*) *Function nebo lambda*</span><span class="sxs-lookup"><span data-stu-id="4a20b-127">`using` (*expression1*) *function-or-lambda*</span></span>

<span data-ttu-id="4a20b-128">Ve výrazu Výraz1 vytvoří objekt, který musí být uvolněn. `using`</span><span class="sxs-lookup"><span data-stu-id="4a20b-128">In a `using` expression, *expression1* creates the object that must be disposed.</span></span> <span data-ttu-id="4a20b-129">Výsledek *Výraz1* (objekt, který musí být vyřazen), se může jednat o argument, *hodnotu*, *funkci nebo-lambda*, což je funkce, která očekává jeden zbývající argument typu, který odpovídá hodnotě vytvořené  *Výraz1*nebo lambda výraz, který očekává argument tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="4a20b-129">The result of *expression1* (the object that must be disposed) becomes an argument, *value*, to *function-or-lambda*, which is either a function that expects a single remaining argument of a type that matches the value produced by *expression1*, or a lambda expression that expects an argument of that type.</span></span> <span data-ttu-id="4a20b-130">Na konci provádění funkce zavolá `Dispose` modul runtime a uvolní prostředky (Pokud hodnota není `null`, v takovém případě se volání metody Dispose nezkouší).</span><span class="sxs-lookup"><span data-stu-id="4a20b-130">At the end of the execution of the function, the runtime calls `Dispose` and frees the resources (unless the value is `null`, in which case the call to Dispose is not attempted).</span></span>

<span data-ttu-id="4a20b-131">Následující příklad ukazuje `using` výraz s výrazem lambda.</span><span class="sxs-lookup"><span data-stu-id="4a20b-131">The following example demonstrates the `using` expression with a lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

<span data-ttu-id="4a20b-132">Následující příklad ukazuje `using` výraz s funkcí.</span><span class="sxs-lookup"><span data-stu-id="4a20b-132">The next example shows the `using` expression with a function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

<span data-ttu-id="4a20b-133">Všimněte si, že funkce může být funkce, která již používá některé argumenty.</span><span class="sxs-lookup"><span data-stu-id="4a20b-133">Note that the function could be a function that has some arguments applied already.</span></span> <span data-ttu-id="4a20b-134">Následující příklad kódu to demonstruje.</span><span class="sxs-lookup"><span data-stu-id="4a20b-134">The following code example demonstrates this.</span></span> <span data-ttu-id="4a20b-135">Vytvoří soubor, který obsahuje řetězec `XYZ`.</span><span class="sxs-lookup"><span data-stu-id="4a20b-135">It creates a file that contains the string `XYZ`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

<span data-ttu-id="4a20b-136">`using` Funkce`use` a vazba jsou skoro ekvivalentní způsob, jak dosáhnout stejné věci.</span><span class="sxs-lookup"><span data-stu-id="4a20b-136">The `using` function and the `use` binding are nearly equivalent ways to accomplish the same thing.</span></span> <span data-ttu-id="4a20b-137">Klíčové slovo poskytuje větší kontrolu nad tím `Dispose` , kdy je volána. `using`</span><span class="sxs-lookup"><span data-stu-id="4a20b-137">The `using` keyword provides more control over when `Dispose` is called.</span></span> <span data-ttu-id="4a20b-138">Když použijete `using`, `Dispose` je volána na konci funkce nebo výrazu lambda `use` ; při použití klíčového slova `Dispose` je volána na konci obsahujícího bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="4a20b-138">When you use `using`, `Dispose` is called at the end of the function or lambda expression; when you use the `use` keyword, `Dispose` is called at the end of the containing code block.</span></span> <span data-ttu-id="4a20b-139">Obecně byste měli raději použít `use` místo `using` funkce.</span><span class="sxs-lookup"><span data-stu-id="4a20b-139">In general, you should prefer to use `use` instead of the `using` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a20b-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a20b-140">See also</span></span>

- [<span data-ttu-id="4a20b-141">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="4a20b-141">F# Language Reference</span></span>](index.md)

---
title: Uživatelsky definované funkce
ms.date: 12/13/2019
description: Naučte se vytvářet uživatelsky definované skalární a agregační funkce.
ms.openlocfilehash: 9ee3fbac73215353c8dc82199203b0d25e580cdb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447172"
---
# <a name="user-defined-functions"></a><span data-ttu-id="10e2e-103">Uživatelsky definované funkce</span><span class="sxs-lookup"><span data-stu-id="10e2e-103">User-defined functions</span></span>

<span data-ttu-id="10e2e-104">Většina databází obsahuje procedurální dialekt SQL, který můžete použít k definování vlastních funkcí.</span><span class="sxs-lookup"><span data-stu-id="10e2e-104">Most databases have a procedural dialect of SQL that you can use to define your own functions.</span></span> <span data-ttu-id="10e2e-105">SQLite se ale v rámci vaší aplikace spouští v procesu.</span><span class="sxs-lookup"><span data-stu-id="10e2e-105">SQLite however, runs in-process with your app.</span></span> <span data-ttu-id="10e2e-106">Místo toho, abyste se seznámili s novým dialektem SQL, můžete pouze použít programovací jazyk vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="10e2e-106">Instead of having to learn a new dialect of SQL, you can just use the programming language of your app.</span></span>

## <a name="scalar-functions"></a><span data-ttu-id="10e2e-107">Skalární funkce</span><span class="sxs-lookup"><span data-stu-id="10e2e-107">Scalar functions</span></span>

<span data-ttu-id="10e2e-108">Skalární funkce vrací jednu skalární hodnotu pro každý řádek v dotazu.</span><span class="sxs-lookup"><span data-stu-id="10e2e-108">Scalar functions return a single, scalar value for each row in a query.</span></span> <span data-ttu-id="10e2e-109">Definujte nové skalární funkce a přepište vestavěné objekty pomocí <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.</span><span class="sxs-lookup"><span data-stu-id="10e2e-109">Define new scalar functions and override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.</span></span>

<span data-ttu-id="10e2e-110">Seznam podporovaných parametrů a návratových typů pro argument `func` naleznete v tématu [datové typy](types.md) .</span><span class="sxs-lookup"><span data-stu-id="10e2e-110">See [Data types](types.md) for a list of supported parameter and return types for the `func` argument.</span></span>

<span data-ttu-id="10e2e-111">Zadáním argumentu `state` předáte tuto hodnotu do každého vyvolání funkce.</span><span class="sxs-lookup"><span data-stu-id="10e2e-111">Specifying the `state` argument will pass that value into every invocation of the function.</span></span> <span data-ttu-id="10e2e-112">Použijte k tomu, abyste se vyhnuli uzávěrům.</span><span class="sxs-lookup"><span data-stu-id="10e2e-112">Use this to avoid closures.</span></span>

<span data-ttu-id="10e2e-113">Zadejte `isDeterministic`, pokud je funkce deterministické, aby mohl SQLite použít při kompilování dotazů další optimalizace.</span><span class="sxs-lookup"><span data-stu-id="10e2e-113">Specify `isDeterministic` if your function is deterministic to allow SQLite to use additional optimizations when compiling queries.</span></span>

<span data-ttu-id="10e2e-114">Následující příklad ukazuje, jak přidat skalární funkci pro výpočet poloměru válce.</span><span class="sxs-lookup"><span data-stu-id="10e2e-114">The following example shows how to add a scalar function to calculate the radius of a cylinder.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ScalarFunctionSample/Program.cs?name=snippet_CreateFunction)]

## <a name="operators"></a><span data-ttu-id="10e2e-115">Operátory</span><span class="sxs-lookup"><span data-stu-id="10e2e-115">Operators</span></span>

<span data-ttu-id="10e2e-116">Následující operátory SQLite jsou implementovány pomocí odpovídajících skalárních funkcí.</span><span class="sxs-lookup"><span data-stu-id="10e2e-116">The following SQLite operators are implemented by corresponding scalar functions.</span></span> <span data-ttu-id="10e2e-117">Definování těchto skalárních funkcí v aplikaci přepíše chování těchto operátorů.</span><span class="sxs-lookup"><span data-stu-id="10e2e-117">Defining these scalar functions in your app will override the behavior of these operators.</span></span>

| <span data-ttu-id="10e2e-118">Operátor</span><span class="sxs-lookup"><span data-stu-id="10e2e-118">Operator</span></span>          | <span data-ttu-id="10e2e-119">Funkce</span><span class="sxs-lookup"><span data-stu-id="10e2e-119">Function</span></span>      |
| ----------------- | ------------- |
| <span data-ttu-id="10e2e-120">X GLOB Y</span><span class="sxs-lookup"><span data-stu-id="10e2e-120">X GLOB Y</span></span>          | <span data-ttu-id="10e2e-121">glob (Y, X)</span><span class="sxs-lookup"><span data-stu-id="10e2e-121">glob(Y, X)</span></span>    |
| <span data-ttu-id="10e2e-122">X JAKO Y</span><span class="sxs-lookup"><span data-stu-id="10e2e-122">X LIKE Y</span></span>          | <span data-ttu-id="10e2e-123">like (Y, X)</span><span class="sxs-lookup"><span data-stu-id="10e2e-123">like(Y, X)</span></span>    |
| <span data-ttu-id="10e2e-124">X JAKO Y ESCAPE Z</span><span class="sxs-lookup"><span data-stu-id="10e2e-124">X LIKE Y ESCAPE Z</span></span> | <span data-ttu-id="10e2e-125">like (Y, X, Z)</span><span class="sxs-lookup"><span data-stu-id="10e2e-125">like(Y, X, Z)</span></span> |
| <span data-ttu-id="10e2e-126">× ODPOVÍDÁ Y</span><span class="sxs-lookup"><span data-stu-id="10e2e-126">X MATCH Y</span></span>         | <span data-ttu-id="10e2e-127">shoda (Y, X)</span><span class="sxs-lookup"><span data-stu-id="10e2e-127">match(Y, X)</span></span>   |
| <span data-ttu-id="10e2e-128">X REGEXP Y</span><span class="sxs-lookup"><span data-stu-id="10e2e-128">X REGEXP Y</span></span>        | <span data-ttu-id="10e2e-129">RegExp (Y, X)</span><span class="sxs-lookup"><span data-stu-id="10e2e-129">regexp(Y, X)</span></span>  |

<span data-ttu-id="10e2e-130">Následující příklad ukazuje, jak definovat funkci RegExp pro povolení odpovídajícího operátoru.</span><span class="sxs-lookup"><span data-stu-id="10e2e-130">The following example shows how to define the regexp function to enable its corresponding operator.</span></span> <span data-ttu-id="10e2e-131">SQLite neobsahuje výchozí implementaci funkce RegExp.</span><span class="sxs-lookup"><span data-stu-id="10e2e-131">SQLite doesn't include a default implementation of the regexp function.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/RegularExpressionSample/Program.cs?name=snippet_Regex)]

## <a name="aggregate-functions"></a><span data-ttu-id="10e2e-132">Agregační funkce</span><span class="sxs-lookup"><span data-stu-id="10e2e-132">Aggregate functions</span></span>

<span data-ttu-id="10e2e-133">Agregační funkce vrací jednu agregovanou hodnotu pro všechny řádky v dotazu.</span><span class="sxs-lookup"><span data-stu-id="10e2e-133">Aggregate functions return a single, aggregated value for all the rows in a query.</span></span> <span data-ttu-id="10e2e-134">Definování a přepsání agregačních funkcí pomocí <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>.</span><span class="sxs-lookup"><span data-stu-id="10e2e-134">Define and override aggregate functions using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>.</span></span>

<span data-ttu-id="10e2e-135">Argument `seed` Určuje počáteční stav kontextu.</span><span class="sxs-lookup"><span data-stu-id="10e2e-135">The `seed` argument specifies the initial state of the context.</span></span> <span data-ttu-id="10e2e-136">Toto použijte, chcete-li se vyhnout uzávěrům také.</span><span class="sxs-lookup"><span data-stu-id="10e2e-136">Use this to avoid closures also.</span></span>

<span data-ttu-id="10e2e-137">Argument `func` je vyvolán jednou na řádek.</span><span class="sxs-lookup"><span data-stu-id="10e2e-137">The `func` argument is invoked once per row.</span></span> <span data-ttu-id="10e2e-138">Pomocí kontextu nashromáždíte konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="10e2e-138">Use the context to accumulate a final result.</span></span> <span data-ttu-id="10e2e-139">Vrátí kontext.</span><span class="sxs-lookup"><span data-stu-id="10e2e-139">Return the context.</span></span> <span data-ttu-id="10e2e-140">Tento model umožňuje, aby kontext byl typ hodnoty nebo neměnný.</span><span class="sxs-lookup"><span data-stu-id="10e2e-140">This pattern allows the context to be a value type or immutable.</span></span>

<span data-ttu-id="10e2e-141">Pokud není zadán žádný `resultSelector`, jako výsledek se použije konečný stav kontextu.</span><span class="sxs-lookup"><span data-stu-id="10e2e-141">If no `resultSelector` is specified, the final state of the context is used as the result.</span></span> <span data-ttu-id="10e2e-142">To může zjednodušit definici funkcí, jako je součet a počet, které potřebují pouze zvyšovat počet řádků a vracet je.</span><span class="sxs-lookup"><span data-stu-id="10e2e-142">This can simplify the definition of functions like sum and count that only need to increment a number each row and return it.</span></span>

<span data-ttu-id="10e2e-143">Zadejte `resultSelector` pro výpočet konečného výsledku z kontextu po provedení iterace na všech řádcích.</span><span class="sxs-lookup"><span data-stu-id="10e2e-143">Specify `resultSelector` to calculate the final result from the context after iterating through all the rows.</span></span>

<span data-ttu-id="10e2e-144">Seznam podporovaných typů parametrů pro `func` argument a návratové typy pro `resultSelector`naleznete v tématu [datové typy](types.md) .</span><span class="sxs-lookup"><span data-stu-id="10e2e-144">See [Data types](types.md) for a list of supported parameter types for the `func` argument and return types for `resultSelector`.</span></span>

<span data-ttu-id="10e2e-145">Pokud je funkce deterministické, určete `isDeterministic`, aby mohl SQLite použít při kompilování dotazů další optimalizace.</span><span class="sxs-lookup"><span data-stu-id="10e2e-145">If your function is deterministic, specify `isDeterministic` to allow SQLite to use additional optimizations when compiling queries.</span></span>

<span data-ttu-id="10e2e-146">Následující příklad definuje agregační funkci pro výpočet směrodatné odchylky sloupce.</span><span class="sxs-lookup"><span data-stu-id="10e2e-146">The following example defines an aggregate function to calculate the standard deviation of a column.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AggregateFunctionSample/Program.cs?name=snippet_CreateAggregate)]

## <a name="errors"></a><span data-ttu-id="10e2e-147">Chyby</span><span class="sxs-lookup"><span data-stu-id="10e2e-147">Errors</span></span>

<span data-ttu-id="10e2e-148">Pokud uživatelsky definovaná funkce vyvolá výjimku, zpráva se vrátí do SQLite.</span><span class="sxs-lookup"><span data-stu-id="10e2e-148">If a user-defined function throws an exception, the message is returned to SQLite.</span></span> <span data-ttu-id="10e2e-149">SQLite potom vyvolá chybu a Microsoft. data. sqlite vyvolá výjimku SqliteException.</span><span class="sxs-lookup"><span data-stu-id="10e2e-149">SQLite will then raise an error and Microsoft.Data.Sqlite will throw a SqliteException.</span></span> <span data-ttu-id="10e2e-150">Další informace najdete v tématu [chyby databáze](database-errors.md).</span><span class="sxs-lookup"><span data-stu-id="10e2e-150">For more information, see [Database errors](database-errors.md).</span></span>

<span data-ttu-id="10e2e-151">Ve výchozím nastavení se kód chyby SQLite chyby SQLITE_ERROR (nebo 1).</span><span class="sxs-lookup"><span data-stu-id="10e2e-151">By default, the error SQLite error code will be SQLITE_ERROR (or 1).</span></span> <span data-ttu-id="10e2e-152">Můžete ji však změnit vyvoláním <xref:Microsoft.Data.Sqlite.SqliteException> ve vaší funkci s požadovaným <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode>.</span><span class="sxs-lookup"><span data-stu-id="10e2e-152">You can, however, change it by throwing a <xref:Microsoft.Data.Sqlite.SqliteException> in your function with the desired <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> specified.</span></span>

## <a name="debugging"></a><span data-ttu-id="10e2e-153">Ladění</span><span class="sxs-lookup"><span data-stu-id="10e2e-153">Debugging</span></span>

<span data-ttu-id="10e2e-154">SQLite volá vaši implementaci přímo.</span><span class="sxs-lookup"><span data-stu-id="10e2e-154">SQLite calls your implementation directly.</span></span> <span data-ttu-id="10e2e-155">To umožňuje přidat zarážky, které se aktivují, zatímco SQLite vyhodnocuje dotazy.</span><span class="sxs-lookup"><span data-stu-id="10e2e-155">This lets you add breakpoints that trigger while SQLite is evaluating queries.</span></span> <span data-ttu-id="10e2e-156">K dispozici je plné rozhraní .NET pro ladění, které vám může pomáhat při vytváření uživatelem definovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="10e2e-156">The full .NET debugging experience is available to help you create your user-defined functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="10e2e-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10e2e-157">See also</span></span>

* [<span data-ttu-id="10e2e-158">Datové typy</span><span class="sxs-lookup"><span data-stu-id="10e2e-158">Data types</span></span>](types.md)
* [<span data-ttu-id="10e2e-159">Základní funkce SQLite</span><span class="sxs-lookup"><span data-stu-id="10e2e-159">SQLite Core functions</span></span>](https://www.sqlite.org/lang_corefunc.html)
* [<span data-ttu-id="10e2e-160">Agregační funkce SQLite</span><span class="sxs-lookup"><span data-stu-id="10e2e-160">SQLite Aggregate Functions</span></span>](https://www.sqlite.org/lang_aggfunc.html)

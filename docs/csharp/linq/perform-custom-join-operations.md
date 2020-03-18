---
title: Provedení operací vlastního spojení (LINQ v C#)
description: Zjistěte, jak provádět vlastní operace připojení LINQ v c#.
ms.date: 12/01/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: 7051007c67bd64cd11ede2f4d5352ce3d497255f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659849"
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="8eae0-103">Provádění vlastních operací spojování</span><span class="sxs-lookup"><span data-stu-id="8eae0-103">Perform custom join operations</span></span>

<span data-ttu-id="8eae0-104">Tento příklad ukazuje, jak provádět operace spojení, `join` které nejsou možné s klauzulí.</span><span class="sxs-lookup"><span data-stu-id="8eae0-104">This example shows how to perform join operations that aren't possible with the `join` clause.</span></span> <span data-ttu-id="8eae0-105">Ve výrazu dotazu `join` je klauzule omezena na a optimalizovaná pro equijoins, které jsou zdaleka nejběžnějším typem operace spojení.</span><span class="sxs-lookup"><span data-stu-id="8eae0-105">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="8eae0-106">Při provádění equijoin, budete pravděpodobně vždy získat nejlepší `join` výkon pomocí klauzule.</span><span class="sxs-lookup"><span data-stu-id="8eae0-106">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>

<span data-ttu-id="8eae0-107">Doložka `join` však nemůže být použita v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="8eae0-107">However, the `join` clause cannot be used in the following cases:</span></span>

- <span data-ttu-id="8eae0-108">Když je spojení založeno na výrazu nerovnosti (neequijoin).</span><span class="sxs-lookup"><span data-stu-id="8eae0-108">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>

- <span data-ttu-id="8eae0-109">Když je spojení založeno na více než jednom výrazu rovnosti nebo nerovnosti.</span><span class="sxs-lookup"><span data-stu-id="8eae0-109">When the join is predicated on more than one expression of equality or inequality.</span></span>

- <span data-ttu-id="8eae0-110">Pokud máte zavést dočasnou proměnnou rozsahu pro pravé straně (vnitřní) sekvence před operací spojení.</span><span class="sxs-lookup"><span data-stu-id="8eae0-110">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>

 <span data-ttu-id="8eae0-111">Chcete-li provést spojení, která nejsou equijoins, můžete použít více `from` klauzulí zavést každý zdroj dat nezávisle.</span><span class="sxs-lookup"><span data-stu-id="8eae0-111">To perform joins that aren't equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="8eae0-112">Potom použít predikát výraz `where` v klauzuli na proměnnou rozsahu pro každý zdroj.</span><span class="sxs-lookup"><span data-stu-id="8eae0-112">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="8eae0-113">Výraz může mít také podobu volání metody.</span><span class="sxs-lookup"><span data-stu-id="8eae0-113">The expression also can take the form of a method call.</span></span>

> [!NOTE]
> <span data-ttu-id="8eae0-114">Nezaměňujte tento druh operace vlastního spojení `from` s použitím více klauzulí pro přístup k vnitřní kolekce.</span><span class="sxs-lookup"><span data-stu-id="8eae0-114">Don't confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="8eae0-115">Další informace naleznete v tématu [join clause](../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8eae0-115">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="8eae0-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="8eae0-116">Example</span></span>

<span data-ttu-id="8eae0-117">První metoda v následujícím příkladu ukazuje jednoduché křížové spojení.</span><span class="sxs-lookup"><span data-stu-id="8eae0-117">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="8eae0-118">Křížová spojení musí být používána s opatrností, protože mohou vytvářet velmi velké sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="8eae0-118">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="8eae0-119">Však mohou být užitečné v některých scénářích pro vytváření zdrojových sekvencí, proti kterému jsou spuštěny další dotazy.</span><span class="sxs-lookup"><span data-stu-id="8eae0-119">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>

<span data-ttu-id="8eae0-120">Druhá metoda vytváří posloupnost všech produktů, jejichž ID kategorie je uveden v seznamu kategorií na levé straně.</span><span class="sxs-lookup"><span data-stu-id="8eae0-120">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="8eae0-121">Všimněte si `let` použití klauzule a `Contains` metody k vytvoření dočasného pole.</span><span class="sxs-lookup"><span data-stu-id="8eae0-121">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="8eae0-122">Je také možné vytvořit pole před dotazem `from` a odstranit první klauzuli.</span><span class="sxs-lookup"><span data-stu-id="8eae0-122">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a><span data-ttu-id="8eae0-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="8eae0-123">Example</span></span>

<span data-ttu-id="8eae0-124">V následujícím příkladu dotaz musí spojit dvě sekvence založené na odpovídající klíče, které v případě vnitřní (pravé straně) sekvence, nelze získat před join klauzule sám.</span><span class="sxs-lookup"><span data-stu-id="8eae0-124">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="8eae0-125">Pokud toto spojení `join` byly provedeny `Split` s klauzulí, pak metoda by musela být volána pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="8eae0-125">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="8eae0-126">Použití více `from` klauzulí umožňuje dotazu, aby se zabránilo režii volání opakované metody.</span><span class="sxs-lookup"><span data-stu-id="8eae0-126">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="8eae0-127">Nicméně vzhledem k tomu, `join` je optimalizován, v tomto `from` konkrétním případě může být stále rychlejší než použití více klauzulí.</span><span class="sxs-lookup"><span data-stu-id="8eae0-127">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="8eae0-128">Výsledky se budou lišit především v závislosti na tom, jak nákladné je volání metody.</span><span class="sxs-lookup"><span data-stu-id="8eae0-128">The results will vary depending primarily on how expensive the method call is.</span></span>

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a><span data-ttu-id="8eae0-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="8eae0-129">See also</span></span>

- [<span data-ttu-id="8eae0-130">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="8eae0-130">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="8eae0-131">spojit klauzuli</span><span class="sxs-lookup"><span data-stu-id="8eae0-131">join clause</span></span>](../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="8eae0-132">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="8eae0-132">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)

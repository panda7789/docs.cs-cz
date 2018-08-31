---
title: Provádění vlastních operací spojování (LINQ v JAZYKU C#)
description: Zjistěte, jak k provádění vlastních operací spojování LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: a0e08396c006f68949357c50a28b3b0982f0dd83
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331860"
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="87938-103">Provádění vlastních operací spojování</span><span class="sxs-lookup"><span data-stu-id="87938-103">Perform custom join operations</span></span>

<span data-ttu-id="87938-104">Tento příklad ukazuje, jak provádět operace spojení, které nejsou možné s `join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="87938-104">This example shows how to perform join operations that aren't possible with the `join` clause.</span></span> <span data-ttu-id="87938-105">Ve výrazu dotazu `join` klauzule je omezená na a optimalizovaná pro equijoins, které jsou jednoznačně nejpopulárnější nejběžnější typ operace spojení.</span><span class="sxs-lookup"><span data-stu-id="87938-105">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="87938-106">Při provádění porovnávání, bude pravděpodobně vždy získat nejlepší výkon pomocí `join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="87938-106">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>

<span data-ttu-id="87938-107">Ale `join` klauzuli nelze použít v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="87938-107">However, the `join` clause cannot be used in the following cases:</span></span>

- <span data-ttu-id="87938-108">Když se spojení záleží na výraz nerovnosti (jiných porovnávání).</span><span class="sxs-lookup"><span data-stu-id="87938-108">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>

- <span data-ttu-id="87938-109">Když se spojení záleží na více než jeden výraz rovnosti nebo nerovnosti.</span><span class="sxs-lookup"><span data-stu-id="87938-109">When the join is predicated on more than one expression of equality or inequality.</span></span>

- <span data-ttu-id="87938-110">Pokud máte zavést proměnnou rozsahu dočasný pro pořadí (vnitřní) na pravé straně před provedením operace spojení.</span><span class="sxs-lookup"><span data-stu-id="87938-110">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>

 <span data-ttu-id="87938-111">K provedení spojení, které nejsou equijoins, lze použít více `from` klauzule zavést každý zdroj dat nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="87938-111">To perform joins that aren't equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="87938-112">Pak použijete v predikátu výraz `where` klauzule pro proměnnou rozsahu pro každý zdroj.</span><span class="sxs-lookup"><span data-stu-id="87938-112">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="87938-113">Výraz také můžou mít podobu volání metody.</span><span class="sxs-lookup"><span data-stu-id="87938-113">The expression also can take the form of a method call.</span></span>

> [!NOTE]
> <span data-ttu-id="87938-114">Nepleťte si tento druh operace vlastní připojení s použitím více `from` klauzule pro přístup k vnitřních kolekcí.</span><span class="sxs-lookup"><span data-stu-id="87938-114">Don't confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="87938-115">Další informace najdete v tématu [klauzule join](../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="87938-115">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="87938-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="87938-116">Example</span></span>

<span data-ttu-id="87938-117">První metoda v následujícím příkladu ukazuje, jednoduché křížové spojení.</span><span class="sxs-lookup"><span data-stu-id="87938-117">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="87938-118">Křížové spojení musí používat opatrně, protože může vést k velmi velké množství výsledků.</span><span class="sxs-lookup"><span data-stu-id="87938-118">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="87938-119">Ale že může být užitečné v některých scénářích pro vytvoření zdrojových posloupností, u kterých jsou spuštěny další dotazy.</span><span class="sxs-lookup"><span data-stu-id="87938-119">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>

<span data-ttu-id="87938-120">Druhá metoda vytvoří posloupnost všech produktů, jejichž ID kategorie je uveden v seznamu kategorií na levé straně.</span><span class="sxs-lookup"><span data-stu-id="87938-120">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="87938-121">Všimněte si použití `let` klauzule a `Contains` metodu pro vytvoření dočasné pole.</span><span class="sxs-lookup"><span data-stu-id="87938-121">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="87938-122">Také je možné vytvořit pole před dotaz a předchází první `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="87938-122">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a><span data-ttu-id="87938-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="87938-123">Example</span></span>

<span data-ttu-id="87938-124">V následujícím příkladu musí dotaz spojení dvou sekvencí založené na přiřazování shodných klíčů, které v případě pořadí vnitřní (pravá strana), nelze získat před klauzuli spojení sama.</span><span class="sxs-lookup"><span data-stu-id="87938-124">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="87938-125">Pokud toto připojení se prováděly s `join` klauzule, pak bude `Split` metoda musel být volána pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="87938-125">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="87938-126">Použití více `from` umožňuje klauzule dotazu, aby režii volání opakované metody.</span><span class="sxs-lookup"><span data-stu-id="87938-126">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="87938-127">Nicméně od `join` optimalizuje, v tomto konkrétním případě může být rychlejší než při použití více `from` klauzule.</span><span class="sxs-lookup"><span data-stu-id="87938-127">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="87938-128">Výsledky se budou lišit v závislosti primárně na to, jak nákladné volání metody, které je.</span><span class="sxs-lookup"><span data-stu-id="87938-128">The results will vary depending primarily on how expensive the method call is.</span></span>

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a><span data-ttu-id="87938-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87938-129">See also</span></span>

- [<span data-ttu-id="87938-130">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="87938-130">Language Integrated Query (LINQ)</span></span>](index.md)  
- [<span data-ttu-id="87938-131">join – klauzule</span><span class="sxs-lookup"><span data-stu-id="87938-131">join clause</span></span>](../language-reference/keywords/join-clause.md)  
- [<span data-ttu-id="87938-132">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="87938-132">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)  
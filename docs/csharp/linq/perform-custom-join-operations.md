---
title: Provádění vlastních operací spojování
description: Postup provádění vlastních operací spojování.
ms.date: 12/1/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: df80f4382ad5fa96fcdc41b338cbb53a3d8e6cb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288519"
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="078a1-103">Provádění vlastních operací spojování</span><span class="sxs-lookup"><span data-stu-id="078a1-103">Perform custom join operations</span></span>

<span data-ttu-id="078a1-104">Tento příklad ukazuje, jak provádět operace spojení, které nejsou možné pomocí `join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="078a1-104">This example shows how to perform join operations that are not possible with the `join` clause.</span></span> <span data-ttu-id="078a1-105">Ve výrazu dotazu `join` klauzule je omezený na a optimalizováno pro equijoins, které jsou zdaleka nejběžnější typ operace spojení.</span><span class="sxs-lookup"><span data-stu-id="078a1-105">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="078a1-106">Při provádění porovnávání, bude pravděpodobně vždy získáte nejlepší výkon pomocí `join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="078a1-106">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>  
  
 <span data-ttu-id="078a1-107">Ale `join` klauzuli nelze použít v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="078a1-107">However, the `join` clause cannot be used in the following cases:</span></span>  
  
-   <span data-ttu-id="078a1-108">Když spojení záleží na výrazu nerovnosti (jiných porovnávání).</span><span class="sxs-lookup"><span data-stu-id="078a1-108">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>  
  
-   <span data-ttu-id="078a1-109">Když spojení záleží na více než jeden výraz rovnosti nebo nerovnosti.</span><span class="sxs-lookup"><span data-stu-id="078a1-109">When the join is predicated on more than one expression of equality or inequality.</span></span>  
  
-   <span data-ttu-id="078a1-110">Pokud máte zavést proměnnou rozsahu dočasný pro pořadí (vnitřní) na pravé straně před provedením operace spojení.</span><span class="sxs-lookup"><span data-stu-id="078a1-110">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>  
  
 <span data-ttu-id="078a1-111">Chcete-li provést spojení, které nejsou equijoins, můžete použít více `from` klauzule zavádět každý zdroj dat nezávisle.</span><span class="sxs-lookup"><span data-stu-id="078a1-111">To perform joins that are not equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="078a1-112">Potom použijte výraz predikátu v `where` klauzule pro proměnnou rozsahu pro každý zdroj.</span><span class="sxs-lookup"><span data-stu-id="078a1-112">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="078a1-113">Výraz také může mít formu volání metody.</span><span class="sxs-lookup"><span data-stu-id="078a1-113">The expression also can take the form of a method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="078a1-114">Nezaměňujte tento druh operace vlastní připojení s použitím více `from` klauzule pro přístup k vnitřní kolekce.</span><span class="sxs-lookup"><span data-stu-id="078a1-114">Do not confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="078a1-115">Další informace najdete v tématu [klauzuli join](../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="078a1-115">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="078a1-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="078a1-116">Example</span></span>  
 <span data-ttu-id="078a1-117">První metoda v následujícím příkladu ukazuje jednoduchý křížové spojení.</span><span class="sxs-lookup"><span data-stu-id="078a1-117">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="078a1-118">Křížové spojení musí používat opatrně, protože může vést k velmi velké množství výsledků.</span><span class="sxs-lookup"><span data-stu-id="078a1-118">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="078a1-119">Budou však může být užitečné v některých scénářích pro vytváření pořadí zdroje, kterými se spouštějí další dotazy.</span><span class="sxs-lookup"><span data-stu-id="078a1-119">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>  
  
 <span data-ttu-id="078a1-120">Druhý metoda vytváří posloupnost všechny produkty, jejichž kategorie ID je uvedena v seznamu kategorií na levé straně.</span><span class="sxs-lookup"><span data-stu-id="078a1-120">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="078a1-121">Všimněte si použití `let` klauzule a `Contains` metodu pro vytvoření dočasné pole.</span><span class="sxs-lookup"><span data-stu-id="078a1-121">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="078a1-122">Také je možné vytvořit pole před dotaz a odstranění první `from` klauzule.</span><span class="sxs-lookup"><span data-stu-id="078a1-122">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="078a1-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="078a1-123">Example</span></span>  
 <span data-ttu-id="078a1-124">V následujícím příkladu musí dotaz připojení dvě pořadí na základě shody klíče, které v případě pořadí vnitřní (vpravo), nelze získat před klauzuli join sám sebe.</span><span class="sxs-lookup"><span data-stu-id="078a1-124">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="078a1-125">Pokud toto připojení nebyly provedeny s `join` klauzule, pak se `Split` by pak bylo metoda volána pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="078a1-125">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="078a1-126">Použití více `from` klauzule umožňuje dotaz předejdete režií při volání metody opakovaných.</span><span class="sxs-lookup"><span data-stu-id="078a1-126">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="078a1-127">Ale protože `join` je optimalizovaná, v tomto případě může být rychlejší než při použití více `from` klauzule.</span><span class="sxs-lookup"><span data-stu-id="078a1-127">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="078a1-128">Výsledky se liší v závislosti především na tom, jak nákladné je volání metody.</span><span class="sxs-lookup"><span data-stu-id="078a1-128">The results will vary depending primarily on how expensive the method call is.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="078a1-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="078a1-129">See also</span></span>  
 [<span data-ttu-id="078a1-130">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="078a1-130">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="078a1-131">join – klauzule</span><span class="sxs-lookup"><span data-stu-id="078a1-131">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="078a1-132">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="078a1-132">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)

---
title: "Provádění vlastních operací spojování"
description: "Postup provádění vlastních operací spojování."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: fef146c92a5cbbf21f8f1688f221c2bd45c99de7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="8f1bc-104">Provádění vlastních operací spojování</span><span class="sxs-lookup"><span data-stu-id="8f1bc-104">Perform custom join operations</span></span>

<span data-ttu-id="8f1bc-105">Tento příklad ukazuje, jak provádět operace spojení, které nejsou možné pomocí `join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-105">This example shows how to perform join operations that are not possible with the `join` clause.</span></span> <span data-ttu-id="8f1bc-106">Ve výrazu dotazu `join` klauzule je omezený na a optimalizováno pro equijoins, které jsou zdaleka nejběžnější typ operace spojení.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-106">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="8f1bc-107">Při provádění porovnávání, bude pravděpodobně vždy získáte nejlepší výkon pomocí `join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-107">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>  
  
 <span data-ttu-id="8f1bc-108">Ale `join` klauzuli nelze použít v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="8f1bc-108">However, the `join` clause cannot be used in the following cases:</span></span>  
  
-   <span data-ttu-id="8f1bc-109">Když spojení záleží na výrazu nerovnosti (jiných porovnávání).</span><span class="sxs-lookup"><span data-stu-id="8f1bc-109">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>  
  
-   <span data-ttu-id="8f1bc-110">Když spojení záleží na více než jeden výraz rovnosti nebo nerovnosti.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-110">When the join is predicated on more than one expression of equality or inequality.</span></span>  
  
-   <span data-ttu-id="8f1bc-111">Pokud máte zavést proměnnou rozsahu dočasný pro pořadí (vnitřní) na pravé straně před provedením operace spojení.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-111">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>  
  
 <span data-ttu-id="8f1bc-112">Chcete-li provést spojení, které nejsou equijoins, můžete použít více `from` klauzule zavádět každý zdroj dat nezávisle.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-112">To perform joins that are not equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="8f1bc-113">Potom použijte výraz predikátu v `where` klauzule pro proměnnou rozsahu pro každý zdroj.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-113">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="8f1bc-114">Výraz také může mít formu volání metody.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-114">The expression also can take the form of a method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f1bc-115">Nezaměňujte tento druh operace vlastní připojení s použitím více `from` klauzule pro přístup k vnitřní kolekce.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-115">Do not confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="8f1bc-116">Další informace najdete v tématu [klauzuli join](../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8f1bc-116">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f1bc-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f1bc-117">Example</span></span>  
 <span data-ttu-id="8f1bc-118">První metoda v následujícím příkladu ukazuje jednoduchý křížové spojení.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-118">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="8f1bc-119">Křížové spojení musí používat opatrně, protože může vést k velmi velké množství výsledků.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-119">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="8f1bc-120">Budou však může být užitečné v některých scénářích pro vytváření pořadí zdroje, kterými se spouštějí další dotazy.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-120">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>  
  
 <span data-ttu-id="8f1bc-121">Druhý metoda vytváří posloupnost všechny produkty, jejichž kategorie ID je uvedena v seznamu kategorií na levé straně.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-121">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="8f1bc-122">Všimněte si použití `let` klauzule a `Contains` metodu pro vytvoření dočasné pole.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-122">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="8f1bc-123">Také je možné vytvořit pole před dotaz a odstranění první `from` klauzule.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-123">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8f1bc-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f1bc-124">Example</span></span>  
 <span data-ttu-id="8f1bc-125">V následujícím příkladu musí dotaz připojení dvě pořadí na základě shody klíče, které v případě pořadí vnitřní (vpravo), nelze získat před klauzuli join sám sebe.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-125">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="8f1bc-126">Pokud toto připojení nebyly provedeny s `join` klauzule, pak se `Split` by pak bylo metoda volána pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-126">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="8f1bc-127">Použití více `from` klauzule umožňuje dotaz předejdete režií při volání metody opakovaných.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-127">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="8f1bc-128">Ale protože `join` je optimalizovaná, v tomto případě může být rychlejší než při použití více `from` klauzule.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-128">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="8f1bc-129">Výsledky se liší v závislosti především na tom, jak nákladné je volání metody.</span><span class="sxs-lookup"><span data-stu-id="8f1bc-129">The results will vary depending primarily on how expensive the method call is.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8f1bc-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f1bc-130">See also</span></span>  
 [<span data-ttu-id="8f1bc-131">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="8f1bc-131">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="8f1bc-132">JOIN – klauzule</span><span class="sxs-lookup"><span data-stu-id="8f1bc-132">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="8f1bc-133">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="8f1bc-133">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)

---
title: Aggregate – klauzule (Visual Basic)
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: e3ce8ff7da647120e5fd9e3b4cd44cc603eb797d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519483"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="3e135-102">Aggregate – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e135-102">Aggregate Clause (Visual Basic)</span></span>
<span data-ttu-id="3e135-103">Použije jeden nebo více agregačních funkcí na kolekci.</span><span class="sxs-lookup"><span data-stu-id="3e135-103">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e135-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e135-104">Syntax</span></span>  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="3e135-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="3e135-105">Parts</span></span>  
  
|<span data-ttu-id="3e135-106">Termín</span><span class="sxs-lookup"><span data-stu-id="3e135-106">Term</span></span>|<span data-ttu-id="3e135-107">Definice</span><span class="sxs-lookup"><span data-stu-id="3e135-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="3e135-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="3e135-108">Required.</span></span> <span data-ttu-id="3e135-109">Proměnné použité k iteraci v rámci elementů kolekce.</span><span class="sxs-lookup"><span data-stu-id="3e135-109">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="3e135-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3e135-110">Optional.</span></span> <span data-ttu-id="3e135-111">Typ `element`.</span><span class="sxs-lookup"><span data-stu-id="3e135-111">The type of `element`.</span></span> <span data-ttu-id="3e135-112">Pokud není zadán žádný typ. typ `element` je odvozen z `collection`.</span><span class="sxs-lookup"><span data-stu-id="3e135-112">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="3e135-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="3e135-113">Required.</span></span> <span data-ttu-id="3e135-114">Odkazuje na kolekci, které se má operace provést.</span><span class="sxs-lookup"><span data-stu-id="3e135-114">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="3e135-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3e135-115">Optional.</span></span> <span data-ttu-id="3e135-116">Jeden nebo více klauzulemi dotazu, například `Where` klauzule, pro upřesnění výsledků dotazu použití klauzule aggregate nebo klauzule.</span><span class="sxs-lookup"><span data-stu-id="3e135-116">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="3e135-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="3e135-117">Required.</span></span> <span data-ttu-id="3e135-118">Jeden nebo více oddělených čárkou výrazů, které identifikují agregační funkce má být použita ke kolekci.</span><span class="sxs-lookup"><span data-stu-id="3e135-118">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="3e135-119">Agregační funkce k určení názvu členu výsledku dotazu, můžete použít jako alias.</span><span class="sxs-lookup"><span data-stu-id="3e135-119">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="3e135-120">Pokud žádný alias je zadaný, použije se název agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="3e135-120">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="3e135-121">Příklady najdete v části o agregačních funkcích dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="3e135-121">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e135-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e135-122">Remarks</span></span>  
 <span data-ttu-id="3e135-123">`Aggregate` Klauzule je možné zahrnout agregačních funkcí v dotazech.</span><span class="sxs-lookup"><span data-stu-id="3e135-123">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="3e135-124">Agregační funkce provádět kontroly a výpočty v rámci sady hodnoty a vrátí jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3e135-124">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="3e135-125">Vypočítaná hodnota můžete přistupovat pomocí členem typ výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="3e135-125">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="3e135-126">Jsou standardní agregační funkce, které můžete použít `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, a `Sum` funkce.</span><span class="sxs-lookup"><span data-stu-id="3e135-126">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="3e135-127">Tyto funkce jsou zkušenosti vývojáře, kteří znají agregace v SQL.</span><span class="sxs-lookup"><span data-stu-id="3e135-127">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="3e135-128">Jsou popsány v následující části tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3e135-128">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="3e135-129">Výsledek agregační funkce je zahrnutá ve výsledku dotazu. jako pole s typem výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="3e135-129">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="3e135-130">Můžete zadat jako alias pro výsledek agregační funkce k zadání názvu členem typu výsledku dotazu, která bude obsahovat agregovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3e135-130">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="3e135-131">Pokud žádný alias je zadaný, použije se název agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="3e135-131">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="3e135-132">`Aggregate` Začít klauzule dotazu, nebo může být zahrnut jako další klauzule v dotazu.</span><span class="sxs-lookup"><span data-stu-id="3e135-132">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="3e135-133">Pokud `Aggregate` začíná klauzulí dotazu, výsledkem je jediná hodnota, která je výsledkem zadanou v agregační funkci `Into` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3e135-133">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="3e135-134">Pokud je zadán více než jeden agregační funkci v `Into` klauzule, dotaz vrátí jeden typ s samostatné vlastností odkazují na výsledek každého agregační funkce `Into` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3e135-134">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="3e135-135">Pokud `Aggregate` klauzule je dostupná jako další klauzule dotazu, typ vrácený v kolekci dotazu bude mít samostatné vlastnosti a odkazují na výsledek každého agregační funkce `Into` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3e135-135">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="3e135-136">Agregační funkce</span><span class="sxs-lookup"><span data-stu-id="3e135-136">Aggregate Functions</span></span>

<span data-ttu-id="3e135-137">Toto jsou standardní agregační funkce, které lze použít s `Aggregate` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3e135-137">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="3e135-138">Všechny</span><span class="sxs-lookup"><span data-stu-id="3e135-138">All</span></span>

<span data-ttu-id="3e135-139">Vrátí `true` Pokud všechny prvky v kolekci splňují zadanou podmínku; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="3e135-139">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="3e135-140">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="3e135-140">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]

### <a name="any"></a><span data-ttu-id="3e135-141">Všechny</span><span class="sxs-lookup"><span data-stu-id="3e135-141">Any</span></span>

<span data-ttu-id="3e135-142">Vrátí `true` Pokud libovolný prvek v kolekci splňuje zadanou podmínku; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="3e135-142">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="3e135-143">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="3e135-143">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]

### <a name="average"></a><span data-ttu-id="3e135-144">Průměr</span><span class="sxs-lookup"><span data-stu-id="3e135-144">Average</span></span>

<span data-ttu-id="3e135-145">Vypočítá průměr všech prvků v kolekci nebo vypočítá zadaný výraz pro všechny elementy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="3e135-145">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="3e135-146">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="3e135-146">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]

### <a name="count"></a><span data-ttu-id="3e135-147">Počet</span><span class="sxs-lookup"><span data-stu-id="3e135-147">Count</span></span>

<span data-ttu-id="3e135-148">Vrátí počet prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="3e135-148">Counts the number of elements in the collection.</span></span> <span data-ttu-id="3e135-149">Můžete zadat volitelný `Boolean` výraz ke zjištění počtu prvků v kolekci, které splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="3e135-149">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="3e135-150">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="3e135-150">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]

### <a name="group"></a><span data-ttu-id="3e135-151">Skupina</span><span class="sxs-lookup"><span data-stu-id="3e135-151">Group</span></span>

<span data-ttu-id="3e135-152">Odkazuje na výsledky dotazu, které jsou seskupeny kvůli `Group By` nebo `Group Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3e135-152">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="3e135-153">`Group` Funkce je platná pouze v `Into` klauzuli `Group By` nebo `Group Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3e135-153">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="3e135-154">Další informace a příklady najdete v tématu [klauzule Group](../../../visual-basic/language-reference/queries/group-by-clause.md) a [Group Join – klauzule](../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="3e135-154">For more information and examples, see [Group By Clause](../../../visual-basic/language-reference/queries/group-by-clause.md) and [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="3e135-155">LongCount</span><span class="sxs-lookup"><span data-stu-id="3e135-155">LongCount</span></span>

<span data-ttu-id="3e135-156">Vrátí počet prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="3e135-156">Counts the number of elements in the collection.</span></span> <span data-ttu-id="3e135-157">Můžete zadat volitelný `Boolean` výraz ke zjištění počtu prvků v kolekci, které splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="3e135-157">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="3e135-158">Vrátí výsledek jako `Long`.</span><span class="sxs-lookup"><span data-stu-id="3e135-158">Returns the result as a `Long`.</span></span> <span data-ttu-id="3e135-159">Příklad najdete v tématu `Count` agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="3e135-159">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="3e135-160">maximální počet</span><span class="sxs-lookup"><span data-stu-id="3e135-160">Max</span></span>

<span data-ttu-id="3e135-161">Vypočítá maximální hodnotu z kolekce nebo vypočítá zadaný výraz pro všechny elementy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="3e135-161">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="3e135-162">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="3e135-162">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]

### <a name="min"></a><span data-ttu-id="3e135-163">min</span><span class="sxs-lookup"><span data-stu-id="3e135-163">Min</span></span>

<span data-ttu-id="3e135-164">Vypočítá minimální hodnotu z kolekce nebo vypočítá zadaný výraz pro všechny elementy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="3e135-164">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="3e135-165">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="3e135-165">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]

### <a name="sum"></a><span data-ttu-id="3e135-166">Součet</span><span class="sxs-lookup"><span data-stu-id="3e135-166">Sum</span></span>

<span data-ttu-id="3e135-167">Vypočítá součet všech prvků v kolekci nebo vypočítá zadaný výraz pro všechny elementy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="3e135-167">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="3e135-168">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="3e135-168">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]

## <a name="example"></a><span data-ttu-id="3e135-169">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e135-169">Example</span></span>  

<span data-ttu-id="3e135-170">Následující příklad ukazuje způsob použití `Aggregate` klauzule k aplikaci agregačních funkcí na výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="3e135-170">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="3e135-171">Vytvoření uživatelsky definované agregační funkce</span><span class="sxs-lookup"><span data-stu-id="3e135-171">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="3e135-172">Přidáním rozšiřující metody, které můžete zahrnout vlastní agregační funkce ve výrazu dotazu <xref:System.Collections.Generic.IEnumerable%601> typu.</span><span class="sxs-lookup"><span data-stu-id="3e135-172">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="3e135-173">Vlastní metoda pak můžete provádět operaci vyčíslitelné kolekce, která je popsána agregační funkce nebo výpočtu.</span><span class="sxs-lookup"><span data-stu-id="3e135-173">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="3e135-174">Další informace o metodách rozšíření naleznete v tématu [rozšiřující metody](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="3e135-174">For more information about extension methods, see [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="3e135-175">Například následující příklad ukazuje vlastní agregační funkce, která vypočítá Medián kolekci čísel.</span><span class="sxs-lookup"><span data-stu-id="3e135-175">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="3e135-176">Existují dvě přetížení `Median` – metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3e135-176">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="3e135-177">První přetížení přijímá jako vstup, kolekci typu `IEnumerable(Of Double)`.</span><span class="sxs-lookup"><span data-stu-id="3e135-177">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="3e135-178">Pokud `Median` agregační funkce se volá pro pole dotazu s typem `Double`, tato metoda bude volána.</span><span class="sxs-lookup"><span data-stu-id="3e135-178">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="3e135-179">Druhé přetížení `Median` metody mohou být předány žádné obecného typu.</span><span class="sxs-lookup"><span data-stu-id="3e135-179">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="3e135-180">Obecné přetížení `Median` metoda přijímá druhý parametr, který odkazuje `Func(Of T, Double)` výraz lambda definoval se projekt hodnota pro typ (z kolekce) jako odpovídající hodnotu typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="3e135-180">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="3e135-181">Potom postoupí výpočtu střední hodnotu do jiné přetížení `Median` metody.</span><span class="sxs-lookup"><span data-stu-id="3e135-181">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="3e135-182">Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3e135-182">For more information about lambda expressions, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 <span data-ttu-id="3e135-183">Následující příklad ukazuje ukázkové dotazy, které volají `Median` agregační funkce na kolekci typu `Integer`a kolekce typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="3e135-183">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="3e135-184">Dotaz, který volá `Median` agregační funkce na kolekci typu `Double` volá přetížení `Median` metody, která přijímá jako vstup, kolekci typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="3e135-184">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="3e135-185">Dotaz, který volá `Median` agregační funkce na kolekci typu `Integer` volá obecné přetížení `Median` metody.</span><span class="sxs-lookup"><span data-stu-id="3e135-185">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3e135-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e135-186">See Also</span></span>

- [<span data-ttu-id="3e135-187">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e135-187">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
- [<span data-ttu-id="3e135-188">Dotazy</span><span class="sxs-lookup"><span data-stu-id="3e135-188">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
- [<span data-ttu-id="3e135-189">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="3e135-189">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
- [<span data-ttu-id="3e135-190">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="3e135-190">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
- [<span data-ttu-id="3e135-191">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="3e135-191">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
- [<span data-ttu-id="3e135-192">Klauzule Group By</span><span class="sxs-lookup"><span data-stu-id="3e135-192">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)

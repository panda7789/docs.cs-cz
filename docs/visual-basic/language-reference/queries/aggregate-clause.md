---
title: Aggregate – klauzule
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
ms.openlocfilehash: 326c3306368ceca2122e912556efd84e4bfef1f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412998"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="20f37-102">Aggregate – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20f37-102">Aggregate Clause (Visual Basic)</span></span>
<span data-ttu-id="20f37-103">Aplikuje jednu nebo více agregačních funkcí na kolekci.</span><span class="sxs-lookup"><span data-stu-id="20f37-103">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20f37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20f37-104">Syntax</span></span>  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="20f37-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="20f37-105">Parts</span></span>  
  
|<span data-ttu-id="20f37-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="20f37-106">Term</span></span>|<span data-ttu-id="20f37-107">Definice</span><span class="sxs-lookup"><span data-stu-id="20f37-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="20f37-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="20f37-108">Required.</span></span> <span data-ttu-id="20f37-109">Proměnná použitá pro iteraci prvků kolekce.</span><span class="sxs-lookup"><span data-stu-id="20f37-109">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="20f37-110">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="20f37-110">Optional.</span></span> <span data-ttu-id="20f37-111">Typ `element` .</span><span class="sxs-lookup"><span data-stu-id="20f37-111">The type of `element`.</span></span> <span data-ttu-id="20f37-112">Pokud není zadán žádný typ, typ `element` je odvozen z `collection` .</span><span class="sxs-lookup"><span data-stu-id="20f37-112">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="20f37-113">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="20f37-113">Required.</span></span> <span data-ttu-id="20f37-114">Odkazuje na kolekci, na které se má pracovat.</span><span class="sxs-lookup"><span data-stu-id="20f37-114">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="20f37-115">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="20f37-115">Optional.</span></span> <span data-ttu-id="20f37-116">Jedna nebo více klauzulí dotazu, jako je například `Where` klauzule, pro upřesnění výsledku dotazu pro použití agregační klauzule nebo klauzule na.</span><span class="sxs-lookup"><span data-stu-id="20f37-116">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="20f37-117">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="20f37-117">Required.</span></span> <span data-ttu-id="20f37-118">Jeden nebo více výrazů oddělených čárkami, které identifikují agregační funkci, která se má použít pro kolekci.</span><span class="sxs-lookup"><span data-stu-id="20f37-118">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="20f37-119">Můžete použít alias pro agregační funkci a zadat název člena pro výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="20f37-119">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="20f37-120">Pokud není zadán žádný alias, je použit název agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="20f37-120">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="20f37-121">Příklady najdete v části o agregačních funkcích dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="20f37-121">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20f37-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20f37-122">Remarks</span></span>  
 <span data-ttu-id="20f37-123">`Aggregate`Klauzuli lze použít k zahrnutí agregačních funkcí do dotazů.</span><span class="sxs-lookup"><span data-stu-id="20f37-123">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="20f37-124">Agregační funkce provádějí kontroly a výpočty přes sadu hodnot a vracejí jedinou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="20f37-124">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="20f37-125">K vypočtené hodnotě můžete přistupovat pomocí členu typu výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="20f37-125">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="20f37-126">Standardní agregační funkce, které lze použít, jsou `All` funkce, `Any` , `Average` , `Count` , `LongCount` , `Max` , `Min` a `Sum` .</span><span class="sxs-lookup"><span data-stu-id="20f37-126">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="20f37-127">Tyto funkce jsou známé vývojářům, kteří jsou obeznámeni s agregacemi v SQL.</span><span class="sxs-lookup"><span data-stu-id="20f37-127">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="20f37-128">Jsou popsány v následující části tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="20f37-128">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="20f37-129">Výsledek agregační funkce je zahrnut ve výsledku dotazu jako pole typu výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="20f37-129">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="20f37-130">Můžete zadat alias pro výsledek agregační funkce pro určení názvu člena typu výsledku dotazu, který bude obsahovat agregovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="20f37-130">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="20f37-131">Pokud není zadán žádný alias, je použit název agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="20f37-131">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="20f37-132">`Aggregate`Klauzule může spustit dotaz nebo může být obsažena jako další klauzule v dotazu.</span><span class="sxs-lookup"><span data-stu-id="20f37-132">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="20f37-133">Pokud `Aggregate` klauzule zahájí dotaz, výsledkem je jediná hodnota, která je výsledkem agregační funkce zadané v `Into` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="20f37-133">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="20f37-134">Je-li v klauzuli zadána více než jedna agregační funkce `Into` , dotaz vrátí jeden typ s samostatnou vlastností, aby odkazoval na výsledek každé agregační funkce v `Into` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="20f37-134">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="20f37-135">Pokud `Aggregate` je klauzule obsažena v dotazu jako další klauzule, typ vrácený v kolekci dotazů bude mít samostatnou vlastnost, která bude odkazovat na výsledek každé agregační funkce v `Into` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="20f37-135">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="20f37-136">Agregační funkce</span><span class="sxs-lookup"><span data-stu-id="20f37-136">Aggregate Functions</span></span>

<span data-ttu-id="20f37-137">Níže jsou uvedené standardní agregační funkce, které lze použít s `Aggregate` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="20f37-137">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="20f37-138">Vše</span><span class="sxs-lookup"><span data-stu-id="20f37-138">All</span></span>

<span data-ttu-id="20f37-139">Vrátí, `true` zda všechny prvky v kolekci odpovídají zadané podmínce. v opačném případě vrátí `false` .</span><span class="sxs-lookup"><span data-stu-id="20f37-139">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="20f37-140">Například:</span><span class="sxs-lookup"><span data-stu-id="20f37-140">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="20f37-141">Všechny</span><span class="sxs-lookup"><span data-stu-id="20f37-141">Any</span></span>

<span data-ttu-id="20f37-142">Vrátí `true` , zda kterýkoli prvek v kolekci splňuje zadanou podmínku. v opačném případě vrátí `false` .</span><span class="sxs-lookup"><span data-stu-id="20f37-142">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="20f37-143">Například:</span><span class="sxs-lookup"><span data-stu-id="20f37-143">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="20f37-144">Průměr</span><span class="sxs-lookup"><span data-stu-id="20f37-144">Average</span></span>

<span data-ttu-id="20f37-145">Vypočítá průměr všech prvků v kolekci nebo vypočítá zadaný výraz pro všechny prvky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="20f37-145">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="20f37-146">Například:</span><span class="sxs-lookup"><span data-stu-id="20f37-146">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="20f37-147">Počet</span><span class="sxs-lookup"><span data-stu-id="20f37-147">Count</span></span>

<span data-ttu-id="20f37-148">Spočítá počet prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="20f37-148">Counts the number of elements in the collection.</span></span> <span data-ttu-id="20f37-149">Můžete zadat volitelný výraz, který bude `Boolean` počítat pouze počet prvků v kolekci, které splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="20f37-149">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="20f37-150">Například:</span><span class="sxs-lookup"><span data-stu-id="20f37-150">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="20f37-151">Skupina</span><span class="sxs-lookup"><span data-stu-id="20f37-151">Group</span></span>

<span data-ttu-id="20f37-152">Odkazuje na výsledky dotazu, které jsou seskupeny jako výsledek `Group By` klauzule OR `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="20f37-152">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="20f37-153">`Group`Funkce je platná pouze v `Into` klauzuli `Group By` `Group Join` klauzule OR.</span><span class="sxs-lookup"><span data-stu-id="20f37-153">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="20f37-154">Další informace a příklady najdete v tématu [klauzule GROUP by](group-by-clause.md) a [Group Join](group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="20f37-154">For more information and examples, see [Group By Clause](group-by-clause.md) and [Group Join Clause](group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="20f37-155">LongCount</span><span class="sxs-lookup"><span data-stu-id="20f37-155">LongCount</span></span>

<span data-ttu-id="20f37-156">Spočítá počet prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="20f37-156">Counts the number of elements in the collection.</span></span> <span data-ttu-id="20f37-157">Můžete zadat volitelný výraz, který bude `Boolean` počítat pouze počet prvků v kolekci, které splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="20f37-157">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="20f37-158">Vrátí výsledek jako `Long` .</span><span class="sxs-lookup"><span data-stu-id="20f37-158">Returns the result as a `Long`.</span></span> <span data-ttu-id="20f37-159">Příklad naleznete v `Count` agregační funkci.</span><span class="sxs-lookup"><span data-stu-id="20f37-159">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="20f37-160">Maximum</span><span class="sxs-lookup"><span data-stu-id="20f37-160">Max</span></span>

<span data-ttu-id="20f37-161">Vypočítá maximální hodnotu z kolekce nebo vypočítá zadaný výraz pro všechny prvky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="20f37-161">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="20f37-162">Například:</span><span class="sxs-lookup"><span data-stu-id="20f37-162">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="20f37-163">Minimum</span><span class="sxs-lookup"><span data-stu-id="20f37-163">Min</span></span>

<span data-ttu-id="20f37-164">Vypočítá minimální hodnotu z kolekce nebo vypočítá zadaný výraz pro všechny prvky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="20f37-164">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="20f37-165">Například:</span><span class="sxs-lookup"><span data-stu-id="20f37-165">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="20f37-166">Součet</span><span class="sxs-lookup"><span data-stu-id="20f37-166">Sum</span></span>

<span data-ttu-id="20f37-167">Vypočítá součet všech prvků v kolekci nebo vypočítá zadaný výraz pro všechny prvky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="20f37-167">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="20f37-168">Například:</span><span class="sxs-lookup"><span data-stu-id="20f37-168">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="20f37-169">Příklad</span><span class="sxs-lookup"><span data-stu-id="20f37-169">Example</span></span>  

<span data-ttu-id="20f37-170">Následující příklad ukazuje, jak použít `Aggregate` klauzuli pro použití agregačních funkcí pro výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="20f37-170">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="20f37-171">Vytváření agregačních funkcí definovaných uživatelem</span><span class="sxs-lookup"><span data-stu-id="20f37-171">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="20f37-172">Do výrazu dotazu můžete přidat vlastní agregační funkce přidáním rozšiřujících metod do <xref:System.Collections.Generic.IEnumerable%601> typu.</span><span class="sxs-lookup"><span data-stu-id="20f37-172">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="20f37-173">Vaše vlastní metoda potom může provést výpočet nebo operaci na vyčíslitelné kolekci, která odkazovala na agregační funkci.</span><span class="sxs-lookup"><span data-stu-id="20f37-173">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="20f37-174">Další informace o metodách rozšíření naleznete v tématu [metody rozšíření](../../programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="20f37-174">For more information about extension methods, see [Extension Methods](../../programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="20f37-175">Například následující příklad ukazuje vlastní agregační funkci, která vypočítá medián hodnoty kolekce čísel.</span><span class="sxs-lookup"><span data-stu-id="20f37-175">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="20f37-176">Existují dvě přetížení `Median` metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="20f37-176">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="20f37-177">První přetížení akceptuje jako vstup kolekci typu `IEnumerable(Of Double)` .</span><span class="sxs-lookup"><span data-stu-id="20f37-177">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="20f37-178">Pokud `Median` je agregační funkce volána pro pole dotazu typu `Double` , bude tato metoda volána.</span><span class="sxs-lookup"><span data-stu-id="20f37-178">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="20f37-179">Druhé přetížení `Median` metody může být předáno libovolným obecným typem.</span><span class="sxs-lookup"><span data-stu-id="20f37-179">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="20f37-180">Obecné přetížení `Median` metody přebírá druhý parametr, který odkazuje na `Func(Of T, Double)` výraz lambda, aby prokáže hodnotu pro typ (z kolekce) jako odpovídající hodnotu typu `Double` .</span><span class="sxs-lookup"><span data-stu-id="20f37-180">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="20f37-181">Poté deleguje výpočet střední hodnoty k druhé přetížení `Median` metody.</span><span class="sxs-lookup"><span data-stu-id="20f37-181">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="20f37-182">Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="20f37-182">For more information about lambda expressions, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="20f37-183">Následující příklad ukazuje Ukázkové dotazy, které volají `Median` agregační funkci na kolekci typu `Integer` a kolekci typu `Double` .</span><span class="sxs-lookup"><span data-stu-id="20f37-183">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="20f37-184">Dotaz, který volá `Median` agregační funkci na kolekci typu `Double` volá přetížení `Median` metody, která přijímá jako vstup, kolekci typu `Double` .</span><span class="sxs-lookup"><span data-stu-id="20f37-184">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="20f37-185">Dotaz, který volá `Median` agregační funkci na kolekci typu, `Integer` volá obecné přetížení `Median` metody.</span><span class="sxs-lookup"><span data-stu-id="20f37-185">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="20f37-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="20f37-186">See also</span></span>

- [<span data-ttu-id="20f37-187">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20f37-187">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="20f37-188">Dotazy</span><span class="sxs-lookup"><span data-stu-id="20f37-188">Queries</span></span>](index.md)
- [<span data-ttu-id="20f37-189">Klauzule SELECT</span><span class="sxs-lookup"><span data-stu-id="20f37-189">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="20f37-190">Klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="20f37-190">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="20f37-191">Klauzule WHERE</span><span class="sxs-lookup"><span data-stu-id="20f37-191">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="20f37-192">Group By – klauzule</span><span class="sxs-lookup"><span data-stu-id="20f37-192">Group By Clause</span></span>](group-by-clause.md)

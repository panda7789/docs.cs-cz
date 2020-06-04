---
title: From – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 33680f49247b3b2a6082b3a6b27ca64f8401e42d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396178"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="e2ab8-102">From – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2ab8-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="e2ab8-103">Určuje jednu nebo více proměnných rozsahu a kolekci pro dotaz.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2ab8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2ab8-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="e2ab8-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e2ab8-105">Parts</span></span>  
  
|<span data-ttu-id="e2ab8-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="e2ab8-106">Term</span></span>|<span data-ttu-id="e2ab8-107">Definice</span><span class="sxs-lookup"><span data-stu-id="e2ab8-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="e2ab8-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-108">Required.</span></span> <span data-ttu-id="e2ab8-109">*Proměnná rozsahu* používaná k iterování prostřednictvím prvků kolekce.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="e2ab8-110">Proměnná rozsahu se používá pro odkazování na každého člena v, `collection` protože dotaz prochází pomocí `collection` .</span><span class="sxs-lookup"><span data-stu-id="e2ab8-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="e2ab8-111">Musí se jednat o vyčíslitelného typu.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="e2ab8-112">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-112">Optional.</span></span> <span data-ttu-id="e2ab8-113">Typ `element` .</span><span class="sxs-lookup"><span data-stu-id="e2ab8-113">The type of `element`.</span></span> <span data-ttu-id="e2ab8-114">Pokud `type` není zadán, typ `element` je odvozen z `collection` .</span><span class="sxs-lookup"><span data-stu-id="e2ab8-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="e2ab8-115">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-115">Required.</span></span> <span data-ttu-id="e2ab8-116">Odkazuje na kolekci, do které se má dotazovat.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="e2ab8-117">Musí se jednat o vyčíslitelného typu.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2ab8-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2ab8-118">Remarks</span></span>  
 <span data-ttu-id="e2ab8-119">`From`Klauzule slouží k identifikaci zdrojových dat pro dotaz a proměnné, které se používají k odkazování na element ze zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="e2ab8-120">Tyto proměnné se nazývají *proměnné rozsahu*.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-120">These variables are called *range variables*.</span></span> <span data-ttu-id="e2ab8-121">`From`Klauzule je vyžadována pro dotaz s výjimkou případů, kdy `Aggregate` je použita klauzule k identifikaci dotazu, který vrací pouze agregované výsledky.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="e2ab8-122">Další informace naleznete v tématu [klauzule Aggregate](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e2ab8-122">For more information, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="e2ab8-123">V dotazu můžete zadat více `From` klauzulí k identifikaci více kolekcí, které mají být spojeny.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="e2ab8-124">Pokud je zadáno více kolekcí, jsou iterované na nezávisle, nebo se k nim můžete připojit, pokud jsou v relaci.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="e2ab8-125">Kolekce můžete spojit implicitně pomocí `Select` klauzule nebo explicitně pomocí `Join` `Group Join` klauzulí or.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="e2ab8-126">Alternativně můžete zadat více proměnných rozsahu a kolekcí v rámci jedné `From` klauzule, přičemž každá související proměnná rozsahu a kolekce je oddělená od ostatních o čárku.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="e2ab8-127">Následující příklad kódu ukazuje obě možnosti syntaxe `From` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="e2ab8-128">`From`Klauzule definuje rozsah dotazu, který je podobný oboru `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="e2ab8-129">Proto musí každá `element` Proměnná rozsahu v oboru dotazu mít jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="e2ab8-130">Vzhledem k tomu, že lze zadat více `From` klauzulí pro dotaz, následné `From` klauzule mohou odkazovat na proměnné rozsahu v `From` klauzuli nebo mohou odkazovat na proměnné rozsahu v předchozí `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="e2ab8-131">Například následující příklad ukazuje vnořenou `From` klauzuli, kde kolekce v druhé klauzuli je založena na vlastnosti proměnné rozsahu v první klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="e2ab8-132">`From`U každé klauzule může následovat jakákoli kombinace dalších klauzulí dotazu pro upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="e2ab8-133">Dotaz můžete upřesnit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="e2ab8-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="e2ab8-134">Použijte implicitně kombinaci více kolekcí pomocí `From` klauzulí a `Select` nebo explicitně pomocí `Join` `Group Join` klauzulí or.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="e2ab8-135">Pomocí `Where` klauzule můžete filtrovat výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="e2ab8-136">Seřaďte výsledek pomocí `Order By` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="e2ab8-137">Seskupte podobné výsledky společně pomocí `Group By` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="e2ab8-138">Použijte `Aggregate` klauzuli k identifikaci agregačních funkcí pro vyhodnocení celého výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="e2ab8-139">Použijte `Let` klauzuli pro představení proměnné iterace, jejíž hodnota je určena výrazem namísto kolekce.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="e2ab8-140">Použijte `Distinct` klauzuli pro ignorování duplicitních výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="e2ab8-141">Identifikujte části výsledku, které mají být vráceny pomocí `Skip` `Take` klauzulí,, `Skip While` a `Take While` .</span><span class="sxs-lookup"><span data-stu-id="e2ab8-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2ab8-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2ab8-142">Example</span></span>  
 <span data-ttu-id="e2ab8-143">Následující výraz dotazu používá `From` klauzuli pro deklaraci proměnné rozsahu `cust` pro každý `Customer` objekt v `customers` kolekci.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="e2ab8-144">`Where`Klauzule používá proměnnou rozsahu k omezení výstupu na zákazníky ze zadané oblasti.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="e2ab8-145">`For Each`Smyčka zobrazí název společnosti pro každého zákazníka ve výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="e2ab8-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="e2ab8-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2ab8-146">See also</span></span>

- [<span data-ttu-id="e2ab8-147">Dotazy</span><span class="sxs-lookup"><span data-stu-id="e2ab8-147">Queries</span></span>](index.md)
- [<span data-ttu-id="e2ab8-148">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2ab8-148">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="e2ab8-149">For Each...Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="e2ab8-149">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="e2ab8-150">For...Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="e2ab8-150">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="e2ab8-151">Klauzule SELECT</span><span class="sxs-lookup"><span data-stu-id="e2ab8-151">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="e2ab8-152">Klauzule WHERE</span><span class="sxs-lookup"><span data-stu-id="e2ab8-152">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="e2ab8-153">Aggregate – klauzule</span><span class="sxs-lookup"><span data-stu-id="e2ab8-153">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="e2ab8-154">Distinct – klauzule</span><span class="sxs-lookup"><span data-stu-id="e2ab8-154">Distinct Clause</span></span>](distinct-clause.md)
- [<span data-ttu-id="e2ab8-155">Klauzule JOIN</span><span class="sxs-lookup"><span data-stu-id="e2ab8-155">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="e2ab8-156">Group Join – klauzule</span><span class="sxs-lookup"><span data-stu-id="e2ab8-156">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="e2ab8-157">Order By – klauzule</span><span class="sxs-lookup"><span data-stu-id="e2ab8-157">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="e2ab8-158">Let – klauzule</span><span class="sxs-lookup"><span data-stu-id="e2ab8-158">Let Clause</span></span>](let-clause.md)
- [<span data-ttu-id="e2ab8-159">Skip – klauzule</span><span class="sxs-lookup"><span data-stu-id="e2ab8-159">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="e2ab8-160">Take – klauzule</span><span class="sxs-lookup"><span data-stu-id="e2ab8-160">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="e2ab8-161">Skip While – klauzule</span><span class="sxs-lookup"><span data-stu-id="e2ab8-161">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="e2ab8-162">Take While – klauzule</span><span class="sxs-lookup"><span data-stu-id="e2ab8-162">Take While Clause</span></span>](take-while-clause.md)

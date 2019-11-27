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
ms.openlocfilehash: a63fb41fc2b0ad885acf76ad5d56e446922f5b90
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343782"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="ee969-102">From – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee969-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="ee969-103">Určuje jednu nebo více proměnných rozsahu a kolekci pro dotaz.</span><span class="sxs-lookup"><span data-stu-id="ee969-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee969-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee969-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="ee969-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ee969-105">Parts</span></span>  
  
|<span data-ttu-id="ee969-106">Termín</span><span class="sxs-lookup"><span data-stu-id="ee969-106">Term</span></span>|<span data-ttu-id="ee969-107">Definice</span><span class="sxs-lookup"><span data-stu-id="ee969-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="ee969-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ee969-108">Required.</span></span> <span data-ttu-id="ee969-109">*Proměnná rozsahu* používaná k iterování prostřednictvím prvků kolekce.</span><span class="sxs-lookup"><span data-stu-id="ee969-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="ee969-110">Proměnná rozsahu se používá pro odkazování na každého člena `collection`, protože dotaz prochází `collection`.</span><span class="sxs-lookup"><span data-stu-id="ee969-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="ee969-111">Musí se jednat o vyčíslitelného typu.</span><span class="sxs-lookup"><span data-stu-id="ee969-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="ee969-112">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="ee969-112">Optional.</span></span> <span data-ttu-id="ee969-113">Typ připojení `element`.</span><span class="sxs-lookup"><span data-stu-id="ee969-113">The type of `element`.</span></span> <span data-ttu-id="ee969-114">Pokud není zadán žádný `type`, typ `element` je odvozen z `collection`.</span><span class="sxs-lookup"><span data-stu-id="ee969-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="ee969-115">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ee969-115">Required.</span></span> <span data-ttu-id="ee969-116">Odkazuje na kolekci, do které se má dotazovat.</span><span class="sxs-lookup"><span data-stu-id="ee969-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="ee969-117">Musí se jednat o vyčíslitelného typu.</span><span class="sxs-lookup"><span data-stu-id="ee969-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee969-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee969-118">Remarks</span></span>  
 <span data-ttu-id="ee969-119">Klauzule `From` slouží k identifikaci zdrojových dat pro dotaz a proměnné, které se používají k odkazování na prvek ze zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="ee969-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="ee969-120">Tyto proměnné se nazývají *proměnné rozsahu*.</span><span class="sxs-lookup"><span data-stu-id="ee969-120">These variables are called *range variables*.</span></span> <span data-ttu-id="ee969-121">Klauzule `From` je vyžadována pro dotaz s výjimkou případů, kdy je použita klauzule `Aggregate` k identifikaci dotazu, který vrací pouze agregované výsledky.</span><span class="sxs-lookup"><span data-stu-id="ee969-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="ee969-122">Další informace naleznete v tématu [klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ee969-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="ee969-123">V dotazu můžete zadat více klauzulí `From` pro identifikaci více kolekcí, které mají být spojeny.</span><span class="sxs-lookup"><span data-stu-id="ee969-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="ee969-124">Pokud je zadáno více kolekcí, jsou iterované na nezávisle, nebo se k nim můžete připojit, pokud jsou v relaci.</span><span class="sxs-lookup"><span data-stu-id="ee969-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="ee969-125">Kolekce můžete spojit implicitně pomocí klauzule `Select`, nebo explicitně pomocí klauzule `Join` nebo `Group Join`.</span><span class="sxs-lookup"><span data-stu-id="ee969-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="ee969-126">Alternativně můžete zadat více proměnných rozsahu a kolekcí v rámci jedné klauzule `From`, přičemž každou související proměnnou rozsahu a kolekci od sebe budou oddělené čárkou.</span><span class="sxs-lookup"><span data-stu-id="ee969-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="ee969-127">Následující příklad kódu ukazuje obě možnosti syntaxe pro klauzuli `From`.</span><span class="sxs-lookup"><span data-stu-id="ee969-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="ee969-128">Klauzule `From` definuje rozsah dotazu, který je podobný rozsahu `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="ee969-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="ee969-129">Proto musí každá proměnná rozsahu `element` v oboru dotazu mít jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="ee969-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="ee969-130">Vzhledem k tomu, že lze zadat více klauzulí `From` pro dotaz, následné `From` klauzule mohou odkazovat na proměnné rozsahu v klauzuli `From` nebo mohou odkazovat na proměnné rozsahu v předchozí klauzuli `From`.</span><span class="sxs-lookup"><span data-stu-id="ee969-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="ee969-131">Například následující příklad ukazuje vnořenou klauzuli `From`, kde kolekce v druhé klauzuli je založena na vlastnosti proměnné rozsahu v první klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ee969-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="ee969-132">U každé klauzule `From` může následovat jakákoli kombinace dalších klauzulí dotazu pro upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ee969-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="ee969-133">Dotaz můžete upřesnit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="ee969-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="ee969-134">Použijte implicitně kombinaci více kolekcí pomocí klauzulí `From` a `Select` nebo explicitně pomocí klauzule `Join` nebo `Group Join`.</span><span class="sxs-lookup"><span data-stu-id="ee969-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="ee969-135">K filtrování výsledků dotazu použijte klauzuli `Where`.</span><span class="sxs-lookup"><span data-stu-id="ee969-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="ee969-136">Seřaďte výsledek pomocí klauzule `Order By`.</span><span class="sxs-lookup"><span data-stu-id="ee969-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="ee969-137">Seskupte podobné výsledky společně pomocí klauzule `Group By`.</span><span class="sxs-lookup"><span data-stu-id="ee969-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="ee969-138">Použijte klauzuli `Aggregate` k identifikaci agregačních funkcí pro vyhodnocení celého výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="ee969-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="ee969-139">Použijte klauzuli `Let` k představení proměnné iterace, jejíž hodnota je určena výrazem namísto kolekce.</span><span class="sxs-lookup"><span data-stu-id="ee969-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="ee969-140">K ignorování duplicitních výsledků dotazu použijte klauzuli `Distinct`.</span><span class="sxs-lookup"><span data-stu-id="ee969-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="ee969-141">Identifikujte části výsledku, které se mají vrátit, pomocí klauzulí `Skip`, `Take`, `Skip While`a `Take While`.</span><span class="sxs-lookup"><span data-stu-id="ee969-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee969-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee969-142">Example</span></span>  
 <span data-ttu-id="ee969-143">Následující výraz dotazu používá klauzuli `From` k deklaraci proměnné rozsahu `cust` pro každý objekt `Customer` v kolekci `customers`.</span><span class="sxs-lookup"><span data-stu-id="ee969-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="ee969-144">Klauzule `Where` používá proměnnou rozsahu k omezení výstupu na zákazníky ze zadané oblasti.</span><span class="sxs-lookup"><span data-stu-id="ee969-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="ee969-145">Smyčka `For Each` zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="ee969-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="ee969-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee969-146">See also</span></span>

- [<span data-ttu-id="ee969-147">Dotazy</span><span class="sxs-lookup"><span data-stu-id="ee969-147">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="ee969-148">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee969-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ee969-149">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="ee969-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="ee969-150">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="ee969-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="ee969-151">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="ee969-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="ee969-152">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="ee969-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="ee969-153">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="ee969-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="ee969-154">Klauzule Distinct</span><span class="sxs-lookup"><span data-stu-id="ee969-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="ee969-155">Klauzule Join</span><span class="sxs-lookup"><span data-stu-id="ee969-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="ee969-156">Klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="ee969-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="ee969-157">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="ee969-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="ee969-158">Klauzule Let</span><span class="sxs-lookup"><span data-stu-id="ee969-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="ee969-159">Klauzule Skip</span><span class="sxs-lookup"><span data-stu-id="ee969-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="ee969-160">Klauzule Take</span><span class="sxs-lookup"><span data-stu-id="ee969-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="ee969-161">Klauzule Skip While</span><span class="sxs-lookup"><span data-stu-id="ee969-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="ee969-162">Klauzule Take While</span><span class="sxs-lookup"><span data-stu-id="ee969-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)

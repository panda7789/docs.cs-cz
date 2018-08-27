---
title: From – klauzule (Visual Basic)
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
ms.openlocfilehash: 71573de48cc51c48291fc4b82a0628d2d0f96caa
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932485"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="d3c1b-102">From – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3c1b-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="d3c1b-103">Určuje jednu nebo více proměnných rozsahu a kolekce pro dotaz.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3c1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3c1b-104">Syntax</span></span>  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d3c1b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d3c1b-105">Parts</span></span>  
  
|<span data-ttu-id="d3c1b-106">Termín</span><span class="sxs-lookup"><span data-stu-id="d3c1b-106">Term</span></span>|<span data-ttu-id="d3c1b-107">Definice</span><span class="sxs-lookup"><span data-stu-id="d3c1b-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="d3c1b-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-108">Required.</span></span> <span data-ttu-id="d3c1b-109">A *proměnnou rozsahu* použít k iteraci prvků kolekce.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="d3c1b-110">Proměnná rozsahu se používá k odkazování na každý člen `collection` podle dotazu se Iteruje přes `collection`.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="d3c1b-111">Musí být typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="d3c1b-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-112">Optional.</span></span> <span data-ttu-id="d3c1b-113">Typ `element`.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-113">The type of `element`.</span></span> <span data-ttu-id="d3c1b-114">Pokud ne `type` je zadán typ `element` je odvozen z `collection`.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="d3c1b-115">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-115">Required.</span></span> <span data-ttu-id="d3c1b-116">Odkazuje na kolekci, aby se dalo dotazovat.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="d3c1b-117">Musí být typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3c1b-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3c1b-118">Remarks</span></span>  
 <span data-ttu-id="d3c1b-119">`From` Klauzule slouží k identifikaci zdrojová data pro dotaz a proměnné, které se používají k odkazování na prvek ze zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="d3c1b-120">Tyto proměnné jsou volány *proměnné v rozsahu*.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-120">These variables are called *range variables*.</span></span> <span data-ttu-id="d3c1b-121">`From` Vyžádáním klauzule dotazu, kromě případů, kdy `Aggregate` klauzule slouží k identifikaci dotaz vrátí pouze agregovat výsledky.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="d3c1b-122">Další informace najdete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3c1b-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="d3c1b-123">Lze zadat více `From` klauzule v dotazu k identifikaci více kolekcí, který se má spojit.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="d3c1b-124">Pokud jsou zadány více kolekcí, se vyhodnocují přes nezávisle na sobě nebo je můžete spojit, když se vztahují.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="d3c1b-125">Kolekce lze implicitně propojit pomocí `Select` klauzuli, nebo explicitně pomocí `Join` nebo `Group Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="d3c1b-126">Jako alternativu můžete zadat více proměnných rozsahu a kolekce v jediném `From` klauzule s každou proměnnou rozsahu související a kolekce od ostatních oddělené čárkou.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="d3c1b-127">Následující příklad kódu ukazuje obě možnosti syntaxe pro `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 <span data-ttu-id="d3c1b-128">`From` Klauzule definuje rozsah dotazu, který je podobný oboru `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="d3c1b-129">Proto se každá `element` proměnnou rozsahu v rámci dotazu musí mít jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="d3c1b-130">Vzhledem k tomu, že lze zadat více `From` klauzule dotazu, následné `From` klauzule mohou odkazovat na rozsah proměnné ve `From` klauzuli, nebo mohou odkazovat na proměnné rozsahu v předchozím `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="d3c1b-131">Například následující příklad ukazuje vnořený `From` klauzule kde kolekce do druhé klauzule je založena na vlastnost proměnnou rozsahu v první klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 <span data-ttu-id="d3c1b-132">Každý `From` klauzule může být následován libovolnou kombinací další klauzule dotazu pro upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="d3c1b-133">Dotaz můžete upřesnit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="d3c1b-133">You can refine the query in the following ways:</span></span>  
  
-   <span data-ttu-id="d3c1b-134">Kombinace více kolekcí implicitně pomocí `From` a `Select` klauzule, nebo explicitně pomocí `Join` nebo `Group Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
-   <span data-ttu-id="d3c1b-135">Použití `Where` klauzule můžete filtrovat výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-135">Use the `Where` clause to filter the query result.</span></span>  
  
-   <span data-ttu-id="d3c1b-136">Řazení výsledků pomocí `Order By` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-136">Sort the result by using the `Order By` clause.</span></span>  
  
-   <span data-ttu-id="d3c1b-137">Seskupit podobné výsledky pomocí `Group By` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-137">Group similar results together by using the `Group By` clause.</span></span>  
  
-   <span data-ttu-id="d3c1b-138">Použití `Aggregate` klauzule k identifikaci agregační funkce má vyhodnotit pro výsledek celého dotazu.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
-   <span data-ttu-id="d3c1b-139">Použití `Let` klauzule zavést proměnnou iterace, jehož hodnota je určena výrazem místo kolekce.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
-   <span data-ttu-id="d3c1b-140">Použití `Distinct` klauzule ignorovat duplicitní dotaz výsledky.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
-   <span data-ttu-id="d3c1b-141">Identifikovat části výsledek určený k vrácení pomocí `Skip`, `Take`, `Skip While`, a `Take While` klauzule.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3c1b-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3c1b-142">Example</span></span>  
 <span data-ttu-id="d3c1b-143">Následující dotaz používá výraz `From` klauzule k deklaraci proměnné rozsahu `cust` pro každou `Customer` objekt `customers` kolekce.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="d3c1b-144">`Where` Klauzule používá proměnnou rozsahu omezení výstup pro zákazníky ze zadané oblasti.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="d3c1b-145">`For Each` Smyčky zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="d3c1b-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d3c1b-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3c1b-146">See Also</span></span>  
 [<span data-ttu-id="d3c1b-147">Dotazy</span><span class="sxs-lookup"><span data-stu-id="d3c1b-147">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="d3c1b-148">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3c1b-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="d3c1b-149">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="d3c1b-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="d3c1b-150">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="d3c1b-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="d3c1b-151">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="d3c1b-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="d3c1b-152">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="d3c1b-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="d3c1b-153">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="d3c1b-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="d3c1b-154">Klauzule Distinct</span><span class="sxs-lookup"><span data-stu-id="d3c1b-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="d3c1b-155">Klauzule Join</span><span class="sxs-lookup"><span data-stu-id="d3c1b-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="d3c1b-156">Klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="d3c1b-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="d3c1b-157">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="d3c1b-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="d3c1b-158">Klauzule Let</span><span class="sxs-lookup"><span data-stu-id="d3c1b-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="d3c1b-159">Klauzule Skip</span><span class="sxs-lookup"><span data-stu-id="d3c1b-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="d3c1b-160">Klauzule Take</span><span class="sxs-lookup"><span data-stu-id="d3c1b-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="d3c1b-161">Klauzule Skip While</span><span class="sxs-lookup"><span data-stu-id="d3c1b-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="d3c1b-162">Klauzule Take While</span><span class="sxs-lookup"><span data-stu-id="d3c1b-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)

---
title: "From – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ecdc8b70fb1ae164a6c78998ce11db9938fbb56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="e6754-102">From – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6754-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="e6754-103">Určuje jeden nebo více proměnných rozsahu a kolekce dotazu.</span><span class="sxs-lookup"><span data-stu-id="e6754-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6754-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6754-104">Syntax</span></span>  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="e6754-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e6754-105">Parts</span></span>  
  
|<span data-ttu-id="e6754-106">Termín</span><span class="sxs-lookup"><span data-stu-id="e6754-106">Term</span></span>|<span data-ttu-id="e6754-107">Definice</span><span class="sxs-lookup"><span data-stu-id="e6754-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="e6754-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e6754-108">Required.</span></span> <span data-ttu-id="e6754-109">A *proměnnou rozsahu* použít k iteraci v rámci prvků kolekce.</span><span class="sxs-lookup"><span data-stu-id="e6754-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="e6754-110">Proměnná rozsahu slouží k odkazování na každý člen `collection` jako iteruje dotaz `collection`.</span><span class="sxs-lookup"><span data-stu-id="e6754-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="e6754-111">Musí být typu vyčíslitelná.</span><span class="sxs-lookup"><span data-stu-id="e6754-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="e6754-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e6754-112">Optional.</span></span> <span data-ttu-id="e6754-113">Typ `element`.</span><span class="sxs-lookup"><span data-stu-id="e6754-113">The type of `element`.</span></span> <span data-ttu-id="e6754-114">Pokud žádné `type` je zadaný typ `element` je odvozeno z `collection`.</span><span class="sxs-lookup"><span data-stu-id="e6754-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="e6754-115">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e6754-115">Required.</span></span> <span data-ttu-id="e6754-116">Odkazuje na kolekci má být dotazován.</span><span class="sxs-lookup"><span data-stu-id="e6754-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="e6754-117">Musí být typu vyčíslitelná.</span><span class="sxs-lookup"><span data-stu-id="e6754-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6754-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6754-118">Remarks</span></span>  
 <span data-ttu-id="e6754-119">`From` Klauzule slouží k identifikaci zdroje dat pro dotaz a proměnné, které slouží k odkazování na element z kolekce zdroje.</span><span class="sxs-lookup"><span data-stu-id="e6754-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="e6754-120">Tyto proměnné se nazývají *rozsahu proměnné*.</span><span class="sxs-lookup"><span data-stu-id="e6754-120">These variables are called *range variables*.</span></span> <span data-ttu-id="e6754-121">`From` Klauzule se vyžaduje pro daný dotaz, s výjimkou případů, kdy `Aggregate` klauzule slouží k identifikaci vrátí pouze agregovat výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="e6754-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="e6754-122">Další informace najdete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e6754-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="e6754-123">Můžete určit více `From` klauzule v dotazu k identifikaci více kolekcí, který se má spojit.</span><span class="sxs-lookup"><span data-stu-id="e6754-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="e6754-124">Jsou-li více kolekcí, že jsou vstupní přes nezávisle nebo je můžete připojit, pokud se vztahují.</span><span class="sxs-lookup"><span data-stu-id="e6754-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="e6754-125">Kolekce lze propojit implicitně pomocí `Select` klauzuli, nebo explicitně pomocí `Join` nebo `Group Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e6754-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="e6754-126">Jako alternativu, můžete určit více proměnné rozsahu a kolekcí v jediném `From` klauzule s každou proměnnou související rozsahu a do čárkami oddělených z jiné kolekce.</span><span class="sxs-lookup"><span data-stu-id="e6754-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="e6754-127">Následující příklad kódu ukazuje obě možnosti syntaxe pro `From` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e6754-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 <span data-ttu-id="e6754-128">`From` Klauzule definuje obor dotazu, který je podobný oboru `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="e6754-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="e6754-129">Proto každý `element` proměnnou rozsahu v oboru dotazu musí mít jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="e6754-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="e6754-130">Protože můžete určit více `From` klauzule pro daný dotaz, následných `From` klauzule mohou odkazovat na proměnné rozsahu v `From` klauzuli, nebo se mohou odkazovat na proměnné rozsahu v předchozím `From` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e6754-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="e6754-131">Například následující příklad ukazuje vnořený `From` klauzule, kde je kolekce v druhé založena na vlastnost proměnnou rozsahu v klauzuli první.</span><span class="sxs-lookup"><span data-stu-id="e6754-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 <span data-ttu-id="e6754-132">Každý `From` klauzule může následovat libovolnou kombinaci klauzule další dotazu pro upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="e6754-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="e6754-133">Dotaz můžete upřesnit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="e6754-133">You can refine the query in the following ways:</span></span>  
  
-   <span data-ttu-id="e6754-134">Implicitně kombinovat více kolekcí pomocí `From` a `Select` klauzule, nebo explicitně pomocí `Join` nebo `Group Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e6754-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
-   <span data-ttu-id="e6754-135">Použití `Where` klauzule filtrování výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="e6754-135">Use the `Where` clause to filter the query result.</span></span>  
  
-   <span data-ttu-id="e6754-136">Řazení výsledek pomocí `Order By` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e6754-136">Sort the result by using the `Order By` clause.</span></span>  
  
-   <span data-ttu-id="e6754-137">Seskupit podobné výsledky pomocí `Group By` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e6754-137">Group similar results together by using the `Group By` clause.</span></span>  
  
-   <span data-ttu-id="e6754-138">Použití `Aggregate` klauzule k identifikaci agregační funkce vyhodnotit výsledek celý dotaz.</span><span class="sxs-lookup"><span data-stu-id="e6754-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
-   <span data-ttu-id="e6754-139">Použití `Let` klauzule zavádět proměnné iterace, jehož hodnota je určena pomocí výrazu místo kolekce.</span><span class="sxs-lookup"><span data-stu-id="e6754-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
-   <span data-ttu-id="e6754-140">Použití `Distinct` klauzule ignorovat výsledky duplicitní dotazu.</span><span class="sxs-lookup"><span data-stu-id="e6754-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
-   <span data-ttu-id="e6754-141">Identifikaci částí výsledek určený k vrácení pomocí `Skip`, `Take`, `Skip While`, a `Take While` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e6754-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6754-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6754-142">Example</span></span>  
 <span data-ttu-id="e6754-143">Následující dotaz výraz používá `From` klauzule deklarovat proměnnou rozsahu `cust` pro každou `Customer` objekt v `customers` kolekce.</span><span class="sxs-lookup"><span data-stu-id="e6754-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="e6754-144">`Where` Klauzule používá proměnnou rozsahu omezit výstupu na zákazníky ze zadané oblasti.</span><span class="sxs-lookup"><span data-stu-id="e6754-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="e6754-145">`For Each` Smyčky zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="e6754-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e6754-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6754-146">See Also</span></span>  
 [<span data-ttu-id="e6754-147">Dotazy</span><span class="sxs-lookup"><span data-stu-id="e6754-147">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="e6754-148">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6754-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="e6754-149">Pro každou... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="e6754-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="e6754-150">Pro... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="e6754-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="e6754-151">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6754-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="e6754-152">Kde – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6754-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="e6754-153">AGGREGATE – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6754-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="e6754-154">DISTINCT – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6754-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="e6754-155">JOIN – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6754-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="e6754-156">Group Join – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6754-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="e6754-157">Order By – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6754-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="e6754-158">Let – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6754-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="e6754-159">Skip – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6754-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="e6754-160">Take – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6754-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="e6754-161">Skip While – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6754-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="e6754-162">Take While – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6754-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)

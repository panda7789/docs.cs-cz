---
title: "Group Join – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c43b41336393b40684aee79f88c1e6999ebda674
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="group-join-clause-visual-basic"></a><span data-ttu-id="748e5-102">Group Join – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="748e5-102">Group Join Clause (Visual Basic)</span></span>
<span data-ttu-id="748e5-103">Kombinuje dvě kolekce do jedné hierarchické kolekce.</span><span class="sxs-lookup"><span data-stu-id="748e5-103">Combines two collections into a single hierarchical collection.</span></span> <span data-ttu-id="748e5-104">Spojení operace je založená na odpovídající klíče.</span><span class="sxs-lookup"><span data-stu-id="748e5-104">The join operation is based on matching keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="748e5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="748e5-105">Syntax</span></span>  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="748e5-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="748e5-106">Parts</span></span>  
  
|<span data-ttu-id="748e5-107">Termín</span><span class="sxs-lookup"><span data-stu-id="748e5-107">Term</span></span>|<span data-ttu-id="748e5-108">Definice</span><span class="sxs-lookup"><span data-stu-id="748e5-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="748e5-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="748e5-109">Required.</span></span> <span data-ttu-id="748e5-110">Ovládací prvek proměnnou pro kolekci se připojený.</span><span class="sxs-lookup"><span data-stu-id="748e5-110">The control variable for the collection being joined.</span></span>|  
|`type`|<span data-ttu-id="748e5-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="748e5-111">Optional.</span></span> <span data-ttu-id="748e5-112">Typ `element`.</span><span class="sxs-lookup"><span data-stu-id="748e5-112">The type of `element`.</span></span> <span data-ttu-id="748e5-113">Pokud žádné `type` je zadaný typ `element` je odvozeno z `collection`.</span><span class="sxs-lookup"><span data-stu-id="748e5-113">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="748e5-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="748e5-114">Required.</span></span> <span data-ttu-id="748e5-115">Kolekce se zkombinovat s kolekcí, který je na levé straně `Group Join` operátor.</span><span class="sxs-lookup"><span data-stu-id="748e5-115">The collection to combine with the collection that is on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="748e5-116">A `Group Join` klauzule mohou být použity v `Join` klauzule nebo v jiném `Group Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="748e5-116">A `Group Join` clause can be nested in a `Join` clause or in another `Group Join` clause.</span></span>|  
|<span data-ttu-id="748e5-117">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="748e5-117">`key1` `Equals` `key2`</span></span>|<span data-ttu-id="748e5-118">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="748e5-118">Required.</span></span> <span data-ttu-id="748e5-119">Identifikuje klíče pro kolekce se připojený.</span><span class="sxs-lookup"><span data-stu-id="748e5-119">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="748e5-120">Je nutné použít `Equals` operátor k porovnání klíče z kolekce se připojený.</span><span class="sxs-lookup"><span data-stu-id="748e5-120">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="748e5-121">Podmínky připojení můžete kombinovat pomocí `And` operátor k identifikaci několik klíčů.</span><span class="sxs-lookup"><span data-stu-id="748e5-121">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="748e5-122">`key1` Parametr musí být z kolekce na levé straně `Join` operátor.</span><span class="sxs-lookup"><span data-stu-id="748e5-122">The `key1` parameter must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="748e5-123">`key2` Parametr musí být z kolekce na pravé straně `Join` operátor.</span><span class="sxs-lookup"><span data-stu-id="748e5-123">The `key2` parameter must be from the collection on the right side of the `Join` operator.</span></span><br /><br /> <span data-ttu-id="748e5-124">Klíčů používaných v podmínku připojení může být výrazy, které obsahují více než jednu položku z kolekce.</span><span class="sxs-lookup"><span data-stu-id="748e5-124">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="748e5-125">Každý výraz klíče však může obsahovat pouze položky z jeho příslušné kolekce.</span><span class="sxs-lookup"><span data-stu-id="748e5-125">However, each key expression can contain only items from its respective collection.</span></span>|  
|`expressionList`|<span data-ttu-id="748e5-126">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="748e5-126">Required.</span></span> <span data-ttu-id="748e5-127">Jeden nebo více výrazů, které určují, jak jsou agregovat skupiny elementy z kolekce.</span><span class="sxs-lookup"><span data-stu-id="748e5-127">One or more expressions that identify how the groups of elements from the collection are aggregated.</span></span> <span data-ttu-id="748e5-128">Lze zjistit název člena seskupené výsledků `Group` – klíčové slovo (`<alias> = Group`).</span><span class="sxs-lookup"><span data-stu-id="748e5-128">To identify a member name for the grouped results, use the `Group` keyword (`<alias> = Group`).</span></span> <span data-ttu-id="748e5-129">Můžete použít také agregační funkce na aplikujete na skupinu.</span><span class="sxs-lookup"><span data-stu-id="748e5-129">You can also include aggregate functions to apply to the group.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="748e5-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="748e5-130">Remarks</span></span>  
 <span data-ttu-id="748e5-131">`Group Join` Klauzule kombinuje dvě kolekce na základě shody se hodnoty klíče z kolekce se připojený.</span><span class="sxs-lookup"><span data-stu-id="748e5-131">The `Group Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="748e5-132">Výsledný kolekce může obsahovat člena, který odkazuje na kolekci elementů z druhé kolekci, která odpovídají hodnotě klíče z první kolekce.</span><span class="sxs-lookup"><span data-stu-id="748e5-132">The resulting collection can contain a member that references a collection of elements from the second collection that match the key value from the first collection.</span></span> <span data-ttu-id="748e5-133">Můžete také zadat agregační funkce použít na seskupené elementy z druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="748e5-133">You can also specify aggregate functions to apply to the grouped elements from the second collection.</span></span> <span data-ttu-id="748e5-134">Informace o agregační funkce najdete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="748e5-134">For information about aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="748e5-135">Zvažte například kolekce správci a kolekce zaměstnanci.</span><span class="sxs-lookup"><span data-stu-id="748e5-135">Consider, for example, a collection of managers and a collection of employees.</span></span> <span data-ttu-id="748e5-136">Elementy z obou kolekcí mají ManagerID vlastnost, která identifikuje zaměstnance, kteří pro konkrétní nadřízeného.</span><span class="sxs-lookup"><span data-stu-id="748e5-136">Elements from both collections have a ManagerID property that identifies the employees that report to a particular manager.</span></span> <span data-ttu-id="748e5-137">Výsledek pro každou manager a zaměstnanci s odpovídající hodnotou ManagerID by obsahovat výsledky z operace spojení.</span><span class="sxs-lookup"><span data-stu-id="748e5-137">The results from a join operation would contain a result for each manager and employee with a matching ManagerID value.</span></span> <span data-ttu-id="748e5-138">Výsledky z `Group Join` operace by obsahovat úplný seznam správci.</span><span class="sxs-lookup"><span data-stu-id="748e5-138">The results from a `Group Join` operation would contain the complete list of managers.</span></span> <span data-ttu-id="748e5-139">Každý výsledek manager by měla mít člena, který odkazuje seznamu zaměstnanců, které byly shoda pro konkrétní správce.</span><span class="sxs-lookup"><span data-stu-id="748e5-139">Each manager result would have a member that referenced the list of employees that were a match for the specific manager.</span></span>  
  
 <span data-ttu-id="748e5-140">Kolekce vyplývající z `Group Join` operace může obsahovat libovolnou kombinaci hodnot z kolekce v identifikovat `From` klauzule a výrazy určené v `Into` klauzuli `Group Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="748e5-140">The collection resulting from a `Group Join` operation can contain any combination of values from the collection identified in the `From` clause and the expressions identified in the `Into` clause of the `Group Join` clause.</span></span> <span data-ttu-id="748e5-141">Další informace o platné výrazy pro `Into` klauzule, najdete v části [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="748e5-141">For more information about valid expressions for the `Into` clause, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="748e5-142">A `Group Join` operace vrátí všechny výsledky z kolekce identifikovat na levé straně `Group Join` operátor.</span><span class="sxs-lookup"><span data-stu-id="748e5-142">A `Group Join` operation will return all results from the collection identified on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="748e5-143">To platí i v případě, že neexistují žádné odpovídající položky v kolekci se připojený.</span><span class="sxs-lookup"><span data-stu-id="748e5-143">This is true even if there are no matches in the collection being joined.</span></span> <span data-ttu-id="748e5-144">Toto je třeba `LEFT OUTER JOIN` v systému SQL.</span><span class="sxs-lookup"><span data-stu-id="748e5-144">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="748e5-145">Můžete použít `Join` klauzule kombinování kolekcí do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="748e5-145">You can use the `Join` clause to combine collections into a single collection.</span></span> <span data-ttu-id="748e5-146">Jde o ekvivalent `INNER JOIN` v systému SQL.</span><span class="sxs-lookup"><span data-stu-id="748e5-146">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="748e5-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="748e5-147">Example</span></span>  
 <span data-ttu-id="748e5-148">Následující příklad kódu spojí dvě kolekce pomocí `Group Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="748e5-148">The following code example joins two collections by using the `Group Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="748e5-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="748e5-149">See Also</span></span>  
 [<span data-ttu-id="748e5-150">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="748e5-150">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="748e5-151">Dotazy</span><span class="sxs-lookup"><span data-stu-id="748e5-151">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="748e5-152">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="748e5-152">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="748e5-153">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="748e5-153">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="748e5-154">JOIN – klauzule</span><span class="sxs-lookup"><span data-stu-id="748e5-154">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="748e5-155">Kde – klauzule</span><span class="sxs-lookup"><span data-stu-id="748e5-155">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="748e5-156">Group By – klauzule</span><span class="sxs-lookup"><span data-stu-id="748e5-156">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)

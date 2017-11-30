---
title: "Join – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bb25c9dac8994e7f975539c1d036f0f0d9d239e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="957a8-102">Join – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="957a8-102">Join Clause (Visual Basic)</span></span>
<span data-ttu-id="957a8-103">Kombinuje dvě kolekce do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="957a8-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="957a8-104">Operace spojení je založena na odpovídající klíče a používá `Equals` operátor.</span><span class="sxs-lookup"><span data-stu-id="957a8-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="957a8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="957a8-105">Syntax</span></span>  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a><span data-ttu-id="957a8-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="957a8-106">Parts</span></span>  
 `element`  
 <span data-ttu-id="957a8-107">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="957a8-107">Required.</span></span> <span data-ttu-id="957a8-108">Ovládací prvek proměnnou pro kolekci se připojený.</span><span class="sxs-lookup"><span data-stu-id="957a8-108">The control variable for the collection being joined.</span></span>  
  
 `collection`  
 <span data-ttu-id="957a8-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="957a8-109">Required.</span></span> <span data-ttu-id="957a8-110">Kolekce se zkombinovat s kolekcí identifikovat na levé straně `Join` operátor.</span><span class="sxs-lookup"><span data-stu-id="957a8-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="957a8-111">A `Join` klauzule mohou být použity v jiné `Join` klauzuli, nebo v `Group Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="957a8-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>  
  
 `joinClause`  
 <span data-ttu-id="957a8-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="957a8-112">Optional.</span></span> <span data-ttu-id="957a8-113">Jeden nebo více dalších `Join` klauzule pro další upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="957a8-113">One or more additional `Join` clauses to further refine the query.</span></span>  
  
 `groupJoinClause`  
 <span data-ttu-id="957a8-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="957a8-114">Optional.</span></span> <span data-ttu-id="957a8-115">Jeden nebo více dalších `Group Join` klauzule pro další upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="957a8-115">One or more additional `Group Join` clauses to further refine the query.</span></span>  
  
 <span data-ttu-id="957a8-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="957a8-116">`key1` `Equals` `key2`</span></span>  
 <span data-ttu-id="957a8-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="957a8-117">Required.</span></span> <span data-ttu-id="957a8-118">Identifikuje klíče pro kolekce se připojený.</span><span class="sxs-lookup"><span data-stu-id="957a8-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="957a8-119">Je nutné použít `Equals` operátor k porovnání klíče z kolekce se připojený.</span><span class="sxs-lookup"><span data-stu-id="957a8-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="957a8-120">Podmínky připojení můžete kombinovat pomocí `And` operátor k identifikaci několik klíčů.</span><span class="sxs-lookup"><span data-stu-id="957a8-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="957a8-121">`key1`musí být z kolekce na levé straně `Join` operátor.</span><span class="sxs-lookup"><span data-stu-id="957a8-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="957a8-122">`key2`musí být z kolekce na pravé straně `Join` operátor.</span><span class="sxs-lookup"><span data-stu-id="957a8-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>  
  
 <span data-ttu-id="957a8-123">Klíčů používaných v podmínku připojení může být výrazy, které obsahují více než jednu položku z kolekce.</span><span class="sxs-lookup"><span data-stu-id="957a8-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="957a8-124">Každý výraz klíče však může obsahovat pouze položky z jeho příslušné kolekce.</span><span class="sxs-lookup"><span data-stu-id="957a8-124">However, each key expression can contain only items from its respective collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="957a8-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="957a8-125">Remarks</span></span>  
 <span data-ttu-id="957a8-126">`Join` Klauzule kombinuje dvě kolekce na základě shody se hodnoty klíče z kolekce se připojený.</span><span class="sxs-lookup"><span data-stu-id="957a8-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="957a8-127">Výsledný kolekce může obsahovat libovolnou kombinaci hodnoty z kolekce identifikovat na levé straně `Join` operátor a identifikovat v kolekci `Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="957a8-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="957a8-128">Dotaz vrátí jenom ty výsledky, pro které podmínku určeného `Equals` splníte operátor.</span><span class="sxs-lookup"><span data-stu-id="957a8-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="957a8-129">Jde o ekvivalent `INNER JOIN` v systému SQL.</span><span class="sxs-lookup"><span data-stu-id="957a8-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="957a8-130">Můžete použít více `Join` klauzule v dotazu pro připojení dvě nebo více kolekcí do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="957a8-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>  
  
 <span data-ttu-id="957a8-131">Můžete provádět na implicitní spojení kombinovat kolekce bez `Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="957a8-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="957a8-132">Chcete-li to provést, obsahovat více `In` klauzule v vaše `From` klauzule a zadejte `Where` klauzuli, která identifikuje klíčů, které chcete použít pro spojení.</span><span class="sxs-lookup"><span data-stu-id="957a8-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>  
  
 <span data-ttu-id="957a8-133">Můžete použít `Group Join` klauzule kombinování kolekcí do jedné hierarchické kolekce.</span><span class="sxs-lookup"><span data-stu-id="957a8-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="957a8-134">Toto je třeba `LEFT OUTER JOIN` v systému SQL.</span><span class="sxs-lookup"><span data-stu-id="957a8-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="957a8-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="957a8-135">Example</span></span>  
 <span data-ttu-id="957a8-136">Následující příklad kódu provede na implicitní spojení kombinovat seznamu zákazníků jejich objednávky.</span><span class="sxs-lookup"><span data-stu-id="957a8-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="957a8-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="957a8-137">Example</span></span>  
 <span data-ttu-id="957a8-138">Následující příklad kódu spojí dvě kolekce pomocí `Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="957a8-138">The following code example joins two collections by using the `Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 <span data-ttu-id="957a8-139">Tento příklad vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="957a8-139">This example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a><span data-ttu-id="957a8-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="957a8-140">Example</span></span>  
 <span data-ttu-id="957a8-141">Následující příklad kódu spojí dvě kolekce pomocí `Join` klauzuli with dvě klíčové sloupce.</span><span class="sxs-lookup"><span data-stu-id="957a8-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 <span data-ttu-id="957a8-142">Tento příklad vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="957a8-142">The example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a><span data-ttu-id="957a8-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="957a8-143">See Also</span></span>  
 [<span data-ttu-id="957a8-144">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="957a8-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="957a8-145">Dotazy</span><span class="sxs-lookup"><span data-stu-id="957a8-145">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="957a8-146">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="957a8-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="957a8-147">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="957a8-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="957a8-148">Group Join – klauzule</span><span class="sxs-lookup"><span data-stu-id="957a8-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="957a8-149">Kde – klauzule</span><span class="sxs-lookup"><span data-stu-id="957a8-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)

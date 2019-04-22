---
title: Join – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: 21432b95b30ae38ac2cbc9e55b5a3066f0bef665
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825843"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="44b0f-102">Join – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44b0f-102">Join Clause (Visual Basic)</span></span>
<span data-ttu-id="44b0f-103">Kombinuje dvě kolekce do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="44b0f-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="44b0f-104">Operace spojení je založená na shodujících se klíčích a používá `Equals` operátor.</span><span class="sxs-lookup"><span data-stu-id="44b0f-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44b0f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44b0f-105">Syntax</span></span>  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a><span data-ttu-id="44b0f-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="44b0f-106">Parts</span></span>  
 `element`  
 <span data-ttu-id="44b0f-107">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="44b0f-107">Required.</span></span> <span data-ttu-id="44b0f-108">Řídicí proměnná pro kolekci, je připojen.</span><span class="sxs-lookup"><span data-stu-id="44b0f-108">The control variable for the collection being joined.</span></span>  
  
 `collection`  
 <span data-ttu-id="44b0f-109">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="44b0f-109">Required.</span></span> <span data-ttu-id="44b0f-110">Kolekce, kterou chcete v kombinaci s kolekce vymezených na levé straně `Join` operátor.</span><span class="sxs-lookup"><span data-stu-id="44b0f-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="44b0f-111">A `Join` klauzule může být vnořena v jiné `Join` klauzuli, nebo `Group Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="44b0f-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>  
  
 `joinClause`  
 <span data-ttu-id="44b0f-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="44b0f-112">Optional.</span></span> <span data-ttu-id="44b0f-113">Jeden nebo více dalších `Join` klauzule pro další upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="44b0f-113">One or more additional `Join` clauses to further refine the query.</span></span>  
  
 `groupJoinClause`  
 <span data-ttu-id="44b0f-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="44b0f-114">Optional.</span></span> <span data-ttu-id="44b0f-115">Jeden nebo více dalších `Group Join` klauzule pro další upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="44b0f-115">One or more additional `Group Join` clauses to further refine the query.</span></span>  
  
 <span data-ttu-id="44b0f-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="44b0f-116">`key1` `Equals` `key2`</span></span>  
 <span data-ttu-id="44b0f-117">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="44b0f-117">Required.</span></span> <span data-ttu-id="44b0f-118">Určuje klíče pro kolekce, je připojen.</span><span class="sxs-lookup"><span data-stu-id="44b0f-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="44b0f-119">Je nutné použít `Equals` operátor porovnání klíčů z kolekcí je připojen.</span><span class="sxs-lookup"><span data-stu-id="44b0f-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="44b0f-120">Podmínky připojení můžete kombinovat pomocí `And` operátor k identifikaci více klíčů.</span><span class="sxs-lookup"><span data-stu-id="44b0f-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="44b0f-121">`key1` musí být z kolekce na levé straně `Join` operátor.</span><span class="sxs-lookup"><span data-stu-id="44b0f-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="44b0f-122">`key2` musí být z kolekce na pravé straně `Join` operátor.</span><span class="sxs-lookup"><span data-stu-id="44b0f-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>  
  
 <span data-ttu-id="44b0f-123">Klíče používané v podmínku připojení může být výrazů, které obsahují více než jednu položku z kolekce.</span><span class="sxs-lookup"><span data-stu-id="44b0f-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="44b0f-124">Každý výraz klíče však může obsahovat pouze položky z jeho příslušné kolekce.</span><span class="sxs-lookup"><span data-stu-id="44b0f-124">However, each key expression can contain only items from its respective collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44b0f-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44b0f-125">Remarks</span></span>  
 <span data-ttu-id="44b0f-126">`Join` Klauzule kombinuje dvě kolekce na základě porovnání hodnoty klíče z kolekcí je připojen.</span><span class="sxs-lookup"><span data-stu-id="44b0f-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="44b0f-127">Výsledný kolekce může obsahovat libovolnou kombinaci hodnot z kolekce vymezených na levé straně `Join` operátor a identifikovat v kolekci `Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="44b0f-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="44b0f-128">Dotaz vrátí pouze výsledky, pro které je podmínka určené `Equals` operátor je splněna.</span><span class="sxs-lookup"><span data-stu-id="44b0f-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="44b0f-129">To je ekvivalentní `INNER JOIN` v SQL.</span><span class="sxs-lookup"><span data-stu-id="44b0f-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="44b0f-130">Lze použít více `Join` klauzule v dotazu pro připojení dvou nebo více kolekcí do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="44b0f-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>  
  
 <span data-ttu-id="44b0f-131">Můžete provést implicitní spojení kombinování kolekcí bez `Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="44b0f-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="44b0f-132">K tomuto účelu zahrnují více `In` ustanovení vaší `From` klauzule a zadejte `Where` klauzuli, která identifikuje klíče, které chcete použít pro připojení.</span><span class="sxs-lookup"><span data-stu-id="44b0f-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>  
  
 <span data-ttu-id="44b0f-133">Můžete použít `Group Join` klauzule zkombinovat kolekce do jedné hierarchické kolekce.</span><span class="sxs-lookup"><span data-stu-id="44b0f-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="44b0f-134">Podobá se trochu `LEFT OUTER JOIN` v SQL.</span><span class="sxs-lookup"><span data-stu-id="44b0f-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b0f-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="44b0f-135">Example</span></span>  
 <span data-ttu-id="44b0f-136">Následující příklad kódu provádí implicitní spojení do seznamu zákazníků v kombinaci s jejich objednávky.</span><span class="sxs-lookup"><span data-stu-id="44b0f-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="44b0f-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="44b0f-137">Example</span></span>  
 <span data-ttu-id="44b0f-138">Následující příklad kódu spojení dvou kolekcí s použitím `Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="44b0f-138">The following code example joins two collections by using the `Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]  
  
 <span data-ttu-id="44b0f-139">Tento příklad vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="44b0f-139">This example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a><span data-ttu-id="44b0f-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="44b0f-140">Example</span></span>  
 <span data-ttu-id="44b0f-141">Následující příklad kódu spojení dvou kolekcí s použitím `Join` klauzule dvě klíčové sloupce.</span><span class="sxs-lookup"><span data-stu-id="44b0f-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]  
  
 <span data-ttu-id="44b0f-142">Tento příklad vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="44b0f-142">The example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a><span data-ttu-id="44b0f-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44b0f-143">See also</span></span>

- [<span data-ttu-id="44b0f-144">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="44b0f-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="44b0f-145">Dotazy</span><span class="sxs-lookup"><span data-stu-id="44b0f-145">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="44b0f-146">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="44b0f-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="44b0f-147">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="44b0f-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="44b0f-148">Klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="44b0f-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="44b0f-149">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="44b0f-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)

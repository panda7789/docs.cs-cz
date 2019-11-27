---
title: Join – klauzule
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
ms.openlocfilehash: b0baca9f897a00b3c6c67699629477ff385d6ef7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353267"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="4d789-102">Join – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d789-102">Join Clause (Visual Basic)</span></span>

<span data-ttu-id="4d789-103">Kombinuje dvě kolekce do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="4d789-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="4d789-104">Operace JOIN je založena na porovnávacích klíčích a používá operátor `Equals`.</span><span class="sxs-lookup"><span data-stu-id="4d789-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d789-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d789-105">Syntax</span></span>

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a><span data-ttu-id="4d789-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="4d789-106">Parts</span></span>

<span data-ttu-id="4d789-107">`element` nutné.</span><span class="sxs-lookup"><span data-stu-id="4d789-107">`element` Required.</span></span> <span data-ttu-id="4d789-108">Řídicí proměnná pro kolekci, která je připojena.</span><span class="sxs-lookup"><span data-stu-id="4d789-108">The control variable for the collection being joined.</span></span>

`collection`  
<span data-ttu-id="4d789-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4d789-109">Required.</span></span> <span data-ttu-id="4d789-110">Kolekce, která se má zkombinovat s kolekcí identifikovanou na levé straně operátoru `Join`</span><span class="sxs-lookup"><span data-stu-id="4d789-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="4d789-111">Klauzule `Join` může být vnořena do jiné klauzule `Join` nebo v klauzuli `Group Join`.</span><span class="sxs-lookup"><span data-stu-id="4d789-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>

`joinClause`  
<span data-ttu-id="4d789-112">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="4d789-112">Optional.</span></span> <span data-ttu-id="4d789-113">Jedna nebo více dalších klauzulí `Join` pro další upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="4d789-113">One or more additional `Join` clauses to further refine the query.</span></span>

`groupJoinClause`  
<span data-ttu-id="4d789-114">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="4d789-114">Optional.</span></span> <span data-ttu-id="4d789-115">Jedna nebo více dalších klauzulí `Group Join` pro další upřesnění dotazu.</span><span class="sxs-lookup"><span data-stu-id="4d789-115">One or more additional `Group Join` clauses to further refine the query.</span></span>

<span data-ttu-id="4d789-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="4d789-116">`key1` `Equals` `key2`</span></span>  
<span data-ttu-id="4d789-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4d789-117">Required.</span></span> <span data-ttu-id="4d789-118">Identifikuje klíče pro připojené kolekce.</span><span class="sxs-lookup"><span data-stu-id="4d789-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="4d789-119">K porovnání klíčů z kolekce, které jsou spojeny, je nutné použít operátor `Equals`.</span><span class="sxs-lookup"><span data-stu-id="4d789-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="4d789-120">Podmínky spojení můžete kombinovat pomocí operátoru `And` k identifikaci více klíčů.</span><span class="sxs-lookup"><span data-stu-id="4d789-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="4d789-121">`key1` musí být z kolekce na levé straně operátoru `Join`.</span><span class="sxs-lookup"><span data-stu-id="4d789-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="4d789-122">`key2` musí být z kolekce na pravé straně operátoru `Join`.</span><span class="sxs-lookup"><span data-stu-id="4d789-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>

<span data-ttu-id="4d789-123">Klíče používané v podmínce spojení mohou být výrazy, které obsahují více než jednu položku z kolekce.</span><span class="sxs-lookup"><span data-stu-id="4d789-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="4d789-124">Každý klíčový výraz však může obsahovat pouze položky z příslušné kolekce.</span><span class="sxs-lookup"><span data-stu-id="4d789-124">However, each key expression can contain only items from its respective collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d789-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d789-125">Remarks</span></span>

<span data-ttu-id="4d789-126">Klauzule `Join` kombinuje dvě kolekce založené na porovnání hodnot klíčů od připojených kolekcí.</span><span class="sxs-lookup"><span data-stu-id="4d789-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="4d789-127">Výsledná kolekce může obsahovat libovolnou kombinaci hodnot z kolekce identifikované na levé straně operátoru `Join` a kolekce identifikovaná v klauzuli `Join`.</span><span class="sxs-lookup"><span data-stu-id="4d789-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="4d789-128">Dotaz vrátí pouze výsledky, pro které je splněna podmínka určená operátorem `Equals`.</span><span class="sxs-lookup"><span data-stu-id="4d789-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="4d789-129">Jedná se o ekvivalent `INNER JOIN` v SQL.</span><span class="sxs-lookup"><span data-stu-id="4d789-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>

<span data-ttu-id="4d789-130">V dotazu můžete použít více klauzulí `Join` pro spojení dvou nebo více kolekcí do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="4d789-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>

<span data-ttu-id="4d789-131">Můžete provést implicitní spojení pro kombinování kolekcí bez klauzule `Join`.</span><span class="sxs-lookup"><span data-stu-id="4d789-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="4d789-132">Chcete-li to provést, zahrňte do klauzule `From` více klauzulí `In` a určete klauzuli `Where`, která určuje klíče, které chcete použít pro spojení.</span><span class="sxs-lookup"><span data-stu-id="4d789-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>

<span data-ttu-id="4d789-133">Klauzuli `Group Join` můžete použít ke kombinování kolekcí do jedné hierarchické kolekce.</span><span class="sxs-lookup"><span data-stu-id="4d789-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="4d789-134">Jedná se například o `LEFT OUTER JOIN` v SQL.</span><span class="sxs-lookup"><span data-stu-id="4d789-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>

## <a name="example"></a><span data-ttu-id="4d789-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d789-135">Example</span></span>

<span data-ttu-id="4d789-136">Následující příklad kódu provede implicitní spojení a kombinuje seznam zákazníků se svými objednávkami.</span><span class="sxs-lookup"><span data-stu-id="4d789-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a><span data-ttu-id="4d789-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d789-137">Example</span></span>

<span data-ttu-id="4d789-138">Následující příklad kódu spojuje dvě kolekce pomocí klauzule `Join`.</span><span class="sxs-lookup"><span data-stu-id="4d789-138">The following code example joins two collections by using the `Join` clause.</span></span>

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

<span data-ttu-id="4d789-139">Tento příklad vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="4d789-139">This example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a><span data-ttu-id="4d789-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d789-140">Example</span></span>

<span data-ttu-id="4d789-141">Následující příklad kódu spojuje dvě kolekce pomocí klauzule `Join` se dvěma klíčovými sloupci.</span><span class="sxs-lookup"><span data-stu-id="4d789-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

<span data-ttu-id="4d789-142">Příklad vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="4d789-142">The example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a><span data-ttu-id="4d789-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d789-143">See also</span></span>

- [<span data-ttu-id="4d789-144">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d789-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="4d789-145">Dotazy</span><span class="sxs-lookup"><span data-stu-id="4d789-145">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="4d789-146">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="4d789-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="4d789-147">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="4d789-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="4d789-148">Klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="4d789-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="4d789-149">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="4d789-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)

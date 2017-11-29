---
title: "Množinové operace (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e30c521635326afeea4aad9ce932d5206d06c6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="f5cad-102">Množinové operace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5cad-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="f5cad-103">Množinové operace v technologii LINQ naleznete v operacích dotazu, které produkují je sada výsledků dotazu, který je založen na přítomnosti nebo absenci ekvivalentní elementů v rámci stejné nebo samostatné kolekce (nebo sady).</span><span class="sxs-lookup"><span data-stu-id="f5cad-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="f5cad-104">Operátor metody standardní dotazů, které provádět operace set jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="f5cad-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5cad-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f5cad-105">Methods</span></span>  
  
|<span data-ttu-id="f5cad-106">Název metody</span><span class="sxs-lookup"><span data-stu-id="f5cad-106">Method Name</span></span>|<span data-ttu-id="f5cad-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f5cad-107">Description</span></span>|<span data-ttu-id="f5cad-108">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5cad-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="f5cad-109">Další informace</span><span class="sxs-lookup"><span data-stu-id="f5cad-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="f5cad-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="f5cad-110">Distinct</span></span>|<span data-ttu-id="f5cad-111">Odebere duplicitní hodnoty z kolekce.</span><span class="sxs-lookup"><span data-stu-id="f5cad-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5cad-112">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="f5cad-112">Except</span></span>|<span data-ttu-id="f5cad-113">Vrátí množinových rozdílů, což znamená elementy jednu kolekci, která nejsou uvedena v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="f5cad-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="f5cad-114">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f5cad-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5cad-115">Intersect</span><span class="sxs-lookup"><span data-stu-id="f5cad-115">Intersect</span></span>|<span data-ttu-id="f5cad-116">Vrátí průnik sady, což znamená elementy, které se zobrazují v každé dvě kolekce.</span><span class="sxs-lookup"><span data-stu-id="f5cad-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="f5cad-117">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f5cad-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5cad-118">Unie</span><span class="sxs-lookup"><span data-stu-id="f5cad-118">Union</span></span>|<span data-ttu-id="f5cad-119">Vrátí sjednocení sady, což znamená jedinečný elementy, které se zobrazují v některém z dvě kolekce.</span><span class="sxs-lookup"><span data-stu-id="f5cad-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="f5cad-120">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f5cad-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="f5cad-121">Porovnání množinové operace</span><span class="sxs-lookup"><span data-stu-id="f5cad-121">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="f5cad-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="f5cad-122">Distinct</span></span>  
 <span data-ttu-id="f5cad-123">Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metodu posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="f5cad-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="f5cad-124">Vrácený pořadí obsahuje jedinečný elementy ze vstupní pořadí.</span><span class="sxs-lookup"><span data-stu-id="f5cad-124">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="f5cad-125">![Obrázek znázorňující chování Distinct &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Odlišné")</span><span class="sxs-lookup"><span data-stu-id="f5cad-125">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="f5cad-126">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="f5cad-126">Except</span></span>  
 <span data-ttu-id="f5cad-127">Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5cad-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f5cad-128">Vrácený pořadí obsahuje pouze elementy z první vstupní pořadí, které nejsou v druhé vstupní pořadí.</span><span class="sxs-lookup"><span data-stu-id="f5cad-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="f5cad-129">![Obrázek znázorňující akce s výjimkou &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/except.png "s výjimkou")</span><span class="sxs-lookup"><span data-stu-id="f5cad-129">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="f5cad-130">Intersect</span><span class="sxs-lookup"><span data-stu-id="f5cad-130">Intersect</span></span>  
 <span data-ttu-id="f5cad-131">Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5cad-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f5cad-132">Vrácený pořadí obsahuje prvky, které jsou společné pro objekty vstupních sekvencí.</span><span class="sxs-lookup"><span data-stu-id="f5cad-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="f5cad-133">![Obrázek znázorňující průnik dvou sekvencí. ] (../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span><span class="sxs-lookup"><span data-stu-id="f5cad-133">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="f5cad-134">Unie</span><span class="sxs-lookup"><span data-stu-id="f5cad-134">Union</span></span>  
 <span data-ttu-id="f5cad-135">Následující obrázek znázorňuje sjednocovací operace na dvě sekvence znaků.</span><span class="sxs-lookup"><span data-stu-id="f5cad-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="f5cad-136">Vrácený pořadí obsahuje jedinečný prvky z obou vstupních sekvencí.</span><span class="sxs-lookup"><span data-stu-id="f5cad-136">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="f5cad-137">![Obrázek znázorňující sjednocení dvou pořadí. ] (../../../../csharp/programming-guide/concepts/linq/media/union.png "Sjednocení")</span><span class="sxs-lookup"><span data-stu-id="f5cad-137">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="f5cad-138">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="f5cad-138">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="f5cad-139">Následující příklad používá `Distinct` klauzuli v dotazu LINQ vrácení jedinečná čísla z seznam celých čísel.</span><span class="sxs-lookup"><span data-stu-id="f5cad-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 [!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f5cad-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5cad-140">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="f5cad-141">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5cad-141">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="f5cad-142">DISTINCT – klauzule</span><span class="sxs-lookup"><span data-stu-id="f5cad-142">Distinct Clause</span></span>](../../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="f5cad-143">Postupy: kombinace a porovnávání kolekcí řetězců (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5cad-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [<span data-ttu-id="f5cad-144">Postupy: hledání množinových rozdílů mezi dvěma seznamy (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5cad-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)

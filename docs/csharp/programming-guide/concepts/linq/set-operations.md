---
title: "Množinové operace (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5b546d9df8752fd7afd6e0db4525bc923a74bbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-c"></a><span data-ttu-id="7ef41-102">Množinové operace (C#)</span><span class="sxs-lookup"><span data-stu-id="7ef41-102">Set Operations (C#)</span></span>
<span data-ttu-id="7ef41-103">Množinové operace v technologii LINQ naleznete v operacích dotazu, které produkují je sada výsledků dotazu, který je založen na přítomnosti nebo absenci ekvivalentní elementů v rámci stejné nebo samostatné kolekce (nebo sady).</span><span class="sxs-lookup"><span data-stu-id="7ef41-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="7ef41-104">Operátor metody standardní dotazů, které provádět operace set jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="7ef41-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ef41-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7ef41-105">Methods</span></span>  
  
|<span data-ttu-id="7ef41-106">Název metody</span><span class="sxs-lookup"><span data-stu-id="7ef41-106">Method Name</span></span>|<span data-ttu-id="7ef41-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7ef41-107">Description</span></span>|<span data-ttu-id="7ef41-108">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7ef41-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="7ef41-109">Další informace</span><span class="sxs-lookup"><span data-stu-id="7ef41-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="7ef41-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="7ef41-110">Distinct</span></span>|<span data-ttu-id="7ef41-111">Odebere duplicitní hodnoty z kolekce.</span><span class="sxs-lookup"><span data-stu-id="7ef41-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="7ef41-112">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="7ef41-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7ef41-113">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="7ef41-113">Except</span></span>|<span data-ttu-id="7ef41-114">Vrátí množinových rozdílů, což znamená elementy jednu kolekci, která nejsou uvedena v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="7ef41-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="7ef41-115">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="7ef41-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7ef41-116">Intersect</span><span class="sxs-lookup"><span data-stu-id="7ef41-116">Intersect</span></span>|<span data-ttu-id="7ef41-117">Vrátí průnik sady, což znamená elementy, které se zobrazují v každé dvě kolekce.</span><span class="sxs-lookup"><span data-stu-id="7ef41-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="7ef41-118">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="7ef41-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7ef41-119">Unie</span><span class="sxs-lookup"><span data-stu-id="7ef41-119">Union</span></span>|<span data-ttu-id="7ef41-120">Vrátí sjednocení sady, což znamená jedinečný elementy, které se zobrazují v některém z dvě kolekce.</span><span class="sxs-lookup"><span data-stu-id="7ef41-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="7ef41-121">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="7ef41-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="7ef41-122">Porovnání množinové operace</span><span class="sxs-lookup"><span data-stu-id="7ef41-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="7ef41-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="7ef41-123">Distinct</span></span>  
 <span data-ttu-id="7ef41-124">Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metodu posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="7ef41-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="7ef41-125">Vrácený pořadí obsahuje jedinečný elementy ze vstupní pořadí.</span><span class="sxs-lookup"><span data-stu-id="7ef41-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="7ef41-126">![Obrázek znázorňující chování Distinct &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Odlišné")</span><span class="sxs-lookup"><span data-stu-id="7ef41-126">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="7ef41-127">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="7ef41-127">Except</span></span>  
 <span data-ttu-id="7ef41-128">Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ef41-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7ef41-129">Vrácený pořadí obsahuje pouze elementy z první vstupní pořadí, které nejsou v druhé vstupní pořadí.</span><span class="sxs-lookup"><span data-stu-id="7ef41-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="7ef41-130">![Obrázek znázorňující akce s výjimkou &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/except.png "s výjimkou")</span><span class="sxs-lookup"><span data-stu-id="7ef41-130">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="7ef41-131">Intersect</span><span class="sxs-lookup"><span data-stu-id="7ef41-131">Intersect</span></span>  
 <span data-ttu-id="7ef41-132">Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ef41-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7ef41-133">Vrácený pořadí obsahuje prvky, které jsou společné pro objekty vstupních sekvencí.</span><span class="sxs-lookup"><span data-stu-id="7ef41-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="7ef41-134">![Obrázek znázorňující průnik dvou sekvencí. ] (../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span><span class="sxs-lookup"><span data-stu-id="7ef41-134">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="7ef41-135">Unie</span><span class="sxs-lookup"><span data-stu-id="7ef41-135">Union</span></span>  
 <span data-ttu-id="7ef41-136">Následující obrázek znázorňuje sjednocovací operace na dvě sekvence znaků.</span><span class="sxs-lookup"><span data-stu-id="7ef41-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="7ef41-137">Vrácený pořadí obsahuje jedinečný prvky z obou vstupních sekvencí.</span><span class="sxs-lookup"><span data-stu-id="7ef41-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="7ef41-138">![Obrázek znázorňující sjednocení dvou pořadí. ] (../../../../csharp/programming-guide/concepts/linq/media/union.png "Sjednocení")</span><span class="sxs-lookup"><span data-stu-id="7ef41-138">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ef41-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ef41-139">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="7ef41-140">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="7ef41-140">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="7ef41-141">Postupy: kombinace a porovnávání kolekcí řetězců (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ef41-141">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [<span data-ttu-id="7ef41-142">Postupy: hledání množinových rozdílů mezi dvěma seznamy (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ef41-142">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)

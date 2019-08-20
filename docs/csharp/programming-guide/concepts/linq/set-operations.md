---
title: Operace set (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: cea0c0ba4dd6c7f874f69e3ec4a179248397b67d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591114"
---
# <a name="set-operations-c"></a><span data-ttu-id="fd1ab-102">Operace set (C#)</span><span class="sxs-lookup"><span data-stu-id="fd1ab-102">Set Operations (C#)</span></span>
<span data-ttu-id="fd1ab-103">Operace s nastavením v LINQ odkazují na operace dotazů, které tvoří sadu výsledků dotazu založenou na přítomnosti nebo nepřítomnosti ekvivalentních prvků v rámci stejné nebo samostatné kolekce (nebo sady).</span><span class="sxs-lookup"><span data-stu-id="fd1ab-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="fd1ab-104">Standardní metody operátoru dotazu, které provádějí operace set, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd1ab-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fd1ab-105">Methods</span></span>  
  
|<span data-ttu-id="fd1ab-106">Název metody</span><span class="sxs-lookup"><span data-stu-id="fd1ab-106">Method Name</span></span>|<span data-ttu-id="fd1ab-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fd1ab-107">Description</span></span>|<span data-ttu-id="fd1ab-108">C#Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="fd1ab-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="fd1ab-109">Další informace</span><span class="sxs-lookup"><span data-stu-id="fd1ab-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="fd1ab-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="fd1ab-110">Distinct</span></span>|<span data-ttu-id="fd1ab-111">Odebere z kolekce duplicitní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="fd1ab-112">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fd1ab-113">Výjimk</span><span class="sxs-lookup"><span data-stu-id="fd1ab-113">Except</span></span>|<span data-ttu-id="fd1ab-114">Vrátí množinu rozdílů, což znamená prvky jedné kolekce, které se nezobrazují v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="fd1ab-115">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fd1ab-116">Krývají</span><span class="sxs-lookup"><span data-stu-id="fd1ab-116">Intersect</span></span>|<span data-ttu-id="fd1ab-117">Vrátí průnik sady, což znamená prvky, které se zobrazují v každé ze dvou kolekcí.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="fd1ab-118">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fd1ab-119">Unie</span><span class="sxs-lookup"><span data-stu-id="fd1ab-119">Union</span></span>|<span data-ttu-id="fd1ab-120">Vrátí sjednocení set, což znamená jedinečné prvky, které se zobrazí v obou dvou kolekcích.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="fd1ab-121">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="fd1ab-122">Porovnání operací set</span><span class="sxs-lookup"><span data-stu-id="fd1ab-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="fd1ab-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="fd1ab-123">Distinct</span></span>  
 <span data-ttu-id="fd1ab-124">Následující ilustrace znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody v sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="fd1ab-125">Vrácená sekvence obsahuje jedinečné prvky ze vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Obrázek znázorňující chování samostatného&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a><span data-ttu-id="fd1ab-127">Výjimk</span><span class="sxs-lookup"><span data-stu-id="fd1ab-127">Except</span></span>  
 <span data-ttu-id="fd1ab-128">Následující ilustrace znázorňuje chování <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>nástroje.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fd1ab-129">Vrácená sekvence obsahuje pouze prvky z první vstupní sekvence, které nejsou ve druhé vstupní sekvenci.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="fd1ab-130">![Obrázek znázorňující akci s výjimkou&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Zobrazuje chování s výjimkou.")</span><span class="sxs-lookup"><span data-stu-id="fd1ab-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="fd1ab-131">Krývají</span><span class="sxs-lookup"><span data-stu-id="fd1ab-131">Intersect</span></span>  
 <span data-ttu-id="fd1ab-132">Následující ilustrace znázorňuje chování <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>nástroje.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fd1ab-133">Vrácená sekvence obsahuje prvky, které jsou společné pro obě vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Obrázek znázorňující průnik dvou sekvencí](./media/set-operations/intersection-two-sequences.png)  
 
### <a name="union"></a><span data-ttu-id="fd1ab-135">Unie</span><span class="sxs-lookup"><span data-stu-id="fd1ab-135">Union</span></span>  
 <span data-ttu-id="fd1ab-136">Následující ilustrace znázorňuje operaci sjednocení na dvou sekvencích znaků.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="fd1ab-137">Vrácená sekvence obsahuje jedinečné prvky z obou vstupních sekvencí.</span><span class="sxs-lookup"><span data-stu-id="fd1ab-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Obrázek znázorňující sjednocení dvou sekvencí.](./media/set-operations/union-operation-two-sequences.png)  
## <a name="see-also"></a><span data-ttu-id="fd1ab-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd1ab-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="fd1ab-140">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="fd1ab-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="fd1ab-141">Postupy: Kombinování a porovnávání kolekcí řetězců (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="fd1ab-141">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="fd1ab-142">Postupy: Najde množinu rozdílů mezi dvěma seznamy (LINQ)C#().</span><span class="sxs-lookup"><span data-stu-id="fd1ab-142">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)

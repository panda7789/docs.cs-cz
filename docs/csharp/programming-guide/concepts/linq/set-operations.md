---
title: Operace set (C#)
description: Přečtěte si o operacích set a metodách standardního operátoru dotazu, které provádějí operace Set v LINQ v jazyce C#.
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: ab2608b267113ad5d47a33e64cd9a5e21496f668
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302370"
---
# <a name="set-operations-c"></a><span data-ttu-id="8a5ec-103">Operace set (C#)</span><span class="sxs-lookup"><span data-stu-id="8a5ec-103">Set Operations (C#)</span></span>
<span data-ttu-id="8a5ec-104">Operace s nastavením v LINQ odkazují na operace dotazů, které tvoří sadu výsledků dotazu založenou na přítomnosti nebo nepřítomnosti ekvivalentních prvků v rámci stejné nebo samostatné kolekce (nebo sady).</span><span class="sxs-lookup"><span data-stu-id="8a5ec-104">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="8a5ec-105">Standardní metody operátoru dotazu, které provádějí operace set, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-105">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a5ec-106">Metody</span><span class="sxs-lookup"><span data-stu-id="8a5ec-106">Methods</span></span>  
  
|<span data-ttu-id="8a5ec-107">Název metody</span><span class="sxs-lookup"><span data-stu-id="8a5ec-107">Method Name</span></span>|<span data-ttu-id="8a5ec-108">Popis</span><span class="sxs-lookup"><span data-stu-id="8a5ec-108">Description</span></span>|<span data-ttu-id="8a5ec-109">Syntaxe výrazu dotazu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8a5ec-109">C# Query Expression Syntax</span></span>|<span data-ttu-id="8a5ec-110">Další informace</span><span class="sxs-lookup"><span data-stu-id="8a5ec-110">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="8a5ec-111">Distinct</span><span class="sxs-lookup"><span data-stu-id="8a5ec-111">Distinct</span></span>|<span data-ttu-id="8a5ec-112">Odebere z kolekce duplicitní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-112">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="8a5ec-113">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-113">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8a5ec-114">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="8a5ec-114">Except</span></span>|<span data-ttu-id="8a5ec-115">Vrátí množinu rozdílů, což znamená prvky jedné kolekce, které se nezobrazují v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-115">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="8a5ec-116">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8a5ec-117">Krývají</span><span class="sxs-lookup"><span data-stu-id="8a5ec-117">Intersect</span></span>|<span data-ttu-id="8a5ec-118">Vrátí průnik sady, což znamená prvky, které se zobrazují v každé ze dvou kolekcí.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-118">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="8a5ec-119">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8a5ec-120">Sjednocení</span><span class="sxs-lookup"><span data-stu-id="8a5ec-120">Union</span></span>|<span data-ttu-id="8a5ec-121">Vrátí sjednocení set, což znamená jedinečné prvky, které se zobrazí v obou dvou kolekcích.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-121">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="8a5ec-122">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="8a5ec-123">Porovnání operací set</span><span class="sxs-lookup"><span data-stu-id="8a5ec-123">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="8a5ec-124">Distinct</span><span class="sxs-lookup"><span data-stu-id="8a5ec-124">Distinct</span></span>  
 <span data-ttu-id="8a5ec-125">Následující příklad znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody v sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-125">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="8a5ec-126">Vrácená sekvence obsahuje jedinečné prvky ze vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-126">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Obrázek znázorňující chování odlišného&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="8a5ec-128">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="8a5ec-128">Except</span></span>  
 <span data-ttu-id="8a5ec-129">Následující příklad znázorňuje chování nástroje <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8a5ec-129">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8a5ec-130">Vrácená sekvence obsahuje pouze prvky z první vstupní sekvence, které nejsou ve druhé vstupní sekvenci.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-130">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="8a5ec-131">![Obrázek znázorňující akci s výjimkou&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Zobrazuje chování s výjimkou.")</span><span class="sxs-lookup"><span data-stu-id="8a5ec-131">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="8a5ec-132">Krývají</span><span class="sxs-lookup"><span data-stu-id="8a5ec-132">Intersect</span></span>  
 <span data-ttu-id="8a5ec-133">Následující příklad znázorňuje chování nástroje <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8a5ec-133">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8a5ec-134">Vrácená sekvence obsahuje prvky, které jsou společné pro obě vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-134">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Obrázek znázorňující průnik dvou sekvencí](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="8a5ec-136">Sjednocení</span><span class="sxs-lookup"><span data-stu-id="8a5ec-136">Union</span></span>  
 <span data-ttu-id="8a5ec-137">Následující příklad znázorňuje operaci sjednocení na dvou sekvencích znaků.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-137">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="8a5ec-138">Vrácená sekvence obsahuje jedinečné prvky z obou vstupních sekvencí.</span><span class="sxs-lookup"><span data-stu-id="8a5ec-138">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Obrázek znázorňující sjednocení dvou sekvencí.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a><span data-ttu-id="8a5ec-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a5ec-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="8a5ec-141">Přehled standardních operátorů dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="8a5ec-141">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="8a5ec-142">Postup kombinování a porovnávání kolekcí řetězců (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="8a5ec-142">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="8a5ec-143">Jak najít množinu rozdílů mezi dvěma seznamy (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="8a5ec-143">How to find the set difference between two lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)

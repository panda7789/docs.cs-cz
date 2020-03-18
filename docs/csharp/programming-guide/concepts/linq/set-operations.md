---
title: Nastavit operace (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 44a145a625b5e2e16d2469b20f8cfda1858560a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167930"
---
# <a name="set-operations-c"></a><span data-ttu-id="bba1b-102">Nastavit operace (C#)</span><span class="sxs-lookup"><span data-stu-id="bba1b-102">Set Operations (C#)</span></span>
<span data-ttu-id="bba1b-103">Nastavit operace v LINQ odkazují na operace dotazu, které vytvářejí sadu výsledků, která je založena na přítomnosti nebo nepřítomnosti ekvivalentních prvků v rámci stejné nebo samostatné kolekce (nebo sady).</span><span class="sxs-lookup"><span data-stu-id="bba1b-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="bba1b-104">Standardní metody operátoru dotazu, které provádějí operace sady, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="bba1b-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bba1b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bba1b-105">Methods</span></span>  
  
|<span data-ttu-id="bba1b-106">Název metody</span><span class="sxs-lookup"><span data-stu-id="bba1b-106">Method Name</span></span>|<span data-ttu-id="bba1b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bba1b-107">Description</span></span>|<span data-ttu-id="bba1b-108">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bba1b-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="bba1b-109">Další informace</span><span class="sxs-lookup"><span data-stu-id="bba1b-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="bba1b-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="bba1b-110">Distinct</span></span>|<span data-ttu-id="bba1b-111">Odebere duplicitní hodnoty z kolekce.</span><span class="sxs-lookup"><span data-stu-id="bba1b-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="bba1b-112">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="bba1b-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bba1b-113">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="bba1b-113">Except</span></span>|<span data-ttu-id="bba1b-114">Vrátí set rozdíl, což znamená, že prvky jedné kolekce, které se nezobrazují v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="bba1b-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="bba1b-115">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="bba1b-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bba1b-116">Protínají</span><span class="sxs-lookup"><span data-stu-id="bba1b-116">Intersect</span></span>|<span data-ttu-id="bba1b-117">Vrátí nastavený průsečík, což znamená prvky, které se zobrazí v každé ze dvou kolekcí.</span><span class="sxs-lookup"><span data-stu-id="bba1b-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="bba1b-118">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="bba1b-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bba1b-119">Sjednocení</span><span class="sxs-lookup"><span data-stu-id="bba1b-119">Union</span></span>|<span data-ttu-id="bba1b-120">Vrátí set union, což znamená jedinečné prvky, které se zobrazí v jedné ze dvou kolekcí.</span><span class="sxs-lookup"><span data-stu-id="bba1b-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="bba1b-121">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="bba1b-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="bba1b-122">Porovnání nastavených operací</span><span class="sxs-lookup"><span data-stu-id="bba1b-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="bba1b-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="bba1b-123">Distinct</span></span>  
 <span data-ttu-id="bba1b-124">Následující příklad znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody v posloupnosti znaků.</span><span class="sxs-lookup"><span data-stu-id="bba1b-124">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="bba1b-125">Vrácená sekvence obsahuje jedinečné prvky ze vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="bba1b-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Obrázek znázorňující chování odlišné&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="bba1b-127">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="bba1b-127">Except</span></span>  
 <span data-ttu-id="bba1b-128">Následující příklad znázorňuje <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>chování .</span><span class="sxs-lookup"><span data-stu-id="bba1b-128">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bba1b-129">Vrácená sekvence obsahuje pouze prvky z první vstupní sekvence, které nejsou v druhé vstupní sekvenci.</span><span class="sxs-lookup"><span data-stu-id="bba1b-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="bba1b-130">![Obrázek znázorňující akci s výjimkou&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Zobrazuje chování s výjimkou.")</span><span class="sxs-lookup"><span data-stu-id="bba1b-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="bba1b-131">Protínají</span><span class="sxs-lookup"><span data-stu-id="bba1b-131">Intersect</span></span>  
 <span data-ttu-id="bba1b-132">Následující příklad znázorňuje <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>chování .</span><span class="sxs-lookup"><span data-stu-id="bba1b-132">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bba1b-133">Vrácená sekvence obsahuje prvky, které jsou společné pro obě vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="bba1b-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Obrázek znázorňující průsečík dvou sekvencí.](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="bba1b-135">Sjednocení</span><span class="sxs-lookup"><span data-stu-id="bba1b-135">Union</span></span>  
 <span data-ttu-id="bba1b-136">Následující příklad znázorňuje operaci sjednocení na dvou sekvencích znaků.</span><span class="sxs-lookup"><span data-stu-id="bba1b-136">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="bba1b-137">Vrácená sekvence obsahuje jedinečné prvky z obou vstupních sekvencí.</span><span class="sxs-lookup"><span data-stu-id="bba1b-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Obrázek znázorňující spojení dvou sekvencí.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a><span data-ttu-id="bba1b-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="bba1b-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="bba1b-140">Standardní operátory dotazů – přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="bba1b-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="bba1b-141">Jak kombinovat a porovnávat kolekce řetězců (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="bba1b-141">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="bba1b-142">Jak najít nastavený rozdíl mezi dvěma seznamy (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="bba1b-142">How to find the set difference between two lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)

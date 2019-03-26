---
title: Množinové operace (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 9e507bbaa39bf040a8ce1564630fb5fbb8c0dbe4
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408909"
---
# <a name="set-operations-c"></a><span data-ttu-id="802d9-102">Množinové operace (C#)</span><span class="sxs-lookup"><span data-stu-id="802d9-102">Set Operations (C#)</span></span>
<span data-ttu-id="802d9-103">Množinové operace LINQ naleznete operace dotazů, které vytvářejí sadu výsledků dotazu, který je založen na přítomnosti nebo nepřítomnosti ekvivalentních prvků ve stejném nebo různém kolekcí (nebo sady).</span><span class="sxs-lookup"><span data-stu-id="802d9-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="802d9-104">Standardní metody operátoru dotazu, které provádějí operace sady jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="802d9-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="802d9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="802d9-105">Methods</span></span>  
  
|<span data-ttu-id="802d9-106">Název metody</span><span class="sxs-lookup"><span data-stu-id="802d9-106">Method Name</span></span>|<span data-ttu-id="802d9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="802d9-107">Description</span></span>|<span data-ttu-id="802d9-108">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="802d9-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="802d9-109">Další informace</span><span class="sxs-lookup"><span data-stu-id="802d9-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="802d9-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="802d9-110">Distinct</span></span>|<span data-ttu-id="802d9-111">Odebere duplicitní hodnoty z kolekce.</span><span class="sxs-lookup"><span data-stu-id="802d9-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="802d9-112">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="802d9-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="802d9-113">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="802d9-113">Except</span></span>|<span data-ttu-id="802d9-114">Vrátí množinových rozdílů, což znamená, že prvky jednu kolekci, která není uvedena v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="802d9-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="802d9-115">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="802d9-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="802d9-116">Intersect</span><span class="sxs-lookup"><span data-stu-id="802d9-116">Intersect</span></span>|<span data-ttu-id="802d9-117">Vrátí průnik set, což znamená, že prvky, které se zobrazují v každé dvě kolekce.</span><span class="sxs-lookup"><span data-stu-id="802d9-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="802d9-118">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="802d9-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="802d9-119">Unie</span><span class="sxs-lookup"><span data-stu-id="802d9-119">Union</span></span>|<span data-ttu-id="802d9-120">Vrátí sjednocení, což znamená, že jedinečných prvků, které se zobrazují v některém z dvě kolekce.</span><span class="sxs-lookup"><span data-stu-id="802d9-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="802d9-121">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="802d9-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="802d9-122">Porovnání množinové operace</span><span class="sxs-lookup"><span data-stu-id="802d9-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="802d9-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="802d9-123">Distinct</span></span>  
 <span data-ttu-id="802d9-124">Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metodu na posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="802d9-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="802d9-125">Vrácená sekvence obsahuje jedinečných prvků ze vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="802d9-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Obrázek znázorňující chování Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a><span data-ttu-id="802d9-127">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="802d9-127">Except</span></span>  
 <span data-ttu-id="802d9-128">Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="802d9-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="802d9-129">Vrácená sekvence obsahuje pouze elementy z první vstupní sekvence, které nejsou v druhé vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="802d9-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="802d9-130">![Obrázek znázorňující akce s výjimkou&#40;&#41;. ](./media/set-operations/except-behavior-graphic.png "Ukazuje chování s výjimkou.")</span><span class="sxs-lookup"><span data-stu-id="802d9-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="802d9-131">Intersect</span><span class="sxs-lookup"><span data-stu-id="802d9-131">Intersect</span></span>  
 <span data-ttu-id="802d9-132">Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="802d9-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="802d9-133">Vrácená sekvence obsahuje prvky, které jsou společné pro vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="802d9-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Obrázek znázorňující průniku množin mezi dvěma sekvencemi.](./media/set-operations/intersection-two-sequences.png)  
 
### <a name="union"></a><span data-ttu-id="802d9-135">Unie</span><span class="sxs-lookup"><span data-stu-id="802d9-135">Union</span></span>  
 <span data-ttu-id="802d9-136">Následující ilustrace znázorňuje operaci s sjednocení dvou sekvencí znaků.</span><span class="sxs-lookup"><span data-stu-id="802d9-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="802d9-137">Vrácená sekvence obsahuje jedinečných prvků z obou vstupních sekvencí.</span><span class="sxs-lookup"><span data-stu-id="802d9-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Obrázek znázorňující sjednocení množin mezi dvěma sekvencemi.](./media/set-operations/union-operation-two-sequences.png)  
## <a name="see-also"></a><span data-ttu-id="802d9-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="802d9-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="802d9-140">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="802d9-140">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="802d9-141">Postupy: Kombinace a porovnávání kolekcí řetězců (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="802d9-141">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="802d9-142">Postupy: Hledání množinových rozdílů mezi dvěma seznamy (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="802d9-142">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)

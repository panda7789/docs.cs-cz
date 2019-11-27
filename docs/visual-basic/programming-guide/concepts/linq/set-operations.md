---
title: Množinové operace
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: fe9d910415f30fe672dc702f719fdefdb9c0b3d1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350618"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="62e26-102">Operace set (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62e26-102">Set Operations (Visual Basic)</span></span>

<span data-ttu-id="62e26-103">Operace s nastavením v LINQ odkazují na operace dotazů, které tvoří sadu výsledků dotazu založenou na přítomnosti nebo nepřítomnosti ekvivalentních prvků v rámci stejné nebo samostatné kolekce (nebo sady).</span><span class="sxs-lookup"><span data-stu-id="62e26-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>

<span data-ttu-id="62e26-104">Standardní metody operátoru dotazu, které provádějí operace set, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="62e26-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="62e26-105">Metody</span><span class="sxs-lookup"><span data-stu-id="62e26-105">Methods</span></span>

|<span data-ttu-id="62e26-106">Název metody</span><span class="sxs-lookup"><span data-stu-id="62e26-106">Method Name</span></span>|<span data-ttu-id="62e26-107">Popis</span><span class="sxs-lookup"><span data-stu-id="62e26-107">Description</span></span>|<span data-ttu-id="62e26-108">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="62e26-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="62e26-109">Další informace</span><span class="sxs-lookup"><span data-stu-id="62e26-109">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="62e26-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="62e26-110">Distinct</span></span>|<span data-ttu-id="62e26-111">Odebere z kolekce duplicitní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="62e26-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|<span data-ttu-id="62e26-112">výjimk</span><span class="sxs-lookup"><span data-stu-id="62e26-112">Except</span></span>|<span data-ttu-id="62e26-113">Vrátí množinu rozdílů, což znamená prvky jedné kolekce, které se nezobrazují v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="62e26-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="62e26-114">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="62e26-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|<span data-ttu-id="62e26-115">Krývají</span><span class="sxs-lookup"><span data-stu-id="62e26-115">Intersect</span></span>|<span data-ttu-id="62e26-116">Vrátí průnik sady, což znamená prvky, které se zobrazují v každé ze dvou kolekcí.</span><span class="sxs-lookup"><span data-stu-id="62e26-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="62e26-117">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="62e26-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|<span data-ttu-id="62e26-118">Unie</span><span class="sxs-lookup"><span data-stu-id="62e26-118">Union</span></span>|<span data-ttu-id="62e26-119">Vrátí sjednocení set, což znamená jedinečné prvky, které se zobrazí v obou dvou kolekcích.</span><span class="sxs-lookup"><span data-stu-id="62e26-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="62e26-120">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="62e26-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a><span data-ttu-id="62e26-121">Porovnání operací set</span><span class="sxs-lookup"><span data-stu-id="62e26-121">Comparison of Set Operations</span></span>

### <a name="distinct"></a><span data-ttu-id="62e26-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="62e26-122">Distinct</span></span>

<span data-ttu-id="62e26-123">Následující ilustrace znázorňuje chování metody <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> v sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="62e26-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="62e26-124">Vrácená sekvence obsahuje jedinečné prvky ze vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="62e26-124">The returned sequence contains the unique elements from the input sequence.</span></span>

![Obrázek znázorňující chování samostatného&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a><span data-ttu-id="62e26-126">výjimk</span><span class="sxs-lookup"><span data-stu-id="62e26-126">Except</span></span>

<span data-ttu-id="62e26-127">Následující ilustrace znázorňuje chování <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="62e26-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="62e26-128">Vrácená sekvence obsahuje pouze prvky z první vstupní sekvence, které nejsou ve druhé vstupní sekvenci.</span><span class="sxs-lookup"><span data-stu-id="62e26-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>

<span data-ttu-id="62e26-129">![Obrázek znázorňující akci s výjimkou&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Zobrazuje chování s výjimkou.")</span><span class="sxs-lookup"><span data-stu-id="62e26-129">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>

### <a name="intersect"></a><span data-ttu-id="62e26-130">Krývají</span><span class="sxs-lookup"><span data-stu-id="62e26-130">Intersect</span></span>

<span data-ttu-id="62e26-131">Následující ilustrace znázorňuje chování <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="62e26-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="62e26-132">Vrácená sekvence obsahuje prvky, které jsou společné pro obě vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="62e26-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>

![Obrázek znázorňující průnik dvou sekvencí](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a><span data-ttu-id="62e26-134">Unie</span><span class="sxs-lookup"><span data-stu-id="62e26-134">Union</span></span>

<span data-ttu-id="62e26-135">Následující ilustrace znázorňuje operaci sjednocení na dvou sekvencích znaků.</span><span class="sxs-lookup"><span data-stu-id="62e26-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="62e26-136">Vrácená sekvence obsahuje jedinečné prvky z obou vstupních sekvencí.</span><span class="sxs-lookup"><span data-stu-id="62e26-136">The returned sequence contains the unique elements from both input sequences.</span></span>

![Obrázek znázorňující sjednocení dvou sekvencí.](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a><span data-ttu-id="62e26-138">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="62e26-138">Query Expression Syntax Example</span></span>

<span data-ttu-id="62e26-139">Následující příklad používá klauzuli `Distinct` v dotazu LINQ k vrácení jedinečných čísel ze seznamu celých čísel.</span><span class="sxs-lookup"><span data-stu-id="62e26-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a><span data-ttu-id="62e26-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62e26-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="62e26-141">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62e26-141">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="62e26-142">Klauzule Distinct</span><span class="sxs-lookup"><span data-stu-id="62e26-142">Distinct Clause</span></span>](../../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="62e26-143">Postupy: kombinování a porovnávání kolekcí řetězců (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62e26-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="62e26-144">Postupy: Vyhledání nastaveného rozdílu mezi dvěma seznamy (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62e26-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)

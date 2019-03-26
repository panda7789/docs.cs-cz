---
title: Množinové operace (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 7b8dcaaa82ac5a30c35222417245153e55a522cc
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409247"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="9778f-102">Množinové operace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9778f-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="9778f-103">Množinové operace LINQ naleznete operace dotazů, které vytvářejí sadu výsledků dotazu, který je založen na přítomnosti nebo nepřítomnosti ekvivalentních prvků ve stejném nebo různém kolekcí (nebo sady).</span><span class="sxs-lookup"><span data-stu-id="9778f-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="9778f-104">Standardní metody operátoru dotazu, které provádějí operace sady jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="9778f-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9778f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9778f-105">Methods</span></span>  
  
|<span data-ttu-id="9778f-106">Název metody</span><span class="sxs-lookup"><span data-stu-id="9778f-106">Method Name</span></span>|<span data-ttu-id="9778f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9778f-107">Description</span></span>|<span data-ttu-id="9778f-108">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9778f-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="9778f-109">Další informace</span><span class="sxs-lookup"><span data-stu-id="9778f-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="9778f-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="9778f-110">Distinct</span></span>|<span data-ttu-id="9778f-111">Odebere duplicitní hodnoty z kolekce.</span><span class="sxs-lookup"><span data-stu-id="9778f-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9778f-112">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="9778f-112">Except</span></span>|<span data-ttu-id="9778f-113">Vrátí množinových rozdílů, což znamená, že prvky jednu kolekci, která není uvedena v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="9778f-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="9778f-114">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9778f-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9778f-115">Intersect</span><span class="sxs-lookup"><span data-stu-id="9778f-115">Intersect</span></span>|<span data-ttu-id="9778f-116">Vrátí průnik set, což znamená, že prvky, které se zobrazují v každé dvě kolekce.</span><span class="sxs-lookup"><span data-stu-id="9778f-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="9778f-117">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9778f-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9778f-118">Unie</span><span class="sxs-lookup"><span data-stu-id="9778f-118">Union</span></span>|<span data-ttu-id="9778f-119">Vrátí sjednocení, což znamená, že jedinečných prvků, které se zobrazují v některém z dvě kolekce.</span><span class="sxs-lookup"><span data-stu-id="9778f-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="9778f-120">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9778f-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="9778f-121">Porovnání množinové operace</span><span class="sxs-lookup"><span data-stu-id="9778f-121">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="9778f-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="9778f-122">Distinct</span></span>  
 <span data-ttu-id="9778f-123">Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metodu na posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="9778f-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="9778f-124">Vrácená sekvence obsahuje jedinečných prvků ze vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="9778f-124">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Obrázek znázorňující chování Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a><span data-ttu-id="9778f-126">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="9778f-126">Except</span></span>  
 <span data-ttu-id="9778f-127">Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9778f-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9778f-128">Vrácená sekvence obsahuje pouze elementy z první vstupní sekvence, které nejsou v druhé vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="9778f-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="9778f-129">![Obrázek znázorňující akce s výjimkou&#40;&#41;. ](./media/set-operations/except-behavior-graphic.png "Ukazuje chování s výjimkou.")</span><span class="sxs-lookup"><span data-stu-id="9778f-129">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="9778f-130">Intersect</span><span class="sxs-lookup"><span data-stu-id="9778f-130">Intersect</span></span>  
 <span data-ttu-id="9778f-131">Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9778f-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9778f-132">Vrácená sekvence obsahuje prvky, které jsou společné pro vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="9778f-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Obrázek znázorňující průniku množin mezi dvěma sekvencemi.](./media/set-operations/intersection-two-sequences.png)    
### <a name="union"></a><span data-ttu-id="9778f-134">Unie</span><span class="sxs-lookup"><span data-stu-id="9778f-134">Union</span></span>  
 <span data-ttu-id="9778f-135">Následující ilustrace znázorňuje operaci s sjednocení dvou sekvencí znaků.</span><span class="sxs-lookup"><span data-stu-id="9778f-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="9778f-136">Vrácená sekvence obsahuje jedinečných prvků z obou vstupních sekvencí.</span><span class="sxs-lookup"><span data-stu-id="9778f-136">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Obrázek znázorňující sjednocení množin mezi dvěma sekvencemi.](./media/set-operations/union-operation-two-sequences.png)    
## <a name="query-expression-syntax-example"></a><span data-ttu-id="9778f-138">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="9778f-138">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="9778f-139">V následujícím příkladu `Distinct` klauzuli v LINQ dotaz, který vrací jedinečný čísla ze seznamu celých čísel.</span><span class="sxs-lookup"><span data-stu-id="9778f-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 [!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9778f-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9778f-140">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="9778f-141">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9778f-141">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="9778f-142">Klauzule Distinct</span><span class="sxs-lookup"><span data-stu-id="9778f-142">Distinct Clause</span></span>](../../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="9778f-143">Postupy: Kombinace a porovnávání kolekcí řetězců (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9778f-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="9778f-144">Postupy: Hledání množinových rozdílů mezi dvěma seznamy (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9778f-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)

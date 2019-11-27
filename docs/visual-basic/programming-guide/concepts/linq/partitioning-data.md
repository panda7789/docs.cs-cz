---
title: Segmentace dat
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 2ab4e27ef6d825b9100fc3c15b7a9554ae49e516
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353156"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="6d98b-102">Dělení dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d98b-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="6d98b-103">Dělení v jazyce LINQ odkazuje na operaci rozdělení vstupní sekvence do dvou oddílů bez přeuspořádání prvků a vrácení jedné z sekcí.</span><span class="sxs-lookup"><span data-stu-id="6d98b-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="6d98b-104">Následující ilustrace znázorňuje výsledky tří různých operací dělení na sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="6d98b-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="6d98b-105">První operace vrátí první tři prvky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="6d98b-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="6d98b-106">Druhá operace přeskočí první tři prvky a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="6d98b-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="6d98b-107">Třetí operace přeskočí první dva prvky v sekvenci a vrátí další tři prvky.</span><span class="sxs-lookup"><span data-stu-id="6d98b-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Obrázek, který ukazuje tři operace dělení na oddíly LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="6d98b-109">Standardní metody operátoru dotazu, které sekvence oddílů jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="6d98b-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="6d98b-110">Operátory</span><span class="sxs-lookup"><span data-stu-id="6d98b-110">Operators</span></span>  
  
|<span data-ttu-id="6d98b-111">Název operátoru</span><span class="sxs-lookup"><span data-stu-id="6d98b-111">Operator Name</span></span>|<span data-ttu-id="6d98b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6d98b-112">Description</span></span>|<span data-ttu-id="6d98b-113">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="6d98b-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="6d98b-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="6d98b-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="6d98b-115">Přeskočit</span><span class="sxs-lookup"><span data-stu-id="6d98b-115">Skip</span></span>|<span data-ttu-id="6d98b-116">Přeskočí prvky až do zadané pozice v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="6d98b-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6d98b-117">SkipWhile –</span><span class="sxs-lookup"><span data-stu-id="6d98b-117">SkipWhile</span></span>|<span data-ttu-id="6d98b-118">Přeskočí prvky založené na funkci predikátu, dokud element nesplní podmínku.</span><span class="sxs-lookup"><span data-stu-id="6d98b-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6d98b-119">Take</span><span class="sxs-lookup"><span data-stu-id="6d98b-119">Take</span></span>|<span data-ttu-id="6d98b-120">Přebírá prvky až do zadané pozice v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="6d98b-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6d98b-121">TakeWhile –</span><span class="sxs-lookup"><span data-stu-id="6d98b-121">TakeWhile</span></span>|<span data-ttu-id="6d98b-122">Převezme prvky založené na funkci predikátu, dokud element nesplní podmínku.</span><span class="sxs-lookup"><span data-stu-id="6d98b-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="6d98b-123">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="6d98b-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="6d98b-124">Přeskočit</span><span class="sxs-lookup"><span data-stu-id="6d98b-124">Skip</span></span>  
 <span data-ttu-id="6d98b-125">Následující příklad kódu používá klauzuli `Skip` v Visual Basic k přeskočení prvních čtyř řetězců v poli řetězců před vrácením zbývajících řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="6d98b-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="6d98b-126">SkipWhile –</span><span class="sxs-lookup"><span data-stu-id="6d98b-126">SkipWhile</span></span>  
 <span data-ttu-id="6d98b-127">Následující příklad kódu používá klauzuli `Skip While` v Visual Basic k přeskočení řetězce v poli, zatímco první písmeno řetězce je "a".</span><span class="sxs-lookup"><span data-stu-id="6d98b-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="6d98b-128">Zbývající řetězce v poli jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="6d98b-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="6d98b-129">Take</span><span class="sxs-lookup"><span data-stu-id="6d98b-129">Take</span></span>  
 <span data-ttu-id="6d98b-130">Následující příklad kódu používá klauzuli `Take` v Visual Basic k vrácení prvních dvou řetězců v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="6d98b-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="6d98b-131">TakeWhile –</span><span class="sxs-lookup"><span data-stu-id="6d98b-131">TakeWhile</span></span>  
 <span data-ttu-id="6d98b-132">Následující příklad kódu používá klauzuli `Take While` v Visual Basic k vrácení řetězců z pole, zatímco délka řetězce je pět nebo méně.</span><span class="sxs-lookup"><span data-stu-id="6d98b-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6d98b-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d98b-133">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="6d98b-134">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d98b-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="6d98b-135">Klauzule Skip</span><span class="sxs-lookup"><span data-stu-id="6d98b-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="6d98b-136">Klauzule Skip While</span><span class="sxs-lookup"><span data-stu-id="6d98b-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="6d98b-137">Klauzule Take</span><span class="sxs-lookup"><span data-stu-id="6d98b-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="6d98b-138">Klauzule Take While</span><span class="sxs-lookup"><span data-stu-id="6d98b-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)

---
title: Dělení dat (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 2da63a1f6b73c8592d6036a90fa374a0d4385f4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665895"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="a86a4-102">Dělení dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a86a4-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="a86a4-103">Vytváření oddílů v technologii LINQ odkazuje na operaci dělení vstupní sekvence na dva oddíly bez uspořádání prvků a vrácení jednoho z částí.</span><span class="sxs-lookup"><span data-stu-id="a86a4-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="a86a4-104">Následující obrázek znázorňuje výsledky tři různé dělení operace na sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="a86a4-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="a86a4-105">První operace vrátí první tři prvky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="a86a4-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="a86a4-106">Druhou operaci přeskočí první tři prvky a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="a86a4-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="a86a4-107">Třetí operace přeskočí první dva prvky v pořadí a vrátí následující tři elementy.</span><span class="sxs-lookup"><span data-stu-id="a86a4-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Obrázek, který ukazuje tři operace dělení LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="a86a4-109">V následující části jsou uvedeny standardní metody operátoru dotazu, které oddílu pořadí.</span><span class="sxs-lookup"><span data-stu-id="a86a4-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="a86a4-110">Operátory</span><span class="sxs-lookup"><span data-stu-id="a86a4-110">Operators</span></span>  
  
|<span data-ttu-id="a86a4-111">Název operátoru</span><span class="sxs-lookup"><span data-stu-id="a86a4-111">Operator Name</span></span>|<span data-ttu-id="a86a4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a86a4-112">Description</span></span>|<span data-ttu-id="a86a4-113">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a86a4-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="a86a4-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="a86a4-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="a86a4-115">Skip</span><span class="sxs-lookup"><span data-stu-id="a86a4-115">Skip</span></span>|<span data-ttu-id="a86a4-116">Přeskočí elementy až do zadané pozice v pořadí.</span><span class="sxs-lookup"><span data-stu-id="a86a4-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a86a4-117">SkipWhile –</span><span class="sxs-lookup"><span data-stu-id="a86a4-117">SkipWhile</span></span>|<span data-ttu-id="a86a4-118">Vynechává prvky podle funkce predikátu, dokud element nesplňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="a86a4-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a86a4-119">Take</span><span class="sxs-lookup"><span data-stu-id="a86a4-119">Take</span></span>|<span data-ttu-id="a86a4-120">Získá prvků až do zadané pozice v pořadí.</span><span class="sxs-lookup"><span data-stu-id="a86a4-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a86a4-121">TakeWhile –</span><span class="sxs-lookup"><span data-stu-id="a86a4-121">TakeWhile</span></span>|<span data-ttu-id="a86a4-122">Přijímá prvky podle funkce predikátu, dokud element nesplňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="a86a4-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="a86a4-123">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="a86a4-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="a86a4-124">Skip</span><span class="sxs-lookup"><span data-stu-id="a86a4-124">Skip</span></span>  
 <span data-ttu-id="a86a4-125">Následující příklad kódu používá `Skip` klauzule v jazyce Visual Basic mají přeskočit první čtyři řetězce v poli řetězců před vrácením zbývající řetězce v poli.</span><span class="sxs-lookup"><span data-stu-id="a86a4-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="a86a4-126">SkipWhile –</span><span class="sxs-lookup"><span data-stu-id="a86a4-126">SkipWhile</span></span>  
 <span data-ttu-id="a86a4-127">Následující příklad kódu používá `Skip While` klauzule v jazyce Visual Basic mají přeskočit řetězce v poli je první písmeno řetězce "a".</span><span class="sxs-lookup"><span data-stu-id="a86a4-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="a86a4-128">Zbývající řetězce v poli jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="a86a4-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="a86a4-129">Take</span><span class="sxs-lookup"><span data-stu-id="a86a4-129">Take</span></span>  
 <span data-ttu-id="a86a4-130">Následující příklad kódu používá `Take` klauzule v jazyce Visual Basic se vraťte na první dva řetězce v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="a86a4-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="a86a4-131">TakeWhile –</span><span class="sxs-lookup"><span data-stu-id="a86a4-131">TakeWhile</span></span>  
 <span data-ttu-id="a86a4-132">Následující příklad kódu používá `Take While` klauzuli v jazyce Visual Basic k vrácení řetězce z pole Délka řetězce je pět nebo méně.</span><span class="sxs-lookup"><span data-stu-id="a86a4-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a86a4-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a86a4-133">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="a86a4-134">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a86a4-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a86a4-135">Klauzule Skip</span><span class="sxs-lookup"><span data-stu-id="a86a4-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="a86a4-136">Klauzule Skip While</span><span class="sxs-lookup"><span data-stu-id="a86a4-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="a86a4-137">Klauzule Take</span><span class="sxs-lookup"><span data-stu-id="a86a4-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="a86a4-138">Klauzule Take While</span><span class="sxs-lookup"><span data-stu-id="a86a4-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)

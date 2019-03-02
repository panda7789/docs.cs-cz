---
title: Aggregation Operations (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: fe39c2efb5d9f24a7d9d5240b20a9ca687ed1aa9
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202181"
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="7db06-102">Aggregation Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7db06-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="7db06-103">Operace agregace vypočítá jedinou hodnotu z kolekce hodnot.</span><span class="sxs-lookup"><span data-stu-id="7db06-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="7db06-104">Příklad operace agregace je výpočet denní teplota z za měsíc denní teplotní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7db06-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="7db06-105">Následující obrázek ukazuje výsledky dvou různých agregační operace na sekvenci čísel.</span><span class="sxs-lookup"><span data-stu-id="7db06-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="7db06-106">První operace sečte čísla.</span><span class="sxs-lookup"><span data-stu-id="7db06-106">The first operation sums the numbers.</span></span> <span data-ttu-id="7db06-107">Druhou operaci vrátí maximální hodnotu v pořadí.</span><span class="sxs-lookup"><span data-stu-id="7db06-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 <span data-ttu-id="7db06-108">![Agregační operace LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span><span class="sxs-lookup"><span data-stu-id="7db06-108">![LINQ Aggregation Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span></span>  
  
 <span data-ttu-id="7db06-109">Standardní metody operátoru dotazu, které provádějí operace agregace jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="7db06-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7db06-110">Metody</span><span class="sxs-lookup"><span data-stu-id="7db06-110">Methods</span></span>  
  
|<span data-ttu-id="7db06-111">Název metody</span><span class="sxs-lookup"><span data-stu-id="7db06-111">Method Name</span></span>|<span data-ttu-id="7db06-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7db06-112">Description</span></span>|<span data-ttu-id="7db06-113">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7db06-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="7db06-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="7db06-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="7db06-115">Aggregate</span><span class="sxs-lookup"><span data-stu-id="7db06-115">Aggregate</span></span>|<span data-ttu-id="7db06-116">Provede vlastní agregační operace na hodnotách kolekce.</span><span class="sxs-lookup"><span data-stu-id="7db06-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="7db06-117">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="7db06-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7db06-118">Průměr</span><span class="sxs-lookup"><span data-stu-id="7db06-118">Average</span></span>|<span data-ttu-id="7db06-119">Vypočítá průměrnou hodnotu kolekci hodnot.</span><span class="sxs-lookup"><span data-stu-id="7db06-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7db06-120">Počet</span><span class="sxs-lookup"><span data-stu-id="7db06-120">Count</span></span>|<span data-ttu-id="7db06-121">Vrátí počet prvků v kolekci, volitelně pouze elementy, které splňují funkce predikátu.</span><span class="sxs-lookup"><span data-stu-id="7db06-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7db06-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="7db06-122">LongCount</span></span>|<span data-ttu-id="7db06-123">Vrátí počet prvků v velkou kolekci volitelně pouze elementy, které splňují funkce predikátu.</span><span class="sxs-lookup"><span data-stu-id="7db06-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7db06-124">Maximum</span><span class="sxs-lookup"><span data-stu-id="7db06-124">Max</span></span>|<span data-ttu-id="7db06-125">Určuje maximální hodnotu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7db06-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7db06-126">Minimum</span><span class="sxs-lookup"><span data-stu-id="7db06-126">Min</span></span>|<span data-ttu-id="7db06-127">Určuje minimální hodnota v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7db06-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7db06-128">Součet</span><span class="sxs-lookup"><span data-stu-id="7db06-128">Sum</span></span>|<span data-ttu-id="7db06-129">Vypočítá součet hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7db06-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="7db06-130">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="7db06-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="7db06-131">Průměr</span><span class="sxs-lookup"><span data-stu-id="7db06-131">Average</span></span>  
 <span data-ttu-id="7db06-132">Následující příklad kódu používá `Aggregate Into Average` klauzule v jazyce Visual Basic k výpočtu průměrná teplota v poli čísel, které představují teploty.</span><span class="sxs-lookup"><span data-stu-id="7db06-132">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a><span data-ttu-id="7db06-133">Počet</span><span class="sxs-lookup"><span data-stu-id="7db06-133">Count</span></span>  
 <span data-ttu-id="7db06-134">Následující příklad kódu používá `Aggregate Into Count` klauzule v jazyce Visual Basic mají spočítat počet hodnot v poli, které jsou větší než nebo rovna hodnotě 80.</span><span class="sxs-lookup"><span data-stu-id="7db06-134">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a><span data-ttu-id="7db06-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="7db06-135">LongCount</span></span>  
 <span data-ttu-id="7db06-136">Následující příklad kódu používá `Aggregate Into LongCount` klauzule počet hodnot v poli.</span><span class="sxs-lookup"><span data-stu-id="7db06-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a><span data-ttu-id="7db06-137">Maximum</span><span class="sxs-lookup"><span data-stu-id="7db06-137">Max</span></span>  
 <span data-ttu-id="7db06-138">Následující příklad kódu používá `Aggregate Into Max` klauzule a vypočítat maximální teploty v poli čísel, které představují teploty.</span><span class="sxs-lookup"><span data-stu-id="7db06-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a><span data-ttu-id="7db06-139">Minimum</span><span class="sxs-lookup"><span data-stu-id="7db06-139">Min</span></span>  
 <span data-ttu-id="7db06-140">Následující příklad kódu používá `Aggregate Into Min` klauzule a vypočítat minimální teploty v poli čísel, které představují teploty.</span><span class="sxs-lookup"><span data-stu-id="7db06-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a><span data-ttu-id="7db06-141">Součet</span><span class="sxs-lookup"><span data-stu-id="7db06-141">Sum</span></span>  
 <span data-ttu-id="7db06-142">Následující příklad kódu používá `Aggregate Into Sum` klauzule a vypočítat celkové náklady množství z pole hodnot, které představují výdaje.</span><span class="sxs-lookup"><span data-stu-id="7db06-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="7db06-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7db06-143">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="7db06-144">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7db06-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7db06-145">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="7db06-145">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="7db06-146">Postupy: Výpočet hodnot sloupce v textovém souboru CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7db06-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [<span data-ttu-id="7db06-147">Postupy: Počet, SUMA nebo průměr dat</span><span class="sxs-lookup"><span data-stu-id="7db06-147">How to: Count, Sum, or Average Data</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [<span data-ttu-id="7db06-148">Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu</span><span class="sxs-lookup"><span data-stu-id="7db06-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [<span data-ttu-id="7db06-149">Postupy: Dotaz na největší soubor či soubory v adresářovém stromu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7db06-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [<span data-ttu-id="7db06-150">Postupy: Dotaz pro celkový počet bajtů v sadě složek (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7db06-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)

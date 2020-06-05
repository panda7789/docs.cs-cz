---
title: Agregační operace
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 8e2c9698de67dc4def348a03c9d69713a6130f31
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383790"
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="61b35-102">Agregační operace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61b35-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="61b35-103">Agregační operace vypočítá jednu hodnotu z kolekce hodnot.</span><span class="sxs-lookup"><span data-stu-id="61b35-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="61b35-104">Ukázka operace agregace počítá průměrnou denní teplotu z hodnoty denních teplot v měsíci.</span><span class="sxs-lookup"><span data-stu-id="61b35-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="61b35-105">Následující ilustrace znázorňuje výsledky dvou různých agregačních operací na sekvenci čísel.</span><span class="sxs-lookup"><span data-stu-id="61b35-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="61b35-106">První operace Sečte čísla.</span><span class="sxs-lookup"><span data-stu-id="61b35-106">The first operation sums the numbers.</span></span> <span data-ttu-id="61b35-107">Druhá operace vrátí maximální hodnotu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="61b35-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 ![Ilustrace znázorňující agregační operace LINQ](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 <span data-ttu-id="61b35-109">Standardní metody operátoru dotazu, které provádějí operace agregace, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="61b35-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61b35-110">Metody</span><span class="sxs-lookup"><span data-stu-id="61b35-110">Methods</span></span>  
  
|<span data-ttu-id="61b35-111">Název metody</span><span class="sxs-lookup"><span data-stu-id="61b35-111">Method Name</span></span>|<span data-ttu-id="61b35-112">Description</span><span class="sxs-lookup"><span data-stu-id="61b35-112">Description</span></span>|<span data-ttu-id="61b35-113">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="61b35-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="61b35-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="61b35-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="61b35-115">Agregace</span><span class="sxs-lookup"><span data-stu-id="61b35-115">Aggregate</span></span>|<span data-ttu-id="61b35-116">Provede vlastní agregační operaci na hodnotách kolekce.</span><span class="sxs-lookup"><span data-stu-id="61b35-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="61b35-117">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="61b35-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61b35-118">Průměr</span><span class="sxs-lookup"><span data-stu-id="61b35-118">Average</span></span>|<span data-ttu-id="61b35-119">Vypočítá průměrnou hodnotu kolekce hodnot.</span><span class="sxs-lookup"><span data-stu-id="61b35-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61b35-120">Počet</span><span class="sxs-lookup"><span data-stu-id="61b35-120">Count</span></span>|<span data-ttu-id="61b35-121">Spočítá prvky v kolekci, volitelně pouze ty prvky, které odpovídají funkci predikátu.</span><span class="sxs-lookup"><span data-stu-id="61b35-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61b35-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="61b35-122">LongCount</span></span>|<span data-ttu-id="61b35-123">Spočítá prvky ve velké kolekci, volitelně pouze ty prvky, které odpovídají funkci predikátu.</span><span class="sxs-lookup"><span data-stu-id="61b35-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61b35-124">Maximum</span><span class="sxs-lookup"><span data-stu-id="61b35-124">Max</span></span>|<span data-ttu-id="61b35-125">Určuje maximální hodnotu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="61b35-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61b35-126">Minimum</span><span class="sxs-lookup"><span data-stu-id="61b35-126">Min</span></span>|<span data-ttu-id="61b35-127">Určuje minimální hodnotu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="61b35-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="61b35-128">Součet</span><span class="sxs-lookup"><span data-stu-id="61b35-128">Sum</span></span>|<span data-ttu-id="61b35-129">Vypočítá součet hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="61b35-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="61b35-130">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="61b35-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="61b35-131">Průměr</span><span class="sxs-lookup"><span data-stu-id="61b35-131">Average</span></span>  
 <span data-ttu-id="61b35-132">Následující příklad kódu používá `Aggregate Into Average` klauzuli v Visual Basic k výpočtu průměrné teploty v poli čísel, která představuje teploty.</span><span class="sxs-lookup"><span data-stu-id="61b35-132">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a><span data-ttu-id="61b35-133">Počet</span><span class="sxs-lookup"><span data-stu-id="61b35-133">Count</span></span>  
 <span data-ttu-id="61b35-134">Následující příklad kódu používá `Aggregate Into Count` klauzuli v Visual Basic k určení počtu hodnot v poli, které jsou větší nebo rovno 80.</span><span class="sxs-lookup"><span data-stu-id="61b35-134">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a><span data-ttu-id="61b35-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="61b35-135">LongCount</span></span>  
 <span data-ttu-id="61b35-136">Následující příklad kódu používá `Aggregate Into LongCount` klauzuli pro počítání počtu hodnot v poli.</span><span class="sxs-lookup"><span data-stu-id="61b35-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a><span data-ttu-id="61b35-137">Maximum</span><span class="sxs-lookup"><span data-stu-id="61b35-137">Max</span></span>  
 <span data-ttu-id="61b35-138">Následující příklad kódu používá `Aggregate Into Max` klauzuli pro výpočet maximální teploty v poli čísel, která představuje teploty.</span><span class="sxs-lookup"><span data-stu-id="61b35-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a><span data-ttu-id="61b35-139">Minimum</span><span class="sxs-lookup"><span data-stu-id="61b35-139">Min</span></span>  
 <span data-ttu-id="61b35-140">Následující příklad kódu používá `Aggregate Into Min` klauzuli pro výpočet minimální teploty v poli čísel, která představuje teploty.</span><span class="sxs-lookup"><span data-stu-id="61b35-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a><span data-ttu-id="61b35-141">Součet</span><span class="sxs-lookup"><span data-stu-id="61b35-141">Sum</span></span>  
 <span data-ttu-id="61b35-142">Následující příklad kódu používá `Aggregate Into Sum` klauzuli pro výpočet celkové částky výdajů z pole hodnot, které reprezentují výdaje.</span><span class="sxs-lookup"><span data-stu-id="61b35-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="61b35-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="61b35-143">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="61b35-144">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61b35-144">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="61b35-145">Aggregate – klauzule</span><span class="sxs-lookup"><span data-stu-id="61b35-145">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="61b35-146">Postupy: výpočet hodnot sloupce v textovém souboru CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61b35-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [<span data-ttu-id="61b35-147">Postupy: počítání, suma nebo průměr dat</span><span class="sxs-lookup"><span data-stu-id="61b35-147">How to: Count, Sum, or Average Data</span></span>](../../language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [<span data-ttu-id="61b35-148">Postupy: hledání minimální nebo maximální hodnoty ve výsledku dotazu</span><span class="sxs-lookup"><span data-stu-id="61b35-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [<span data-ttu-id="61b35-149">Postupy: vytvoření dotazu na největší soubor nebo soubory ve stromu adresářů (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61b35-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [<span data-ttu-id="61b35-150">Postupy: vytvoření dotazu na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61b35-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)

---
title: "Agregační operace (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d4b07eeb1d09d7db0f75d96629c816f66dbb128
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="41ab5-102">Agregační operace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41ab5-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="41ab5-103">Agregační operace vypočítá jednu hodnotu z kolekce hodnot.</span><span class="sxs-lookup"><span data-stu-id="41ab5-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="41ab5-104">Příklad operace agregace je výpočet průměrné denní teploty z měsíc za denní hodnoty teploty.</span><span class="sxs-lookup"><span data-stu-id="41ab5-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="41ab5-105">Následující obrázek znázorňuje výsledky dvě jiného agregačního operací na sekvenci čísel.</span><span class="sxs-lookup"><span data-stu-id="41ab5-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="41ab5-106">První operace sčítá čísla.</span><span class="sxs-lookup"><span data-stu-id="41ab5-106">The first operation sums the numbers.</span></span> <span data-ttu-id="41ab5-107">Druhá operace vrátí maximální hodnotu v pořadí.</span><span class="sxs-lookup"><span data-stu-id="41ab5-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 <span data-ttu-id="41ab5-108">![Agregační operace LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span><span class="sxs-lookup"><span data-stu-id="41ab5-108">![LINQ Aggregation Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span></span>  
  
 <span data-ttu-id="41ab5-109">Metody operátor standardní dotazů, které provádí operace agregace jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="41ab5-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41ab5-110">Metody</span><span class="sxs-lookup"><span data-stu-id="41ab5-110">Methods</span></span>  
  
|<span data-ttu-id="41ab5-111">Název metody</span><span class="sxs-lookup"><span data-stu-id="41ab5-111">Method Name</span></span>|<span data-ttu-id="41ab5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="41ab5-112">Description</span></span>|<span data-ttu-id="41ab5-113">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="41ab5-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="41ab5-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="41ab5-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="41ab5-115">Aggregate</span><span class="sxs-lookup"><span data-stu-id="41ab5-115">Aggregate</span></span>|<span data-ttu-id="41ab5-116">Provede vlastní agregační operace na hodnoty z kolekce.</span><span class="sxs-lookup"><span data-stu-id="41ab5-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="41ab5-117">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="41ab5-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="41ab5-118">Průměr</span><span class="sxs-lookup"><span data-stu-id="41ab5-118">Average</span></span>|<span data-ttu-id="41ab5-119">Vypočítá průměrnou hodnotu kolekci hodnot.</span><span class="sxs-lookup"><span data-stu-id="41ab5-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="41ab5-120">Počet</span><span class="sxs-lookup"><span data-stu-id="41ab5-120">Count</span></span>|<span data-ttu-id="41ab5-121">Spočítá počet elementů v kolekci, volitelně pouze ty prvky, které odpovídají funkce predikátu.</span><span class="sxs-lookup"><span data-stu-id="41ab5-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="41ab5-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="41ab5-122">LongCount</span></span>|<span data-ttu-id="41ab5-123">Spočítá počet elementů v kolekci velké volitelně pouze ty prvky, které odpovídají funkce predikátu.</span><span class="sxs-lookup"><span data-stu-id="41ab5-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="41ab5-124">maximální počet</span><span class="sxs-lookup"><span data-stu-id="41ab5-124">Max</span></span>|<span data-ttu-id="41ab5-125">Určuje maximální hodnotu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="41ab5-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="41ab5-126">Min.</span><span class="sxs-lookup"><span data-stu-id="41ab5-126">Min</span></span>|<span data-ttu-id="41ab5-127">Určuje minimální hodnotu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="41ab5-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="41ab5-128">Součet</span><span class="sxs-lookup"><span data-stu-id="41ab5-128">Sum</span></span>|<span data-ttu-id="41ab5-129">Vypočítá součet hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="41ab5-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="41ab5-130">Příklady syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="41ab5-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="41ab5-131">Průměr</span><span class="sxs-lookup"><span data-stu-id="41ab5-131">Average</span></span>  
 <span data-ttu-id="41ab5-132">Následující příklad kódu používá `Aggregate Into Average` klauzuli v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vypočítat průměrnou teplotu v pole čísla, která představují teploty.</span><span class="sxs-lookup"><span data-stu-id="41ab5-132">The following code example uses the `Aggregate Into Average` clause in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_1.vb)]  
  
### <a name="count"></a><span data-ttu-id="41ab5-133">Počet</span><span class="sxs-lookup"><span data-stu-id="41ab5-133">Count</span></span>  
 <span data-ttu-id="41ab5-134">Následující příklad kódu používá `Aggregate Into Count` klauzuli v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] můžete zjistit, kolik hodnot v pole, které jsou větší než nebo rovna hodnotě 80.</span><span class="sxs-lookup"><span data-stu-id="41ab5-134">The following code example uses the `Aggregate Into Count` clause in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_2.vb)]  
  
### <a name="longcount"></a><span data-ttu-id="41ab5-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="41ab5-135">LongCount</span></span>  
 <span data-ttu-id="41ab5-136">Následující příklad kódu používá `Aggregate Into LongCount` klauzule určený počet hodnot v matici.</span><span class="sxs-lookup"><span data-stu-id="41ab5-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_3.vb)]  
  
### <a name="max"></a><span data-ttu-id="41ab5-137">maximální počet</span><span class="sxs-lookup"><span data-stu-id="41ab5-137">Max</span></span>  
 <span data-ttu-id="41ab5-138">Následující příklad kódu používá `Aggregate Into Max` klauzule vypočítat maximální teploty v pole čísla, která představují teploty.</span><span class="sxs-lookup"><span data-stu-id="41ab5-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_4.vb)]  
  
### <a name="min"></a><span data-ttu-id="41ab5-139">Min.</span><span class="sxs-lookup"><span data-stu-id="41ab5-139">Min</span></span>  
 <span data-ttu-id="41ab5-140">Následující příklad kódu používá `Aggregate Into Min` klauzule k výpočtu minimální teploty v pole čísla, která představují teploty.</span><span class="sxs-lookup"><span data-stu-id="41ab5-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_5.vb)]  
  
### <a name="sum"></a><span data-ttu-id="41ab5-141">Součet</span><span class="sxs-lookup"><span data-stu-id="41ab5-141">Sum</span></span>  
 <span data-ttu-id="41ab5-142">Následující příklad kódu používá `Aggregate Into Sum` klauzule k výpočtu velikosti celkové náklady z pole hodnot, které představují výdaje.</span><span class="sxs-lookup"><span data-stu-id="41ab5-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="41ab5-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="41ab5-143">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="41ab5-144">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41ab5-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="41ab5-145">AGGREGATE – klauzule</span><span class="sxs-lookup"><span data-stu-id="41ab5-145">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="41ab5-146">Postupy: výpočet hodnot sloupce v textovém souboru CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41ab5-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 [<span data-ttu-id="41ab5-147">Postupy: počet, SUMA nebo průměr dat</span><span class="sxs-lookup"><span data-stu-id="41ab5-147">How to: Count, Sum, or Average Data</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)  
 [<span data-ttu-id="41ab5-148">Postupy: hledání minimální nebo maximální hodnoty ve výsledku dotazu</span><span class="sxs-lookup"><span data-stu-id="41ab5-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
 [<span data-ttu-id="41ab5-149">Postupy: dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41ab5-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 [<span data-ttu-id="41ab5-150">Postupy: dotaz na celkový počet bajtů v sadě složek (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41ab5-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)

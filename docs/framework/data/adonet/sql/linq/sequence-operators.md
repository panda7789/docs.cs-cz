---
title: Pořadí operátory
ms.date: 03/30/2017
ms.assetid: 4d332d32-3806-4451-b7af-25af269194ae
ms.openlocfilehash: 01807e48c06bce1d451961bb6204d1f8e49d53f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360284"
---
# <a name="sequence-operators"></a><span data-ttu-id="5045c-102">Pořadí operátory</span><span class="sxs-lookup"><span data-stu-id="5045c-102">Sequence Operators</span></span>
<span data-ttu-id="5045c-103">Obecně řečeno [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje operátory pořadí, které mají jednu nebo více následujících vlastností:</span><span class="sxs-lookup"><span data-stu-id="5045c-103">Generally speaking, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not support sequence operators that have one or more of the following qualities:</span></span>  
  
-   <span data-ttu-id="5045c-104">Trvat lambda s parametrem index.</span><span class="sxs-lookup"><span data-stu-id="5045c-104">Take a lambda with an index parameter.</span></span>  
  
-   <span data-ttu-id="5045c-105">Spoléhají na vlastnosti po sobě jdoucích řádků, jako je třeba <xref:System.Linq.Queryable.TakeWhile%2A>.</span><span class="sxs-lookup"><span data-stu-id="5045c-105">Rely on the properties of sequential rows, such as <xref:System.Linq.Queryable.TakeWhile%2A>.</span></span>  
  
-   <span data-ttu-id="5045c-106">Spoléhají na libovolný implementace CLR, jako je třeba <xref:System.Collections.Generic.IComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="5045c-106">Rely on an arbitrary CLR implementation, such as <xref:System.Collections.Generic.IComparer%601>.</span></span>  
  
|<span data-ttu-id="5045c-107">Příklady nepodporované</span><span class="sxs-lookup"><span data-stu-id="5045c-107">Examples of Unsupported</span></span>|  
|-----------------------------|  
|<xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.TakeWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.TakeWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.SkipWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.SkipWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.GroupBy%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.GroupBy%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2CSystem.Collections.Generic.IEnumerable%7B%60%602%7D%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Reverse%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%600%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.ElementAt%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Range%28System.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Repeat%60%601%28%60%600%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Contains%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%600%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Aggregate%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%600%2C%60%600%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Aggregate%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%601%2CSystem.Func%7B%60%601%2C%60%600%2C%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Aggregate%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%601%2CSystem.Func%7B%60%601%2C%60%600%2C%60%601%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.SequenceEqual%2A?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="5045c-108">Rozdíl oproti rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="5045c-108">Differences from .NET</span></span>  
 <span data-ttu-id="5045c-109">Všechny podporované pracovní operátory pořadí podle očekávání v common language runtime (CLR) s výjimkou `Average`.</span><span class="sxs-lookup"><span data-stu-id="5045c-109">All supported sequence operators work as expected in the common language runtime (CLR) except for `Average`.</span></span> <span data-ttu-id="5045c-110">`Average` Vrátí hodnotu stejného typu jako typ se průměr, zatímco v modulu CLR `Average` vždy vrátí hodnotu buď <xref:System.Double> nebo <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="5045c-110">`Average` returns a value of the same type as the type being averaged, whereas in the CLR `Average` always returns either a <xref:System.Double> or a <xref:System.Decimal>.</span></span> <span data-ttu-id="5045c-111">Argument zdroje je explicitně přetypování dvojité / decimal nebo selektor vrhá dvojité / decimal, výsledná SQL bude mít i takové převod a výsledkem bude podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="5045c-111">If the source argument is explicitly cast to double / decimal or the selector casts to double / decimal, the resulting SQL will also have such a conversion and the result will be as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5045c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="5045c-112">See Also</span></span>  
 [<span data-ttu-id="5045c-113">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="5045c-113">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)

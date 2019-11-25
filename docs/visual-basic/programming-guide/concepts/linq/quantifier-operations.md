---
title: Operace kvantifikátoru
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: f5b98ec09405ca4b8c715dc7da342e66a5d434d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346585"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="ff5c6-102">Quantifier Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff5c6-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="ff5c6-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span><span class="sxs-lookup"><span data-stu-id="ff5c6-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="ff5c6-104">The following illustration depicts two different quantifier operations on two different source sequences.</span><span class="sxs-lookup"><span data-stu-id="ff5c6-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="ff5c6-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span><span class="sxs-lookup"><span data-stu-id="ff5c6-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="ff5c6-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span><span class="sxs-lookup"><span data-stu-id="ff5c6-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ Quantifier Operations](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="ff5c6-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span><span class="sxs-lookup"><span data-stu-id="ff5c6-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ff5c6-109">Metody</span><span class="sxs-lookup"><span data-stu-id="ff5c6-109">Methods</span></span>  
  
|<span data-ttu-id="ff5c6-110">Method Name</span><span class="sxs-lookup"><span data-stu-id="ff5c6-110">Method Name</span></span>|<span data-ttu-id="ff5c6-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ff5c6-111">Description</span></span>|<span data-ttu-id="ff5c6-112">Visual Basic Query Expression Syntax</span><span class="sxs-lookup"><span data-stu-id="ff5c6-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="ff5c6-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="ff5c6-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="ff5c6-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="ff5c6-114">All</span></span>|<span data-ttu-id="ff5c6-115">Determines whether all the elements in a sequence satisfy a condition.</span><span class="sxs-lookup"><span data-stu-id="ff5c6-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ff5c6-116">Any</span><span class="sxs-lookup"><span data-stu-id="ff5c6-116">Any</span></span>|<span data-ttu-id="ff5c6-117">Determines whether any elements in a sequence satisfy a condition.</span><span class="sxs-lookup"><span data-stu-id="ff5c6-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ff5c6-118">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="ff5c6-118">Contains</span></span>|<span data-ttu-id="ff5c6-119">Determines whether a sequence contains a specified element.</span><span class="sxs-lookup"><span data-stu-id="ff5c6-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="ff5c6-120">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="ff5c6-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ff5c6-121">Query Expression Syntax Examples</span><span class="sxs-lookup"><span data-stu-id="ff5c6-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="ff5c6-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span><span class="sxs-lookup"><span data-stu-id="ff5c6-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="ff5c6-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span><span class="sxs-lookup"><span data-stu-id="ff5c6-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="ff5c6-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span><span class="sxs-lookup"><span data-stu-id="ff5c6-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ff5c6-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff5c6-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ff5c6-126">Standard Query Operators Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff5c6-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="ff5c6-127">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="ff5c6-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="ff5c6-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff5c6-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

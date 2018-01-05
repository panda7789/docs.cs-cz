---
title: "Příklady výrazů dotazu (LINQ na DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d959d28f50cef7820702ae535dcc3307e59cf080
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="query-expression-examples-linq-to-dataset"></a><span data-ttu-id="52dd2-102">Příklady výrazů dotazu (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="52dd2-102">Query Expression Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="52dd2-103">Tato část obsahuje [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programování příklady v syntaxe výrazu dotazu, které používají standardní operátory dotazu.</span><span class="sxs-lookup"><span data-stu-id="52dd2-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples in query expression syntax that use the standard query operators.</span></span> <span data-ttu-id="52dd2-104"><xref:System.Data.DataSet> Použít v těchto příkladech je vyplněný pomocí `FillDataSet` metoda, která je určena v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="52dd2-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="52dd2-105">Další informace najdete v tématu [standardní přehled operátory dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="52dd2-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52dd2-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="52dd2-106">In This Section</span></span>  
 [<span data-ttu-id="52dd2-107">Projekce</span><span class="sxs-lookup"><span data-stu-id="52dd2-107">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
 <span data-ttu-id="52dd2-108">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Select%2A> a <xref:System.Linq.Enumerable.SelectMany%2A> metody pro dotazování <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="52dd2-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="52dd2-109">Omezení</span><span class="sxs-lookup"><span data-stu-id="52dd2-109">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 <span data-ttu-id="52dd2-110">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Where%2A> metodu pro dotaz <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="52dd2-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="52dd2-111">Segmentace</span><span class="sxs-lookup"><span data-stu-id="52dd2-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
 <span data-ttu-id="52dd2-112">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> metody pro dotazování <xref:System.Data.DataSet> a rozdělit na oddíly výsledky.</span><span class="sxs-lookup"><span data-stu-id="52dd2-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="52dd2-113">Řazení</span><span class="sxs-lookup"><span data-stu-id="52dd2-113">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="52dd2-114">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, a <xref:System.Linq.Enumerable.ThenByDescending%2A> metody pro dotazování <xref:System.Data.DataSet> a řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="52dd2-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="52dd2-115">Operátory elementů</span><span class="sxs-lookup"><span data-stu-id="52dd2-115">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
 <span data-ttu-id="52dd2-116">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.First%2A> a <xref:System.Linq.Enumerable.ElementAt%2A> metod k získání <xref:System.Data.DataRow> elementy z <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="52dd2-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="52dd2-117">Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="52dd2-117">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="52dd2-118">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Sum%2A> metody pro dotazování <xref:System.Data.DataSet> a agregovat data.</span><span class="sxs-lookup"><span data-stu-id="52dd2-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="52dd2-119">Operátory spojení</span><span class="sxs-lookup"><span data-stu-id="52dd2-119">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
 <span data-ttu-id="52dd2-120">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.GroupJoin%2A> a <xref:System.Linq.Enumerable.Join%2A> metody pro dotazování <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="52dd2-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52dd2-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="52dd2-121">See Also</span></span>  
 [<span data-ttu-id="52dd2-122">Příklady dotazů založených na metodách</span><span class="sxs-lookup"><span data-stu-id="52dd2-122">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 [<span data-ttu-id="52dd2-123">Příklady operátorů specifických pro datovou sadu</span><span class="sxs-lookup"><span data-stu-id="52dd2-123">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 [<span data-ttu-id="52dd2-124">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="52dd2-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)

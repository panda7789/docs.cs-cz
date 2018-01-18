---
title: "Příklady dotazů – metoda (LINQ na DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1c34420d567e030eb681dbe90a4154e7b709daf7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-examples-linq-to-dataset"></a><span data-ttu-id="4a593-102">Příklady dotazů – metoda (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="4a593-102">Method-Based Query Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="4a593-103">Tato část obsahuje [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programování příklady v syntaxe dotazu na základě metod, které používají standardní operátory dotazu.</span><span class="sxs-lookup"><span data-stu-id="4a593-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples in method-based query syntax that use the standard query operators.</span></span> <span data-ttu-id="4a593-104"><xref:System.Data.DataSet> Použít v těchto příkladech je vyplněný pomocí `FillDataSet` metoda, která je určena v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="4a593-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="4a593-105">Další informace najdete v tématu [standardní přehled operátory dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="4a593-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4a593-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4a593-106">In This Section</span></span>  
 [<span data-ttu-id="4a593-107">Projekce</span><span class="sxs-lookup"><span data-stu-id="4a593-107">Projection</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
 <span data-ttu-id="4a593-108">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Select%2A> a <xref:System.Linq.Enumerable.SelectMany%2A> metody pro dotazování <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="4a593-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="4a593-109">Segmentace</span><span class="sxs-lookup"><span data-stu-id="4a593-109">Partitioning</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
 <span data-ttu-id="4a593-110">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> metody pro dotazování <xref:System.Data.DataSet> a rozdělit na oddíly výsledky.</span><span class="sxs-lookup"><span data-stu-id="4a593-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="4a593-111">Řazení</span><span class="sxs-lookup"><span data-stu-id="4a593-111">Ordering</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="4a593-112">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, a <xref:System.Linq.Enumerable.ThenByDescending%2A> metody pro dotazování <xref:System.Data.DataSet> a řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="4a593-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="4a593-113">Množinové operátory</span><span class="sxs-lookup"><span data-stu-id="4a593-113">Set Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
 <span data-ttu-id="4a593-114">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, a <xref:System.Linq.Enumerable.Union%2A> operátory provádět operace porovnání hodnota založená na sady řádků data.</span><span class="sxs-lookup"><span data-stu-id="4a593-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.</span></span>  
  
 [<span data-ttu-id="4a593-115">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="4a593-115">Conversion Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
 <span data-ttu-id="4a593-116">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, a <xref:System.Linq.Enumerable.ToList%2A> metody okamžitě provést výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="4a593-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 [<span data-ttu-id="4a593-117">Operátory elementů</span><span class="sxs-lookup"><span data-stu-id="4a593-117">Element Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
 <span data-ttu-id="4a593-118">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.First%2A> a <xref:System.Linq.Enumerable.ElementAt%2A> metod k získání <xref:System.Data.DataRow> elementy z <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="4a593-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="4a593-119">Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="4a593-119">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="4a593-120">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Sum%2A> metody pro dotazování <xref:System.Data.DataSet> a agregovat data.</span><span class="sxs-lookup"><span data-stu-id="4a593-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="4a593-121">Spojení</span><span class="sxs-lookup"><span data-stu-id="4a593-121">Join</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
 <span data-ttu-id="4a593-122">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.GroupJoin%2A> a <xref:System.Linq.Enumerable.Join%2A> metody pro dotazování <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="4a593-122">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a593-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a593-123">See Also</span></span>  
 [<span data-ttu-id="4a593-124">Příklady výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="4a593-124">Query Expression Examples</span></span>](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 [<span data-ttu-id="4a593-125">Příklady operátorů specifických pro datovou sadu</span><span class="sxs-lookup"><span data-stu-id="4a593-125">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 [<span data-ttu-id="4a593-126">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="4a593-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)

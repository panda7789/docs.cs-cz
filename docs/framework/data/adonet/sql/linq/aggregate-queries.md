---
title: "Agregační dotazy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d4aa6c0a9103bc4a906ecdfb51a55069e6b8b790
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="aggregate-queries"></a><span data-ttu-id="f39f8-102">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="f39f8-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f39f8-103">podporuje `Average`, `Count`, `Max`, `Min`, a `Sum` agregovat operátory.</span><span class="sxs-lookup"><span data-stu-id="f39f8-103"> supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="f39f8-104">Poznámka: následující vlastnosti agregační operátorů v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="f39f8-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="f39f8-105">Agregační dotazy jsou spustit okamžitě.</span><span class="sxs-lookup"><span data-stu-id="f39f8-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="f39f8-106">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="f39f8-106">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
-   <span data-ttu-id="f39f8-107">Agregační dotazy obvykle vracet číslo místo kolekce.</span><span class="sxs-lookup"><span data-stu-id="f39f8-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="f39f8-108">Další informace najdete v tématu [agregační operace](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span><span class="sxs-lookup"><span data-stu-id="f39f8-108">For more information, see [Aggregation Operations](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span></span>  
  
-   <span data-ttu-id="f39f8-109">Nelze volat agregace proti anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="f39f8-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="f39f8-110">Příklady v následujících tématech jsou odvozeny od ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="f39f8-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="f39f8-111">Další informace najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="f39f8-111">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f39f8-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f39f8-112">In This Section</span></span>  
 [<span data-ttu-id="f39f8-113">Vrácení průměrné hodnoty z číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="f39f8-113">Return the Average Value From a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="f39f8-114">Ukazuje, jak používat <xref:System.Linq.Enumerable.Average%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="f39f8-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="f39f8-115">Počet elementů v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="f39f8-115">Count the Number of Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="f39f8-116">Ukazuje, jak používat <xref:System.Linq.Enumerable.Count%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="f39f8-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="f39f8-117">Nalezení maximální hodnoty v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="f39f8-117">Find the Maximum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="f39f8-118">Ukazuje, jak používat <xref:System.Linq.Enumerable.Max%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="f39f8-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="f39f8-119">Nalezení minimální hodnoty v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="f39f8-119">Find the Minimum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="f39f8-120">Ukazuje, jak používat <xref:System.Linq.Enumerable.Min%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="f39f8-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="f39f8-121">Nalezení součtu hodnot v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="f39f8-121">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="f39f8-122">Ukazuje, jak používat <xref:System.Linq.Enumerable.Sum%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="f39f8-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f39f8-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f39f8-123">Related Sections</span></span>  
 [<span data-ttu-id="f39f8-124">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="f39f8-124">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="f39f8-125">Obsahuje odkazy na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy v jazyce Visual Basic a C#.</span><span class="sxs-lookup"><span data-stu-id="f39f8-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="f39f8-126">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="f39f8-126">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="f39f8-127">Obsahuje odkazy na témata, které vysvětlují koncepty návrhu [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f39f8-127">Provides links to topics that explain concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="f39f8-128">Úvod do dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="f39f8-128">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="f39f8-129">Vysvětluje, jak dotazy [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f39f8-129">Explains how queries work in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>

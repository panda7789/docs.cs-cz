---
title: Agregační dotazy
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 8defefb39974bea150fed84b0e7404b43882c41c
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634739"
---
# <a name="aggregate-queries"></a><span data-ttu-id="0244d-102">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="0244d-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0244d-103">podporuje agregační operátory `Average`, `Count`, `Max`, `Min`a `Sum`.</span><span class="sxs-lookup"><span data-stu-id="0244d-103">supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="0244d-104">Všimněte si následujících vlastností agregačních operátorů v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="0244d-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="0244d-105">Agregované dotazy jsou spouštěny okamžitě.</span><span class="sxs-lookup"><span data-stu-id="0244d-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="0244d-106">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="0244d-106">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
- <span data-ttu-id="0244d-107">Agregační dotazy obvykle vracejí číslo namísto kolekce.</span><span class="sxs-lookup"><span data-stu-id="0244d-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="0244d-108">Další informace najdete v tématu [agregační operace](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="0244d-108">For more information, see [Aggregation Operations](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span></span>  
  
- <span data-ttu-id="0244d-109">Agregace nelze volat proti anonymním typům.</span><span class="sxs-lookup"><span data-stu-id="0244d-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="0244d-110">Příklady v následujících tématech jsou odvozeny z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="0244d-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="0244d-111">Další informace najdete v tématu [stažení ukázkových databází](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="0244d-111">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0244d-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0244d-112">In This Section</span></span>  
 [<span data-ttu-id="0244d-113">Vrácení průměrné hodnoty z číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="0244d-113">Return the Average Value From a Numeric Sequence</span></span>](return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="0244d-114">Ukazuje, jak použít operátor <xref:System.Linq.Enumerable.Average%2A>.</span><span class="sxs-lookup"><span data-stu-id="0244d-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="0244d-115">Počet elementů v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="0244d-115">Count the Number of Elements in a Sequence</span></span>](count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="0244d-116">Ukazuje, jak použít operátor <xref:System.Linq.Enumerable.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="0244d-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="0244d-117">Nalezení maximální hodnoty v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="0244d-117">Find the Maximum Value in a Numeric Sequence</span></span>](find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="0244d-118">Ukazuje, jak použít operátor <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="0244d-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="0244d-119">Nalezení minimální hodnoty v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="0244d-119">Find the Minimum Value in a Numeric Sequence</span></span>](find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="0244d-120">Ukazuje, jak použít operátor <xref:System.Linq.Enumerable.Min%2A>.</span><span class="sxs-lookup"><span data-stu-id="0244d-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="0244d-121">Nalezení součtu hodnot v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="0244d-121">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="0244d-122">Ukazuje, jak použít operátor <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="0244d-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0244d-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0244d-123">Related Sections</span></span>  
 [<span data-ttu-id="0244d-124">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="0244d-124">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="0244d-125">Obsahuje odkazy na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy v Visual Basic a C#.</span><span class="sxs-lookup"><span data-stu-id="0244d-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="0244d-126">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="0244d-126">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="0244d-127">Obsahuje odkazy na témata, která vysvětlují koncepty pro návrh dotazů LINQ v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0244d-127">Provides links to topics that explain concepts for designing LINQ queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="0244d-128">Úvod do dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="0244d-128">Introduction to LINQ Queries (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="0244d-129">Vysvětluje, jak dotazy fungují v LINQ.</span><span class="sxs-lookup"><span data-stu-id="0244d-129">Explains how queries work in LINQ.</span></span>

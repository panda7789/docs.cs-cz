---
title: Agregační dotazy
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: b7b38306903313825056c02fc3c3fb8c98e07e17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964125"
---
# <a name="aggregate-queries"></a><span data-ttu-id="a8377-102">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="a8377-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a8377-103">`Count` `Max` podporujeoperátory`Min`Aggregate ,,`Sum` , a. `Average`</span><span class="sxs-lookup"><span data-stu-id="a8377-103">supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="a8377-104">Všimněte si následujících vlastností agregačních operátorů [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]v:</span><span class="sxs-lookup"><span data-stu-id="a8377-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="a8377-105">Agregované dotazy jsou spouštěny okamžitě.</span><span class="sxs-lookup"><span data-stu-id="a8377-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="a8377-106">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="a8377-106">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
- <span data-ttu-id="a8377-107">Agregační dotazy obvykle vracejí číslo namísto kolekce.</span><span class="sxs-lookup"><span data-stu-id="a8377-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="a8377-108">Další informace najdete v tématu [agregační operace](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="a8377-108">For more information, see [Aggregation Operations](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span></span>  
  
- <span data-ttu-id="a8377-109">Agregace nelze volat proti anonymním typům.</span><span class="sxs-lookup"><span data-stu-id="a8377-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="a8377-110">Příklady v následujících tématech jsou odvozeny z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="a8377-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="a8377-111">Další informace najdete v tématu [stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a8377-111">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8377-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a8377-112">In This Section</span></span>  
 [<span data-ttu-id="a8377-113">Vrácení průměrné hodnoty z číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="a8377-113">Return the Average Value From a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="a8377-114">Ukazuje, jak použít <xref:System.Linq.Enumerable.Average%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="a8377-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="a8377-115">Počet elementů v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="a8377-115">Count the Number of Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="a8377-116">Ukazuje, jak použít <xref:System.Linq.Enumerable.Count%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="a8377-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="a8377-117">Nalezení maximální hodnoty v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="a8377-117">Find the Maximum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="a8377-118">Ukazuje, jak použít <xref:System.Linq.Enumerable.Max%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="a8377-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="a8377-119">Nalezení minimální hodnoty v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="a8377-119">Find the Minimum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="a8377-120">Ukazuje, jak použít <xref:System.Linq.Enumerable.Min%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="a8377-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="a8377-121">Nalezení součtu hodnot v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="a8377-121">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="a8377-122">Ukazuje, jak použít <xref:System.Linq.Enumerable.Sum%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="a8377-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8377-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a8377-123">Related Sections</span></span>  
 [<span data-ttu-id="a8377-124">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="a8377-124">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="a8377-125">Obsahuje odkazy na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy v Visual Basic a C#.</span><span class="sxs-lookup"><span data-stu-id="a8377-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="a8377-126">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="a8377-126">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="a8377-127">Obsahuje odkazy na témata, která vysvětlují [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] koncepty pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]návrh dotazů v nástroji.</span><span class="sxs-lookup"><span data-stu-id="a8377-127">Provides links to topics that explain concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="a8377-128">Úvod do dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="a8377-128">Introduction to LINQ Queries (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="a8377-129">Vysvětluje, jak dotazy fungují [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]v.</span><span class="sxs-lookup"><span data-stu-id="a8377-129">Explains how queries work in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>

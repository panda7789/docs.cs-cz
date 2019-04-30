---
title: Seskupení prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: 5d812ae9b5fd0a796588d3366b8546ef84c982c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877354"
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="b96bf-102">Seskupení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="b96bf-102">Group Elements in a Sequence</span></span>
<span data-ttu-id="b96bf-103"><xref:System.Linq.Enumerable.GroupBy%2A> Operátor seskupuje prvky sady sekvenci.</span><span class="sxs-lookup"><span data-stu-id="b96bf-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="b96bf-104">Následující příklady používají databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="b96bf-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b96bf-105">Hodnota Null, hodnot sloupce v <xref:System.Linq.Enumerable.GroupBy%2A> někdy může vyvolat dotazů <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="b96bf-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="b96bf-106">Další informace najdete v tématu v části "GroupBy InvalidOperationException" [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="b96bf-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b96bf-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b96bf-107">Example</span></span>  
 <span data-ttu-id="b96bf-108">Následující příklad oddíly `Products` podle `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="b96bf-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="b96bf-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b96bf-109">Example</span></span>  
 <span data-ttu-id="b96bf-110">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> k vyhledání maximální jednotkové ceny pro každý `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="b96bf-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="b96bf-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="b96bf-111">Example</span></span>  
 <span data-ttu-id="b96bf-112">Následující příklad používá průměr Pokud chcete vypočítat průměr `UnitPrice` pro každou `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="b96bf-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="b96bf-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b96bf-113">Example</span></span>  
 <span data-ttu-id="b96bf-114">Následující příklad používá <xref:System.Linq.Queryable.Sum%2A> najít celkové `UnitPrice` pro každou `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="b96bf-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="b96bf-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="b96bf-115">Example</span></span>  
 <span data-ttu-id="b96bf-116">Následující příklad používá <xref:System.Linq.Queryable.Count%2A> zjistí počet ukončena `Products` v každém `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="b96bf-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="b96bf-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="b96bf-117">Example</span></span>  
 <span data-ttu-id="b96bf-118">Následující příklad používá následující `where` klauzule k vyhledání všech kategorií, které mají alespoň 10 produkty.</span><span class="sxs-lookup"><span data-stu-id="b96bf-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="b96bf-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="b96bf-119">Example</span></span>  
 <span data-ttu-id="b96bf-120">Následující příklad skupin produkty v jednotlivých `CategoryID` a `SupplierID`.</span><span class="sxs-lookup"><span data-stu-id="b96bf-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="b96bf-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="b96bf-121">Example</span></span>  
 <span data-ttu-id="b96bf-122">Následující příklad vrátí dvou sekvencí produktů.</span><span class="sxs-lookup"><span data-stu-id="b96bf-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="b96bf-123">První sekvence obsahuje produkty se cena za jednotku menší než nebo rovno 10.</span><span class="sxs-lookup"><span data-stu-id="b96bf-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="b96bf-124">Druhá sekvence obsahuje produkty se cena za jednotku větší než 10.</span><span class="sxs-lookup"><span data-stu-id="b96bf-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="b96bf-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="b96bf-125">Example</span></span>  
 <span data-ttu-id="b96bf-126"><xref:System.Linq.Queryable.GroupBy%2A> Operátor může trvat pouze jeden argument klíče.</span><span class="sxs-lookup"><span data-stu-id="b96bf-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="b96bf-127">Pokud potřebujete seskupit podle více než jeden klíč, musíte vytvořit anonymního typu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b96bf-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="b96bf-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b96bf-128">See also</span></span>

- [<span data-ttu-id="b96bf-129">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="b96bf-129">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="b96bf-130">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="b96bf-130">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)

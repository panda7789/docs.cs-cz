---
title: Seskupení prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: 50887acefdd5d0feaf9d0885e9ee842f44f0ef65
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915055"
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="646d7-102">Seskupení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="646d7-102">Group Elements in a Sequence</span></span>
<span data-ttu-id="646d7-103"><xref:System.Linq.Enumerable.GroupBy%2A> Operátor seskupí prvky sekvence.</span><span class="sxs-lookup"><span data-stu-id="646d7-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="646d7-104">V následujících příkladech se používá databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="646d7-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="646d7-105">Hodnoty null sloupce v <xref:System.Linq.Enumerable.GroupBy%2A> dotazech mohou někdy <xref:System.InvalidOperationException>vyvolat.</span><span class="sxs-lookup"><span data-stu-id="646d7-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="646d7-106">Další informace najdete v části "GroupBy InvalidOperationException" tématu [řešení potíží](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="646d7-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="646d7-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="646d7-107">Example</span></span>  
 <span data-ttu-id="646d7-108">Následující příklady oddílů `Products` podle `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="646d7-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="646d7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="646d7-109">Example</span></span>  
 <span data-ttu-id="646d7-110">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> k vyhledání maximální jednotkové ceny pro každý z `CategoryID`nich.</span><span class="sxs-lookup"><span data-stu-id="646d7-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="646d7-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="646d7-111">Example</span></span>  
 <span data-ttu-id="646d7-112">Následující příklad používá průměr pro nalezení průměru `UnitPrice` pro každý z nich. `CategoryID`</span><span class="sxs-lookup"><span data-stu-id="646d7-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="646d7-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="646d7-113">Example</span></span>  
 <span data-ttu-id="646d7-114">Následující příklad používá <xref:System.Linq.Queryable.Sum%2A> k vyhledání celkového součtu `UnitPrice` pro každý `CategoryID`z nich.</span><span class="sxs-lookup"><span data-stu-id="646d7-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="646d7-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="646d7-115">Example</span></span>  
 <span data-ttu-id="646d7-116">Následující příklad používá <xref:System.Linq.Queryable.Count%2A> k vyhledání počtu `Products` vyřazených v každé z nich `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="646d7-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="646d7-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="646d7-117">Example</span></span>  
 <span data-ttu-id="646d7-118">Následující příklad používá následující `where` klauzuli k vyhledání všech kategorií, které mají alespoň 10 produktů.</span><span class="sxs-lookup"><span data-stu-id="646d7-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="646d7-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="646d7-119">Example</span></span>  
 <span data-ttu-id="646d7-120">Následující příklad seskupuje produkty podle `CategoryID` a `SupplierID`.</span><span class="sxs-lookup"><span data-stu-id="646d7-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="646d7-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="646d7-121">Example</span></span>  
 <span data-ttu-id="646d7-122">Následující příklad vrátí dvě sekvence produktů.</span><span class="sxs-lookup"><span data-stu-id="646d7-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="646d7-123">První sekvence obsahuje produkty s jednotkovou cenou menší nebo rovnou 10.</span><span class="sxs-lookup"><span data-stu-id="646d7-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="646d7-124">Druhá sekvence obsahuje produkty s jednotkovou cenou větší než 10.</span><span class="sxs-lookup"><span data-stu-id="646d7-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="646d7-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="646d7-125">Example</span></span>  
 <span data-ttu-id="646d7-126"><xref:System.Linq.Queryable.GroupBy%2A> Operátor může převzít pouze jeden argument Key.</span><span class="sxs-lookup"><span data-stu-id="646d7-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="646d7-127">Pokud potřebujete seskupit podle více než jednoho klíče, je nutné vytvořit anonymní typ, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="646d7-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="646d7-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="646d7-128">See also</span></span>

- [<span data-ttu-id="646d7-129">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="646d7-129">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="646d7-130">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="646d7-130">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)

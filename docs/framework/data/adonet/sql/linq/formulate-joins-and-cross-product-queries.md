---
title: "Formulovali spojení a dotazy smíšený produkt"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 703823368f451839304ce02ff8b5f7259a44b935
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="10b1f-102">Formulovali spojení a dotazy smíšený produkt</span><span class="sxs-lookup"><span data-stu-id="10b1f-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="10b1f-103">Následující příklady ukazují, jak kombinují výsledky z více tabulek.</span><span class="sxs-lookup"><span data-stu-id="10b1f-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10b1f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="10b1f-104">Example</span></span>  
 <span data-ttu-id="10b1f-105">Následující příklad používá cizího klíče navigace ve `From` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` klauzule v jazyce C#) a vyberte všechny objednávky zákazníků v Londýně.</span><span class="sxs-lookup"><span data-stu-id="10b1f-105">The following example uses foreign key navigation in the `From` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="10b1f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="10b1f-106">Example</span></span>  
 <span data-ttu-id="10b1f-107">Následující příklad používá cizího klíče navigace ve `Where` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`where` klauzule v jazyce C#) Chcete-li filtrovat na více systémů stock `Products` jehož `Supplier` je ve Spojených státech amerických.</span><span class="sxs-lookup"><span data-stu-id="10b1f-107">The following example uses foreign key navigation in the `Where` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="10b1f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="10b1f-108">Example</span></span>  
 <span data-ttu-id="10b1f-109">Následující příklad používá cizího klíče navigace ve `From` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` klauzule v jazyce C#) k filtrování pro zaměstnance v Praze tak, aby jejich teritoria.</span><span class="sxs-lookup"><span data-stu-id="10b1f-109">The following example uses foreign key navigation in the `From` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="10b1f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="10b1f-110">Example</span></span>  
 <span data-ttu-id="10b1f-111">Následující příklad používá cizího klíče navigace ve `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) Chcete-li filtrovat páry zaměstnanců, kde jeden zaměstnanec sestavy na druhý a kde jsou obě zaměstnanci ze stejné `City`.</span><span class="sxs-lookup"><span data-stu-id="10b1f-111">The following example uses foreign key navigation in the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="10b1f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="10b1f-112">Example</span></span>  
 <span data-ttu-id="10b1f-113">Následující [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] příkladu vypadá pro všechny zákazníky a objednávky, zajišťuje, že budou odpovídat objednávky zákazníků a zaručuje, že pro každý zákazník v tomto seznamu, jméno kontaktní osoby je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="10b1f-113">The following [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="10b1f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="10b1f-114">Example</span></span>  
 <span data-ttu-id="10b1f-115">Následující příklad explicitně spojení dvou tabulek a projekty výsledky z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="10b1f-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="10b1f-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="10b1f-116">Example</span></span>  
 <span data-ttu-id="10b1f-117">Následující příklad explicitně spojí tři tabulky a projekty výsledky z každého z nich.</span><span class="sxs-lookup"><span data-stu-id="10b1f-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="10b1f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="10b1f-118">Example</span></span>  
 <span data-ttu-id="10b1f-119">Následující příklad ukazuje, jak dosáhnout `LEFT OUTER JOIN` pomocí `DefaultIfEmpty()`.</span><span class="sxs-lookup"><span data-stu-id="10b1f-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="10b1f-120">`DefaultIfEmpty()` Metoda vrátí hodnotu null, pokud není žádná `Order` pro `Employee`.</span><span class="sxs-lookup"><span data-stu-id="10b1f-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="10b1f-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="10b1f-121">Example</span></span>  
 <span data-ttu-id="10b1f-122">Následující příklad projekty `let` výraz výsledkem spojení.</span><span class="sxs-lookup"><span data-stu-id="10b1f-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="10b1f-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="10b1f-123">Example</span></span>  
 <span data-ttu-id="10b1f-124">Následující příklad ukazuje `join` s složený klíč.</span><span class="sxs-lookup"><span data-stu-id="10b1f-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="10b1f-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="10b1f-125">Example</span></span>  
 <span data-ttu-id="10b1f-126">Následující příklad ukazuje, jak vytvořit `join` kde jedné straně může mít hodnotu Null a druhý není.</span><span class="sxs-lookup"><span data-stu-id="10b1f-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="10b1f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="10b1f-127">See Also</span></span>  
 [<span data-ttu-id="10b1f-128">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="10b1f-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)

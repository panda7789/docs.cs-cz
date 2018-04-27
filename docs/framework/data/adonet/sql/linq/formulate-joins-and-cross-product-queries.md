---
title: Formulovali spojení a dotazy smíšený produkt
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 468ee54b0936afcbb548249bc714ea4b04abd3de
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="de66b-102">Formulovali spojení a dotazy smíšený produkt</span><span class="sxs-lookup"><span data-stu-id="de66b-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="de66b-103">Následující příklady ukazují, jak kombinují výsledky z více tabulek.</span><span class="sxs-lookup"><span data-stu-id="de66b-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de66b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="de66b-104">Example</span></span>  
 <span data-ttu-id="de66b-105">Následující příklad používá cizího klíče navigace ve `From` klauzule v jazyce Visual Basic (`from` klauzule v jazyce C#) a vyberte všechny objednávky zákazníků v Londýně.</span><span class="sxs-lookup"><span data-stu-id="de66b-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="de66b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="de66b-106">Example</span></span>  
 <span data-ttu-id="de66b-107">Následující příklad používá cizího klíče navigace ve `Where` klauzule v jazyce Visual Basic (`where` klauzule v jazyce C#) Chcete-li filtrovat na více systémů stock `Products` jehož `Supplier` je ve Spojených státech amerických.</span><span class="sxs-lookup"><span data-stu-id="de66b-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="de66b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="de66b-108">Example</span></span>  
 <span data-ttu-id="de66b-109">Následující příklad používá cizího klíče navigace ve `From` klauzule v jazyce Visual Basic (`from` klauzule v jazyce C#) k filtrování pro zaměstnance v Praze tak, aby jejich teritoria.</span><span class="sxs-lookup"><span data-stu-id="de66b-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="de66b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="de66b-110">Example</span></span>  
 <span data-ttu-id="de66b-111">Následující příklad používá cizího klíče navigace ve `Select` klauzule v jazyce Visual Basic (`select` klauzule v jazyce C#) Chcete-li filtrovat páry zaměstnanců, kde jeden zaměstnanec sestavy na druhý a kde jsou obě zaměstnanci ze stejné `City`.</span><span class="sxs-lookup"><span data-stu-id="de66b-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="de66b-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="de66b-112">Example</span></span>  
 <span data-ttu-id="de66b-113">Následující příklad jazyka Visual Basic vypadá pro všechny zákazníky a objednávky, zajišťuje, že budou odpovídat objednávky zákazníků a zaručuje, že pro každý zákazník v tomto seznamu, jméno kontaktní osoby je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="de66b-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="de66b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="de66b-114">Example</span></span>  
 <span data-ttu-id="de66b-115">Následující příklad explicitně spojení dvou tabulek a projekty výsledky z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="de66b-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="de66b-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="de66b-116">Example</span></span>  
 <span data-ttu-id="de66b-117">Následující příklad explicitně spojí tři tabulky a projekty výsledky z každého z nich.</span><span class="sxs-lookup"><span data-stu-id="de66b-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="de66b-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="de66b-118">Example</span></span>  
 <span data-ttu-id="de66b-119">Následující příklad ukazuje, jak dosáhnout `LEFT OUTER JOIN` pomocí `DefaultIfEmpty()`.</span><span class="sxs-lookup"><span data-stu-id="de66b-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="de66b-120">`DefaultIfEmpty()` Metoda vrátí hodnotu null, pokud není žádná `Order` pro `Employee`.</span><span class="sxs-lookup"><span data-stu-id="de66b-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="de66b-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="de66b-121">Example</span></span>  
 <span data-ttu-id="de66b-122">Následující příklad projekty `let` výraz výsledkem spojení.</span><span class="sxs-lookup"><span data-stu-id="de66b-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="de66b-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="de66b-123">Example</span></span>  
 <span data-ttu-id="de66b-124">Následující příklad ukazuje `join` s složený klíč.</span><span class="sxs-lookup"><span data-stu-id="de66b-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="de66b-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="de66b-125">Example</span></span>  
 <span data-ttu-id="de66b-126">Následující příklad ukazuje, jak vytvořit `join` kde jedné straně může mít hodnotu Null a druhý není.</span><span class="sxs-lookup"><span data-stu-id="de66b-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="de66b-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="de66b-127">See Also</span></span>  
 [<span data-ttu-id="de66b-128">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="de66b-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)

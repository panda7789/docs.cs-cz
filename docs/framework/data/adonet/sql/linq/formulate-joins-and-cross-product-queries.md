---
title: Formulování spojení a dotazů napříč produkty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: b0037f56947a86627ee9ea84369527aec859a0f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180502"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="170dc-102">Formulování spojení a dotazů napříč produkty</span><span class="sxs-lookup"><span data-stu-id="170dc-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="170dc-103">Následující příklady znázorňují způsob kombinace výsledků z více tabulek.</span><span class="sxs-lookup"><span data-stu-id="170dc-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="170dc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="170dc-104">Example</span></span>  
 <span data-ttu-id="170dc-105">Následující příklad používá cizího klíče navigace ve `From` klauzule v jazyce Visual Basic (`from` klauzuli v C#) Chcete-li vybrat všechny objednávky pro zákazníky, kteří v Londýně.</span><span class="sxs-lookup"><span data-stu-id="170dc-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="170dc-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="170dc-106">Example</span></span>  
 <span data-ttu-id="170dc-107">Následující příklad používá cizího klíče navigace v `Where` klauzule v jazyce Visual Basic (`where` klauzuli v C#) Chcete-li filtrovat mimo akcie `Products` jehož `Supplier` je ve Spojených státech.</span><span class="sxs-lookup"><span data-stu-id="170dc-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="170dc-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="170dc-108">Example</span></span>  
 <span data-ttu-id="170dc-109">Následující příklad používá cizího klíče navigace v `From` klauzule v jazyce Visual Basic (`from` klauzuli v C#) Chcete-li filtrovat zaměstnanci v Praze a seznam jejich území.</span><span class="sxs-lookup"><span data-stu-id="170dc-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="170dc-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="170dc-110">Example</span></span>  
 <span data-ttu-id="170dc-111">Následující příklad používá cizího klíče navigace ve `Select` klauzule v jazyce Visual Basic (`select` klauzuli v C#) Chcete-li filtrovat páry zaměstnanců, kde sestavy jeden ze zaměstnanců na druhý a kde jsou obě zaměstnanci ze stejné `City`.</span><span class="sxs-lookup"><span data-stu-id="170dc-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="170dc-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="170dc-112">Example</span></span>  
 <span data-ttu-id="170dc-113">Následující příklad jazyka Visual Basic vyhledá všechny zákazníci a objednávky, zajišťuje, že zákazníci budou odpovídat objednávky a zaručuje, že pro každý zákazník v tomto seznamu jméno kontaktní osoby je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="170dc-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="170dc-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="170dc-114">Example</span></span>  
 <span data-ttu-id="170dc-115">Následující příklad připojí explicitně dvě tabulky a projekty výsledky z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="170dc-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="170dc-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="170dc-116">Example</span></span>  
 <span data-ttu-id="170dc-117">Následující příklad explicitně sloučí tři tabulky a projekty výsledky z každé z nich.</span><span class="sxs-lookup"><span data-stu-id="170dc-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="170dc-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="170dc-118">Example</span></span>  
 <span data-ttu-id="170dc-119">Následující příklad ukazuje, jak dosáhnout `LEFT OUTER JOIN` pomocí `DefaultIfEmpty()`.</span><span class="sxs-lookup"><span data-stu-id="170dc-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="170dc-120">`DefaultIfEmpty()` Metoda vrátí hodnotu null, pokud neexistuje žádný `Order` pro `Employee`.</span><span class="sxs-lookup"><span data-stu-id="170dc-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="170dc-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="170dc-121">Example</span></span>  
 <span data-ttu-id="170dc-122">Následující vzorové projekty `let` výraz vyplývající z spojení.</span><span class="sxs-lookup"><span data-stu-id="170dc-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="170dc-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="170dc-123">Example</span></span>  
 <span data-ttu-id="170dc-124">Následující příklad ukazuje `join` s složený klíč.</span><span class="sxs-lookup"><span data-stu-id="170dc-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="170dc-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="170dc-125">Example</span></span>  
 <span data-ttu-id="170dc-126">Následující příklad ukazuje, jak vytvořit `join` kde na jedné straně může mít hodnotu Null a druhá ne.</span><span class="sxs-lookup"><span data-stu-id="170dc-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="170dc-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="170dc-127">See also</span></span>

- [<span data-ttu-id="170dc-128">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="170dc-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)

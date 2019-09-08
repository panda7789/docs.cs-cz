---
title: Formulování spojení a dotazů napříč produkty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 002a644ff5d48b25351228dcd74330707491d6c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782091"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="46ea8-102">Formulování spojení a dotazů napříč produkty</span><span class="sxs-lookup"><span data-stu-id="46ea8-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="46ea8-103">Následující příklady znázorňují, jak kombinovat výsledky z více tabulek.</span><span class="sxs-lookup"><span data-stu-id="46ea8-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46ea8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="46ea8-104">Example</span></span>  
 <span data-ttu-id="46ea8-105">V následujícím příkladu se používá navigace pomocí cizího `From` klíče v klauzuli v`from` Visual Basic ( C#klauzule in) pro výběr všech objednávek pro zákazníky v Londýně.</span><span class="sxs-lookup"><span data-stu-id="46ea8-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="46ea8-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="46ea8-106">Example</span></span>  
 <span data-ttu-id="46ea8-107">V následujícím příkladu se používá navigace pomocí cizího `Where` klíče v klauzuli v`where` Visual Basic ( C#klauzule in) k filtrování pro nepoužitou `Products` populaci `Supplier` , jejíž je v USA.</span><span class="sxs-lookup"><span data-stu-id="46ea8-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="46ea8-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="46ea8-108">Example</span></span>  
 <span data-ttu-id="46ea8-109">V následujícím příkladu se používá navigace pomocí cizího `From` klíče v klauzuli v`from` Visual Basic ( C#klauzule in) k filtrování zaměstnanců v Seattlu a k vypsání jejich oblastí.</span><span class="sxs-lookup"><span data-stu-id="46ea8-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="46ea8-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="46ea8-110">Example</span></span>  
 <span data-ttu-id="46ea8-111">V následujícím příkladu se používá navigace pomocí cizího `Select` klíče v klauzuli v`select` Visual Basic ( C#klauzule in) k filtrování párů zaměstnanců, kteří jeden zaměstnanec nahlásí do druhé a kde jsou oba zaměstnanci ze stejné `City`.</span><span class="sxs-lookup"><span data-stu-id="46ea8-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="46ea8-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="46ea8-112">Example</span></span>  
 <span data-ttu-id="46ea8-113">Následující Visual Basic příklad vyhledá všechny zákazníky a objednávky, zajistěte, aby objednávky odpovídaly zákazníkům, a zaručuje, že pro každého zákazníka v tomto seznamu se zadá jméno kontaktu.</span><span class="sxs-lookup"><span data-stu-id="46ea8-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="46ea8-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="46ea8-114">Example</span></span>  
 <span data-ttu-id="46ea8-115">Následující příklad explicitně spojí dvě tabulky a projekty z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="46ea8-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="46ea8-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="46ea8-116">Example</span></span>  
 <span data-ttu-id="46ea8-117">Následující příklad explicitně spojí tři tabulky a projekty z každého z nich.</span><span class="sxs-lookup"><span data-stu-id="46ea8-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="46ea8-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="46ea8-118">Example</span></span>  
 <span data-ttu-id="46ea8-119">Následující příklad ukazuje, jak dosáhnout `LEFT OUTER JOIN` pomocí. `DefaultIfEmpty()`</span><span class="sxs-lookup"><span data-stu-id="46ea8-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="46ea8-120">Metoda vrátí hodnotu null, pokud `Order` není pro `Employee`. `DefaultIfEmpty()`</span><span class="sxs-lookup"><span data-stu-id="46ea8-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="46ea8-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="46ea8-121">Example</span></span>  
 <span data-ttu-id="46ea8-122">Následující příklad vyjedná výraz `let` , který je výsledkem spojení.</span><span class="sxs-lookup"><span data-stu-id="46ea8-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="46ea8-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="46ea8-123">Example</span></span>  
 <span data-ttu-id="46ea8-124">Následující příklad ukazuje a `join` obsahuje složený klíč.</span><span class="sxs-lookup"><span data-stu-id="46ea8-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="46ea8-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="46ea8-125">Example</span></span>  
 <span data-ttu-id="46ea8-126">Následující příklad ukazuje, jak vytvořit, kde `join` jedna strana může mít hodnotu null a druhá není.</span><span class="sxs-lookup"><span data-stu-id="46ea8-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="46ea8-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46ea8-127">See also</span></span>

- [<span data-ttu-id="46ea8-128">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="46ea8-128">Query Examples</span></span>](query-examples.md)

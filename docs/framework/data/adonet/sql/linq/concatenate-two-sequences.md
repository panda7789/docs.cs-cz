---
title: "Řetězení dvě pořadí"
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
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a73ace484c3ca519f250069063a9222b75ef6c17
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="b5808-102">Řetězení dvě pořadí</span><span class="sxs-lookup"><span data-stu-id="b5808-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="b5808-103">Použití <xref:System.Linq.Queryable.Concat%2A> operátor ke zřetězení dvě pořadí.</span><span class="sxs-lookup"><span data-stu-id="b5808-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="b5808-104"><xref:System.Linq.Queryable.Concat%2A> Operátor je definována pro seřazené multisets kde objednávky příjemce a argument jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="b5808-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="b5808-105">Řazení v systému SQL je v posledním kroku, před vytváří výsledky.</span><span class="sxs-lookup"><span data-stu-id="b5808-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="b5808-106">Z tohoto důvodu <xref:System.Linq.Queryable.Concat%2A> operátor je implementována pomocí `UNION ALL` a nezachovává pořadí argumentů.</span><span class="sxs-lookup"><span data-stu-id="b5808-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="b5808-107">Ujistěte se, že řazení je správný ve výsledcích, zajistěte, aby explicitně řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="b5808-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5808-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5808-108">Example</span></span>  
 <span data-ttu-id="b5808-109">Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> vrátit pořadí všech `Customer` a `Employee` číslo telefonu a faxu.</span><span class="sxs-lookup"><span data-stu-id="b5808-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="b5808-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5808-110">Example</span></span>  
 <span data-ttu-id="b5808-111">Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> vrátit pořadí všech `Customer` a `Employee` název a telefonní číslo mapování.</span><span class="sxs-lookup"><span data-stu-id="b5808-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="b5808-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5808-112">See Also</span></span>  
 [<span data-ttu-id="b5808-113">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="b5808-113">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="b5808-114">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="b5808-114">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)

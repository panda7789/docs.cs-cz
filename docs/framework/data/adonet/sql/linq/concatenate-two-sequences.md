---
title: Zřetězení dvou sekvencí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: b802abae9fc2c1731a623209862f61ed5ee51f9c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247889"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="704ff-102">Zřetězení dvou sekvencí</span><span class="sxs-lookup"><span data-stu-id="704ff-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="704ff-103"><xref:System.Linq.Queryable.Concat%2A> Použijte operátor ke zřetězení dvou sekvencí.</span><span class="sxs-lookup"><span data-stu-id="704ff-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="704ff-104"><xref:System.Linq.Queryable.Concat%2A> Operátor je definován pro seřazené množiny, kde jsou objednávky příjemce a argumentu stejné.</span><span class="sxs-lookup"><span data-stu-id="704ff-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="704ff-105">Řazení v SQL je posledním krokem před tím, než se vytvoří výsledky.</span><span class="sxs-lookup"><span data-stu-id="704ff-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="704ff-106">Z <xref:System.Linq.Queryable.Concat%2A> tohoto důvodu je operátor implementován pomocí `UNION ALL` a nezachovává pořadí jeho argumentů.</span><span class="sxs-lookup"><span data-stu-id="704ff-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="704ff-107">Chcete-li se ujistit, že je řazení ve výsledcích správné, ujistěte se, že jsou výsledky explicitně seřazeny.</span><span class="sxs-lookup"><span data-stu-id="704ff-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="704ff-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="704ff-108">Example</span></span>  
 <span data-ttu-id="704ff-109">Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> k vrácení posloupnosti `Employee` všech `Customer` telefonních a faxových čísel.</span><span class="sxs-lookup"><span data-stu-id="704ff-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="704ff-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="704ff-110">Example</span></span>  
 <span data-ttu-id="704ff-111">Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> k vrácení posloupnosti mapování všech `Customer` názvů `Employee` a názvu a telefonního čísla.</span><span class="sxs-lookup"><span data-stu-id="704ff-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="704ff-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="704ff-112">See also</span></span>

- [<span data-ttu-id="704ff-113">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="704ff-113">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="704ff-114">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="704ff-114">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)

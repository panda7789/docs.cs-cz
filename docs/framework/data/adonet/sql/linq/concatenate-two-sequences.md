---
title: Zřetězení dvou sekvencí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: a2f2510cb334f4e22a7b0c6015a0a93b4dc11579
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142776"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="ab63d-102">Zřetězení dvou sekvencí</span><span class="sxs-lookup"><span data-stu-id="ab63d-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="ab63d-103">Použití <xref:System.Linq.Queryable.Concat%2A> operátoru pro zřetězení dvou sekvencí.</span><span class="sxs-lookup"><span data-stu-id="ab63d-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="ab63d-104"><xref:System.Linq.Queryable.Concat%2A> Operátor je definován pro uspořádaný multisets kde objednávky příjemce a argument jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="ab63d-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="ab63d-105">Řazení v SQL je posledním krokem předtím, než se produkují výsledky.</span><span class="sxs-lookup"><span data-stu-id="ab63d-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="ab63d-106">Z tohoto důvodu <xref:System.Linq.Queryable.Concat%2A> operátor je implementovaný s využitím `UNION ALL` a nezachovávat hodnotu pořadí z jejích argumentů.</span><span class="sxs-lookup"><span data-stu-id="ab63d-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="ab63d-107">Ujistěte se, že pořadí je správné výsledky, ujistěte se, že explicitně řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="ab63d-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab63d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab63d-108">Example</span></span>  
 <span data-ttu-id="ab63d-109">Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> k vrácení sekvence všech `Customer` a `Employee` číslo telefonu a faxu.</span><span class="sxs-lookup"><span data-stu-id="ab63d-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="ab63d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab63d-110">Example</span></span>  
 <span data-ttu-id="ab63d-111">Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> k vrácení sekvence všech `Customer` a `Employee` pojmenujte a telefonní číslo mapování.</span><span class="sxs-lookup"><span data-stu-id="ab63d-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="ab63d-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab63d-112">See also</span></span>

- [<span data-ttu-id="ab63d-113">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="ab63d-113">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="ab63d-114">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="ab63d-114">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)

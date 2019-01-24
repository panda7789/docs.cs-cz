---
title: Zřetězení dvou sekvencí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: 831905ca5a712bcb80d5bab1aef61a81d2ade1b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734272"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="c9a5f-102">Zřetězení dvou sekvencí</span><span class="sxs-lookup"><span data-stu-id="c9a5f-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="c9a5f-103">Použití <xref:System.Linq.Queryable.Concat%2A> operátoru pro zřetězení dvou sekvencí.</span><span class="sxs-lookup"><span data-stu-id="c9a5f-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="c9a5f-104"><xref:System.Linq.Queryable.Concat%2A> Operátor je definován pro uspořádaný multisets kde objednávky příjemce a argument jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="c9a5f-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="c9a5f-105">Řazení v SQL je posledním krokem předtím, než se produkují výsledky.</span><span class="sxs-lookup"><span data-stu-id="c9a5f-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="c9a5f-106">Z tohoto důvodu <xref:System.Linq.Queryable.Concat%2A> operátor je implementovaný s využitím `UNION ALL` a nezachovávat hodnotu pořadí z jejích argumentů.</span><span class="sxs-lookup"><span data-stu-id="c9a5f-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="c9a5f-107">Ujistěte se, že pořadí je správné výsledky, ujistěte se, že explicitně řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="c9a5f-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9a5f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9a5f-108">Example</span></span>  
 <span data-ttu-id="c9a5f-109">Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> k vrácení sekvence všech `Customer` a `Employee` číslo telefonu a faxu.</span><span class="sxs-lookup"><span data-stu-id="c9a5f-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="c9a5f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9a5f-110">Example</span></span>  
 <span data-ttu-id="c9a5f-111">Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> k vrácení sekvence všech `Customer` a `Employee` pojmenujte a telefonní číslo mapování.</span><span class="sxs-lookup"><span data-stu-id="c9a5f-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="c9a5f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9a5f-112">See also</span></span>
- [<span data-ttu-id="c9a5f-113">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="c9a5f-113">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="c9a5f-114">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="c9a5f-114">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)

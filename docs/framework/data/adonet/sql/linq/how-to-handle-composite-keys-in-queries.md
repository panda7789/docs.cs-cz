---
title: 'Postupy: Zpracování složených klíčů v dotazech'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 2621ab4db207d1b868fbe3778c30c744201b0506
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135249"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="f41f2-102">Postupy: Zpracování složených klíčů v dotazech</span><span class="sxs-lookup"><span data-stu-id="f41f2-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="f41f2-103">Některé operátory lze provést pouze jeden argument.</span><span class="sxs-lookup"><span data-stu-id="f41f2-103">Some operators can take only one argument.</span></span> <span data-ttu-id="f41f2-104">Pokud váš argument musí obsahovat více než jeden sloupec z databáze, musíte vytvořit anonymního typu k reprezentaci kombinace.</span><span class="sxs-lookup"><span data-stu-id="f41f2-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f41f2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f41f2-105">Example</span></span>  
 <span data-ttu-id="f41f2-106">Následující příklad ukazuje dotaz, který vyvolá `GroupBy` operátor, který může mít pouze jeden `key` argument.</span><span class="sxs-lookup"><span data-stu-id="f41f2-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="f41f2-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f41f2-107">Example</span></span>  
 <span data-ttu-id="f41f2-108">O stejnou situaci se vztahují na spojení, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f41f2-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f41f2-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f41f2-109">See also</span></span>

- [<span data-ttu-id="f41f2-110">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="f41f2-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)

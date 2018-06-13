---
title: 'Postupy: zpracování složené klíče v dotazech.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 26c281445b84d3b3f85980de6ae4076411bb4fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354236"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="94545-102">Postupy: zpracování složené klíče v dotazech.</span><span class="sxs-lookup"><span data-stu-id="94545-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="94545-103">Některé operátory může trvat jenom jeden argument.</span><span class="sxs-lookup"><span data-stu-id="94545-103">Some operators can take only one argument.</span></span> <span data-ttu-id="94545-104">Pokud váš argument musí obsahovat více než jeden sloupec z databáze, musíte vytvořit anonymní typ představují kombinaci.</span><span class="sxs-lookup"><span data-stu-id="94545-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94545-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="94545-105">Example</span></span>  
 <span data-ttu-id="94545-106">Následující příklad ukazuje dotaz, který volá `GroupBy` operátor, který můžete provést pouze jednu `key` argument.</span><span class="sxs-lookup"><span data-stu-id="94545-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="94545-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="94545-107">Example</span></span>  
 <span data-ttu-id="94545-108">Stejná situace se vztahují na spojení, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="94545-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="94545-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="94545-109">See Also</span></span>  
 [<span data-ttu-id="94545-110">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="94545-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)

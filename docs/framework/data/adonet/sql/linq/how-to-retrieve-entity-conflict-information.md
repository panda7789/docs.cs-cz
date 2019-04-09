---
title: 'Postupy: Načtení informací o konfliktech entit'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: 825ba2a32e7c75e922ca08386b9f6efede7b2693
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154749"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="16096-102">Postupy: Načtení informací o konfliktech entit</span><span class="sxs-lookup"><span data-stu-id="16096-102">How to: Retrieve Entity Conflict Information</span></span>
<span data-ttu-id="16096-103">Můžete použít objekty <xref:System.Data.Linq.ObjectChangeConflict> třídy k poskytnutí informací o konfliktech neposkytuje <xref:System.Data.Linq.ChangeConflictException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="16096-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="16096-104">Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16096-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="16096-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="16096-105">Example</span></span>  
 <span data-ttu-id="16096-106">Následující příklad Iteruje přes seznam součet je v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="16096-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="16096-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16096-107">See also</span></span>

- [<span data-ttu-id="16096-108">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="16096-108">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)

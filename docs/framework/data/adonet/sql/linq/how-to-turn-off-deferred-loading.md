---
title: 'Postupy: Vypnutí odloženého načítání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f68db5a5a0092fc4cf37746f2a4dc81e40ee4a9d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938680"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="e4da2-102">Postupy: Vypnutí odloženého načítání</span><span class="sxs-lookup"><span data-stu-id="e4da2-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="e4da2-103">Odložené načítání můžete vypnout nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> na. `false`</span><span class="sxs-lookup"><span data-stu-id="e4da2-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="e4da2-104">Další informace najdete v tématu [odložené porovnání a okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="e4da2-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4da2-105">Odložené načítání je vypnuto, je-li sledování objektu vypnuto.</span><span class="sxs-lookup"><span data-stu-id="e4da2-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="e4da2-106">Další informace najdete v tématu [jak: Načte informace jen pro čtení](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="e4da2-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4da2-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4da2-107">Example</span></span>  
 <span data-ttu-id="e4da2-108">Následující příklad ukazuje, jak vypnout odložené načítání nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> na. `false`</span><span class="sxs-lookup"><span data-stu-id="e4da2-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e4da2-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4da2-109">See also</span></span>

- [<span data-ttu-id="e4da2-110">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="e4da2-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="e4da2-111">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="e4da2-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)

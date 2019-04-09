---
title: 'Postupy: Vypnutí odloženého načítání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f82e347ecdb3c69cee3749855d1e4cb457a460f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112954"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="68d9a-102">Postupy: Vypnutí odloženého načítání</span><span class="sxs-lookup"><span data-stu-id="68d9a-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="68d9a-103">Můžete ji vypnout odloženého načítání nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> k `false`.</span><span class="sxs-lookup"><span data-stu-id="68d9a-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="68d9a-104">Další informace najdete v tématu [odložené versus okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="68d9a-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68d9a-105">Odložené načítání je vypnuto již při objektů pro sledování je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="68d9a-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="68d9a-106">Další informace najdete v tématu [jak: Načtení informací ve stavu jen pro čtení](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="68d9a-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68d9a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="68d9a-107">Example</span></span>  
 <span data-ttu-id="68d9a-108">Následující příklad ukazuje, jak vypnutí odloženého načítání nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> k `false`.</span><span class="sxs-lookup"><span data-stu-id="68d9a-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="68d9a-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68d9a-109">See also</span></span>

- [<span data-ttu-id="68d9a-110">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="68d9a-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="68d9a-111">Dotazy do databáze</span><span class="sxs-lookup"><span data-stu-id="68d9a-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)

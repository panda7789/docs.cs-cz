---
title: 'Postupy: Vypnutí odloženého načítání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 6559392527bb02afe9cea61e704f1f371c6d5470
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781653"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="a8f96-102">Postupy: Vypnutí odloženého načítání</span><span class="sxs-lookup"><span data-stu-id="a8f96-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="a8f96-103">Odložené načítání můžete vypnout nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> na. `false`</span><span class="sxs-lookup"><span data-stu-id="a8f96-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="a8f96-104">Další informace najdete v tématu [odložené porovnání a okamžité načítání](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="a8f96-104">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8f96-105">Odložené načítání je vypnuto, je-li sledování objektu vypnuto.</span><span class="sxs-lookup"><span data-stu-id="a8f96-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="a8f96-106">Další informace najdete v tématu [jak: Načte informace jen pro čtení](how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="a8f96-106">For more information, see [How to: Retrieve Information As Read-Only](how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8f96-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8f96-107">Example</span></span>  
 <span data-ttu-id="a8f96-108">Následující příklad ukazuje, jak vypnout odložené načítání nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> na. `false`</span><span class="sxs-lookup"><span data-stu-id="a8f96-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a8f96-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8f96-109">See also</span></span>

- [<span data-ttu-id="a8f96-110">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="a8f96-110">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="a8f96-111">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="a8f96-111">Querying the Database</span></span>](querying-the-database.md)

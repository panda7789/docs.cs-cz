---
title: 'Postupy: Načtení informací ve stavu jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 131562e9ee0fbfde8c94f580bcb6d452918f42ee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148977"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="948a3-102">Postupy: Načtení informací ve stavu jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="948a3-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="948a3-103">Pokud je nemáte v úmyslu změnit data, můžete zvýšit výkon dotazů jen pro čtení výsledků hledání.</span><span class="sxs-lookup"><span data-stu-id="948a3-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="948a3-104">Implementace zpracování jen pro čtení tak, že nastavíte <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> k `false`.</span><span class="sxs-lookup"><span data-stu-id="948a3-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="948a3-105">Když <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> je nastavena na `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> implicitně nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="948a3-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="948a3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="948a3-106">Example</span></span>  
 <span data-ttu-id="948a3-107">Následující kód načte kolekci jen pro čtení dat zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="948a3-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="948a3-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="948a3-108">See also</span></span>

- [<span data-ttu-id="948a3-109">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="948a3-109">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="948a3-110">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="948a3-110">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [<span data-ttu-id="948a3-111">Odložené versus okamžité načítání</span><span class="sxs-lookup"><span data-stu-id="948a3-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)

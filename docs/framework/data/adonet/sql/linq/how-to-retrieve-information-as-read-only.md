---
title: 'Postupy: Načtení informací ve stavu jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 399bf44ef5536a9adebf1cad590439741df998f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793312"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="6b955-102">Postupy: Načtení informací ve stavu jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6b955-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="6b955-103">Pokud nechcete data změnit, můžete zvýšit výkon dotazů hledáním výsledků jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="6b955-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="6b955-104">Implementujete zpracování <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> jen pro čtení nastavením na `false`.</span><span class="sxs-lookup"><span data-stu-id="6b955-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b955-105">Pokud <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> je nastaveno na `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> je implicitně nastaveno na `false`.</span><span class="sxs-lookup"><span data-stu-id="6b955-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b955-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b955-106">Example</span></span>  
 <span data-ttu-id="6b955-107">Následující kód načte kolekci kalendářních dat o přijímácích zaměstnanců jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="6b955-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6b955-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b955-108">See also</span></span>

- [<span data-ttu-id="6b955-109">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="6b955-109">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="6b955-110">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="6b955-110">Querying the Database</span></span>](querying-the-database.md)
- [<span data-ttu-id="6b955-111">Odložené versus okamžité načítání</span><span class="sxs-lookup"><span data-stu-id="6b955-111">Deferred versus Immediate Loading</span></span>](deferred-versus-immediate-loading.md)

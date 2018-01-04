---
title: "Postupy: načtení informací o jen pro čtení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 04a20a06cd8ed8785b37bdc604a817b475f93873
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="f1a0c-102">Postupy: načtení informací o jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f1a0c-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="f1a0c-103">Pokud jste neměli v úmyslu změnit data, můžete zvýšit výkon dotazů ve vyhledávání výsledky jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f1a0c-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="f1a0c-104">Implementace zpracování jen pro čtení nastavením <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> k `false`.</span><span class="sxs-lookup"><span data-stu-id="f1a0c-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1a0c-105">Když <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> je nastaven na `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> implicitně nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="f1a0c-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1a0c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1a0c-106">Example</span></span>  
 <span data-ttu-id="f1a0c-107">Následující kód načte kolekci jen pro čtení dat zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="f1a0c-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f1a0c-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1a0c-108">See Also</span></span>  
 [<span data-ttu-id="f1a0c-109">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="f1a0c-109">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="f1a0c-110">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="f1a0c-110">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 [<span data-ttu-id="f1a0c-111">Odložené versus okamžité načítání</span><span class="sxs-lookup"><span data-stu-id="f1a0c-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)

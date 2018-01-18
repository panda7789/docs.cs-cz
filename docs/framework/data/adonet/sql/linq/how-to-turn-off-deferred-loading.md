---
title: "Postupy: odložené načítání vypnout."
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
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e5c17d0cfa4fed33c2648173002e5ee1bdcc2c15
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="73f6d-102">Postupy: odložené načítání vypnout.</span><span class="sxs-lookup"><span data-stu-id="73f6d-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="73f6d-103">Můžete vypnout odložené načítání nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> k `false`.</span><span class="sxs-lookup"><span data-stu-id="73f6d-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="73f6d-104">Další informace najdete v tématu [odložení versus okamžitou načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="73f6d-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73f6d-105">Odložené načtení je vypnutý nepřímo při sledování objektu je vypnutý.</span><span class="sxs-lookup"><span data-stu-id="73f6d-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="73f6d-106">Další informace najdete v tématu [postupy: načtení informací jako jen pro čtení](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="73f6d-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73f6d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="73f6d-107">Example</span></span>  
 <span data-ttu-id="73f6d-108">Následující příklad ukazuje, jak vypnout odložené načítání nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> k `false`.</span><span class="sxs-lookup"><span data-stu-id="73f6d-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="73f6d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="73f6d-109">See Also</span></span>  
 [<span data-ttu-id="73f6d-110">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="73f6d-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="73f6d-111">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="73f6d-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)

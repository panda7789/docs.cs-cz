---
title: "Postupy: Zadejte Kontrola konfliktu souběžnosti"
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
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e9c3839f4b70bfec759617d875095d9ce8eecf54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="e8c9b-102">Postupy: Zadejte Kontrola konfliktu souběžnosti</span><span class="sxs-lookup"><span data-stu-id="e8c9b-102">How to: Specify Concurrency-Conflict Checking</span></span>
<span data-ttu-id="e8c9b-103">Můžete určit sloupce, které databáze jsou ke kontrole souběžnosti konflikty při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-103">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="e8c9b-104">Další informace najdete v tématu [postup: Určete který členové jsou testovány souběžnosti konflikty](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="e8c9b-104">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8c9b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8c9b-105">Example</span></span>  
 <span data-ttu-id="e8c9b-106">Následující kód určuje, že `HomePage` člen by měl být vůbec neotestovali během kontroly aktualizací.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-106">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="e8c9b-107">Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="e8c9b-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e8c9b-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8c9b-108">See Also</span></span>  
 [<span data-ttu-id="e8c9b-109">Technologie LINQ to SQL objektový Model</span><span class="sxs-lookup"><span data-stu-id="e8c9b-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="e8c9b-110">Postupy: přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="e8c9b-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)

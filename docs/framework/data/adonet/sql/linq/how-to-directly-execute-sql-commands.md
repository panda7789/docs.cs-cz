---
title: "Postupy: přímo spustit příkazy SQL"
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
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a1b3b94f00e9b8fb866a81f5076fb43fe9f22951
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="82431-102">Postupy: přímo spustit příkazy SQL</span><span class="sxs-lookup"><span data-stu-id="82431-102">How to: Directly Execute SQL Commands</span></span>
<span data-ttu-id="82431-103">Za předpokladu, že <xref:System.Data.Linq.DataContext> připojení, můžete použít <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> provést příkazy SQL, které nevracejí objekty.</span><span class="sxs-lookup"><span data-stu-id="82431-103">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82431-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="82431-104">Example</span></span>  
 <span data-ttu-id="82431-105">Následující příklad způsobí, že Server SQL a zvyšuje UnitPrice 1.00.</span><span class="sxs-lookup"><span data-stu-id="82431-105">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="82431-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="82431-106">See Also</span></span>  
 [<span data-ttu-id="82431-107">Postupy: Přímé spuštění dotazů SQL</span><span class="sxs-lookup"><span data-stu-id="82431-107">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 [<span data-ttu-id="82431-108">Komunikace s databází</span><span class="sxs-lookup"><span data-stu-id="82431-108">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)

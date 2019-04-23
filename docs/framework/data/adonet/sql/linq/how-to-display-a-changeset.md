---
title: 'Postupy: Zobrazení sady změn'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: 92acee0d36634ea09c245418fcc7a8b97d208aa6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228626"
---
# <a name="how-to-display-a-changeset"></a><span data-ttu-id="f8002-102">Postupy: Zobrazení sady změn</span><span class="sxs-lookup"><span data-stu-id="f8002-102">How to: Display a ChangeSet</span></span>
<span data-ttu-id="f8002-103">Sledovat změny si můžete prohlédnout <xref:System.Data.Linq.DataContext> pomocí <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8002-103">You can view changes tracked by a <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8002-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8002-104">Example</span></span>  
 <span data-ttu-id="f8002-105">Následující příklad načte zákazníků, jejichž Město je Londýn, Město se změní na Paříž a odešle změny zpět do databáze.</span><span class="sxs-lookup"><span data-stu-id="f8002-105">The following example retrieves customers whose city is London, changes the city to Paris, and submits the changes back to the database.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 <span data-ttu-id="f8002-106">Výstup tohoto kódu se zobrazí podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="f8002-106">Output from this code appears similar to the following.</span></span> <span data-ttu-id="f8002-107">Všimněte si, že souhrnu uplynutí ukazuje, že byly provedeny změny osm.</span><span class="sxs-lookup"><span data-stu-id="f8002-107">Note that the summary at the end shows that eight changes were made.</span></span>  

 ```console
CustomerID: AROUT
   Original value: London
   Updated value: Paris
CustomerID: BSBEV
   Original value: London
   Updated value: Paris
CustomerID: CONSH
   Original value: London
   Updated value: Paris
CustomerID: EASTC
   Original value: London
   Updated value: Paris
CustomerID: NORTS
    Original value: London
    Updated value: Paris
CustomerID: PARIS
    Original value: London
    Updated value: Paris
CustomerID: SEVES
    Original value: London
    Updated value: Paris
CustomerID: SPECD
    Original value: London
    Updated value: Paris
Total changes: {Added: 0, Removed: 0, Modified: 8}
```
  
## <a name="see-also"></a><span data-ttu-id="f8002-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8002-108">See also</span></span>

- [<span data-ttu-id="f8002-109">Podpora ladění</span><span class="sxs-lookup"><span data-stu-id="f8002-109">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)

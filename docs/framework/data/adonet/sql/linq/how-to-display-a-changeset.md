---
title: "Postupy: zobrazení změn"
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
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f6de059f56318ed910f4583ba9618a5a20040ec7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-display-a-changeset"></a><span data-ttu-id="e10c9-102">Postupy: zobrazení změn</span><span class="sxs-lookup"><span data-stu-id="e10c9-102">How to: Display a ChangeSet</span></span>
<span data-ttu-id="e10c9-103">Sleduje změny si můžete prohlédnout <xref:System.Data.Linq.DataContext> pomocí <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span><span class="sxs-lookup"><span data-stu-id="e10c9-103">You can view changes tracked by a <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e10c9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e10c9-104">Example</span></span>  
 <span data-ttu-id="e10c9-105">Následující příklad načte zákazníků, jejichž Město je Londýn, změny město Paříž a odešle, že změny zpět do databáze.</span><span class="sxs-lookup"><span data-stu-id="e10c9-105">The following example retrieves customers whose city is London, changes the city to Paris, and submits the changes back to the database.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 <span data-ttu-id="e10c9-106">Zobrazí se výstup z tohoto kódu podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="e10c9-106">Output from this code appears similar to the following.</span></span> <span data-ttu-id="e10c9-107">Všimněte si, že shrnutí na konci ukazuje, že byly provedeny změny osm.</span><span class="sxs-lookup"><span data-stu-id="e10c9-107">Note that the summary at the end shows that eight changes were made.</span></span>  
  
 `CustomerID: AROUT`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: BSBEV`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: CONSH`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: EASTC`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: NORTS`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: PARIS`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: SEVES`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: SPECD`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 ``  
  
 `Total changes: {Added: 0, Removed: 0, Modified: 8}`  
  
## <a name="see-also"></a><span data-ttu-id="e10c9-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e10c9-108">See Also</span></span>  
 [<span data-ttu-id="e10c9-109">Podpora ladění</span><span class="sxs-lookup"><span data-stu-id="e10c9-109">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)

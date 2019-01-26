---
title: 'Postupy: Zobrazit sadu změn'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: e6030a48a773dcf985eee5c4c113b02386780707
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065814"
---
# <a name="how-to-display-a-changeset"></a>Postupy: Zobrazit sadu změn
Sledovat změny si můžete prohlédnout <xref:System.Data.Linq.DataContext> pomocí <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příklad načte zákazníků, jejichž Město je Londýn, Město se změní na Paříž a odešle změny zpět do databáze.  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 Výstup tohoto kódu se zobrazí podobný následujícímu. Všimněte si, že souhrnu uplynutí ukazuje, že byly provedeny změny osm.  

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
  
## <a name="see-also"></a>Viz také:
- [Podpora ladění](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)

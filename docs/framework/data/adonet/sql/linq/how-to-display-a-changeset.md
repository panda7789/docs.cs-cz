---
title: 'Postupy: Zobrazení sady změn'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: 5f49e123e6e980501d330eeecf2719023cdff8e7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781961"
---
# <a name="how-to-display-a-changeset"></a>Postupy: Zobrazení sady změn
Můžete zobrazit změny, které sledují <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.DataContext.GetChangeSet%2A>pomocí.  
  
## <a name="example"></a>Příklad  
 Následující příklad načte zákazníky, jejichž město je Londýn, změní město na Paříž a odešle změny zpátky do databáze.  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 Výstup z tohoto kódu vypadá podobně jako následující. Všimněte si, že souhrn na konci ukazuje, že došlo k osmi změnám.  

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

- [Podpora ladění](debugging-support.md)

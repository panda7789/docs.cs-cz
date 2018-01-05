---
title: "Priorita operátorů (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: bc8ebd235016a22792d98e1a966e8c1217e2823e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="operator-precedence-entity-sql"></a>Priorita operátorů (entita SQL)
Když [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu má více operátorů, operátorů určuje pořadí, ve kterém se provádí operace. Pořadí zpracování může významně ovlivnit výsledek dotazu.  
  
 Operátory mají přednost před úrovně, uvedené v následující tabulce. Operátor s vyšší úrovní bude vyhodnocena před operátor s nižší úrovni.  
  
|úroveň|Typ operace|Operátor|  
|-----------|--------------------|--------------|  
|1|primární|`. , [] ()`|  
|2|Unární|`! not`|  
|3|Multiplikativní|`* / %`|  
|4|Doplňkové|`+ -`|  
|5|Řazení|`< > <= >=`|  
|6|Rovnost|`= != <>`|  
|7|Podmiňovací operátor AND|`and &&`|  
|8|Podmiňovací operátor OR|`or &#124;&#124;`|  
  
 Když dva operátory ve výrazu mít stejnou úroveň operátor přednost, vlevo se vyhodnocují na pravé straně na základě pozice v dotazu. Například `x+y-z` je vyhodnoceno jako `(x+y)-z`.  
  
 Závorky můžete použít k přepsání definovaná přednost operátorů v dotazu. Všechna data v závorkách vyhodnotí, je nejprve yield jeden výsledek před výsledek lze všechny operátorem mimo závorkách. Například `x+y*z` vynásobí `y` podle `z` a potom přidá `x`, ale `(x+y)*z` přidá `x` k `y` a potom vynásobí výsledek podle `z`.  
  
## <a name="see-also"></a>Viz také  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

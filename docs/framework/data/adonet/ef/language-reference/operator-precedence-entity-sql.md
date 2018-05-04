---
title: Priorita operátorů (entita SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: ab5158a2af18a422cb82f0d44412bcd85a04dc2a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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

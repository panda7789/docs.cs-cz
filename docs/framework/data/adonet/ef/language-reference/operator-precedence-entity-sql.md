---
title: Priorita operátorů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 2d8c78f410708fd1aa843ee8f14f7243a9f686c0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249786"
---
# <a name="operator-precedence-entity-sql"></a>Priorita operátorů (Entity SQL)
Pokud má [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz více operátorů, priorita operátorů určuje pořadí, ve kterém jsou operace prováděny. Pořadí spuštění může významně ovlivnit výsledek dotazu.  
  
 Operátory mají úrovně priority uvedené v následující tabulce. Operátor s vyšší úrovní je vyhodnocen před operátorem nižší úrovně.  
  
|Level|Typ operace|Operátor|  
|-----------|--------------------|--------------|  
|1|Primární|`. , [] ()`|  
|2|Unární|`! not`|  
|3|Multiplikativní|`* / %`|  
|4|Přičítáním|`+ -`|  
|5|Řazení|`< > <= >=`|  
|6|Rovnost|`= != <>`|  
|7|Podmiňovací operátor AND|`and &&`|  
|8|Podmiňovací operátor OR|`or &#124;&#124;`|  
  
 Pokud mají dva operátory ve výrazu stejnou úroveň priority operátora, jsou vyhodnoceny zleva doprava na základě jejich pozice v dotazu. Například `x+y-z` je vyhodnocen jako `(x+y)-z`.  
  
 Pomocí závorek můžete přepsat definovanou prioritu operátorů v dotazu. Vše v závorkách je nejprve vyhodnoceno a výsledkem je jeden výsledek, který může být použit libovolným operátorem mimo závorky. `x+y*z` Například `x` `z`vynásobí `z` apoté`x` přidá, ale `(x+y)*z` přidá do apakvynásobívýsledekhodnotou.`y` `y`  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)

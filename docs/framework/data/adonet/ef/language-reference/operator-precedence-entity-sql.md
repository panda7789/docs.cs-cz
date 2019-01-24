---
title: Priorita operátorů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: c68ac6d89426896b708ac74de1268f8ea8f193c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506833"
---
# <a name="operator-precedence-entity-sql"></a>Priorita operátorů (Entity SQL)
Když [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz obsahuje více operátorů, určuje priorita operátorů pořadí, ve kterém jsou operace prováděny. Pořadí provádění může významně ovlivnit výsledku dotazu.  
  
 Operátory mají přednost před úrovně je znázorněno v následující tabulce. Operátor s vyšší úrovní je vyhodnoceno před operátor s nižší úrovní.  
  
|úroveň|Typ operace|Operátor|  
|-----------|--------------------|--------------|  
|1|Primární|`. , [] ()`|  
|2|Unární|`! not`|  
|3|Násobení|`* / %`|  
|4|Additive|`+ -`|  
|5|Řazení|`< > <= >=`|  
|6|Rovnost|`= != <>`|  
|7|Podmiňovací operátor AND|`and &&`|  
|8|Podmiňovací operátor OR|`or &#124;&#124;`|  
  
 Když dva operátory ve výrazu dosahovat stejné úrovně priority operátoru, že jsou vyhodnoceny zleva doprava, na základě jejich pozice v dotazu. Například `x+y-z` se vyhodnotí jako `(x+y)-z`.  
  
 Můžete použít závorky k přepsání definovaná priorita operátorů v dotazu. Všechno, co v závorkách je vyhodnocen jako první pozastavit před jeden výsledek, výsledek je možné všechny operátorem mimo závorky. Například `x+y*z` vynásobí `y` podle `z` a pak přidá `x`, ale `(x+y)*z` přidá `x` k `y` a pak vynásobí výsledků `z`.  
  
## <a name="see-also"></a>Viz také:
- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

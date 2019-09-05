---
title: Proměnné (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 5be9c80c2fce877f179d79f6b2c22f11e31e65a0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248693"
---
# <a name="variables-entity-sql"></a>Proměnné (Entity SQL)
## <a name="variable"></a>Proměnná  
 Výraz proměnné je odkaz na pojmenovaný výraz definovaný v aktuálním oboru. Odkaz na proměnnou musí být platným [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifikátorem, jak je definováno v [identifikátorech](identifiers-entity-sql.md).  
  
 Následující příklad ukazuje použití proměnné ve výrazu. `c` V klauzuli FROM je definice proměnné. Použití `c` v klauzuli SELECT představuje odkaz na proměnnou.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Viz také:

- [Identifikátory](identifiers-entity-sql.md)
- [Parametry](parameters-entity-sql.md)
- [Přehled Entity SQL](entity-sql-overview.md)

---
title: Proměnné (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bf6fa95e38d1eb5817fd67165b6993cbb0755fd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879772"
---
# <a name="variables-entity-sql"></a>Proměnné (Entity SQL)
## <a name="variable"></a>Proměnná  
 Výraz proměnné je odkaz na pojmenovaný výraz v aktuálním oboru definována. Odkaz na proměnnou musí být platný [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifikátor, jak jsou definovány v [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Následující příklad ukazuje použití proměnné ve výrazu. `c` v z klauzule je definicí proměnné. Použití `c` vyberte v klauzuli představuje odkaz na proměnnou.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Viz také:

- [Identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)
- [Parametry](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)
- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

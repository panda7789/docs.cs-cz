---
title: Proměnné (entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 88ee41bc08711cf84b8b2e273c9ac0f4267d1d34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149814"
---
# <a name="variables-entity-sql"></a>Proměnné (entity SQL)
## <a name="variable"></a>Proměnná  
 Výraz proměnné je odkaz na pojmenovaný výraz definovaný v aktuálním oboru. Odkaz na proměnnou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musí být platný identifikátor, jak je definováno v [identifikátorech](identifiers-entity-sql.md).  
  
 Následující příklad ukazuje použití proměnné ve výrazu. V `c` from klauzule je definice proměnné. Použití `c` v select klauzule představuje odkaz na proměnnou.  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Viz také

- [Identifikátory](identifiers-entity-sql.md)
- [Parametry](parameters-entity-sql.md)
- [Přehled Entity SQL](entity-sql-overview.md)

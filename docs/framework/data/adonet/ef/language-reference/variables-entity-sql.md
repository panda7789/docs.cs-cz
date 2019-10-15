---
title: Proměnné (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bb8e6ebe81dacc7ec0f45fdde65b9c18cfd76789
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319192"
---
# <a name="variables-entity-sql"></a>Proměnné (Entity SQL)
## <a name="variable"></a>Proměnná  
 Výraz proměnné je odkaz na pojmenovaný výraz definovaný v aktuálním oboru. Odkaz na proměnnou musí být platným identifikátorem [!INCLUDE[esql](../../../../../../includes/esql-md.md)], jak je definováno v [identifikátorech](identifiers-entity-sql.md).  
  
 Následující příklad ukazuje použití proměnné ve výrazu. @No__t-0 v klauzuli FROM je definicí proměnné. Použití `c` v klauzuli SELECT představuje odkaz na proměnnou.  
  
```sql  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Viz také:

- [Identifikátory](identifiers-entity-sql.md)
- [Parametry](parameters-entity-sql.md)
- [Přehled Entity SQL](entity-sql-overview.md)

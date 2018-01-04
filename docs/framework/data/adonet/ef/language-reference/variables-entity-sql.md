---
title: "Proměnné (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: fff24c4572fab483c701a93167c0f229d5111d61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="variables-entity-sql"></a>Proměnné (entita SQL)
## <a name="variable"></a>Proměnná  
 Výraz proměnné je odkaz na výraz s názvem definované v aktuálním oboru. Odkaz na proměnnou, musí být platná [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifikátor, jak jsou definovány v [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Následující příklad ukazuje použití proměnné ve výrazu. `c` v od klauzule je definice proměnné. Použití `c` v SELECT klauzule představuje odkaz na proměnnou.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Viz také  
 [Identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [Parametry](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

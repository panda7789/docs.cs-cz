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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d035f8d5616f2eb4c5a4db31857da2be0cd3d930
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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

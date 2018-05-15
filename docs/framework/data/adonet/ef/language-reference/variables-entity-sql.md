---
title: Proměnné (entita SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: f271ffc31875e7d94a27f4752b71bfe508fcb620
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="variables-entity-sql"></a><span data-ttu-id="a46cc-102">Proměnné (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="a46cc-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="a46cc-103">Proměnná</span><span class="sxs-lookup"><span data-stu-id="a46cc-103">Variable</span></span>  
 <span data-ttu-id="a46cc-104">Výraz proměnné je odkaz na výraz s názvem definované v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="a46cc-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="a46cc-105">Odkaz na proměnnou, musí být platná [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifikátor, jak jsou definovány v [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a46cc-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="a46cc-106">Následující příklad ukazuje použití proměnné ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="a46cc-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="a46cc-107">`c` v od klauzule je definice proměnné.</span><span class="sxs-lookup"><span data-stu-id="a46cc-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="a46cc-108">Použití `c` v SELECT klauzule představuje odkaz na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="a46cc-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="a46cc-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a46cc-109">See Also</span></span>  
 [<span data-ttu-id="a46cc-110">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="a46cc-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="a46cc-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="a46cc-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="a46cc-112">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a46cc-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

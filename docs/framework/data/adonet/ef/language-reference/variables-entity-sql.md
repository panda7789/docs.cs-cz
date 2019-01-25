---
title: Proměnné (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: a16c450401eee1021aeef885fba129c943a87fd7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742265"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="20294-102">Proměnné (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="20294-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="20294-103">Proměnná</span><span class="sxs-lookup"><span data-stu-id="20294-103">Variable</span></span>  
 <span data-ttu-id="20294-104">Výraz proměnné je odkaz na pojmenovaný výraz v aktuálním oboru definována.</span><span class="sxs-lookup"><span data-stu-id="20294-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="20294-105">Odkaz na proměnnou musí být platný [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifikátor, jak jsou definovány v [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="20294-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="20294-106">Následující příklad ukazuje použití proměnné ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="20294-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="20294-107">`c` v z klauzule je definicí proměnné.</span><span class="sxs-lookup"><span data-stu-id="20294-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="20294-108">Použití `c` vyberte v klauzuli představuje odkaz na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="20294-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="20294-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20294-109">See also</span></span>
- [<span data-ttu-id="20294-110">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="20294-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)
- [<span data-ttu-id="20294-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="20294-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)
- [<span data-ttu-id="20294-112">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="20294-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

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
# <a name="variables-entity-sql"></a><span data-ttu-id="e2058-102">Proměnné (entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e2058-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="e2058-103">Proměnná</span><span class="sxs-lookup"><span data-stu-id="e2058-103">Variable</span></span>  
 <span data-ttu-id="e2058-104">Výraz proměnné je odkaz na pojmenovaný výraz definovaný v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="e2058-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="e2058-105">Odkaz na proměnnou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musí být platný identifikátor, jak je definováno v [identifikátorech](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e2058-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="e2058-106">Následující příklad ukazuje použití proměnné ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="e2058-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="e2058-107">V `c` from klauzule je definice proměnné.</span><span class="sxs-lookup"><span data-stu-id="e2058-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="e2058-108">Použití `c` v select klauzule představuje odkaz na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="e2058-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2058-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2058-109">See also</span></span>

- [<span data-ttu-id="e2058-110">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="e2058-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="e2058-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2058-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="e2058-112">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e2058-112">Entity SQL Overview</span></span>](entity-sql-overview.md)

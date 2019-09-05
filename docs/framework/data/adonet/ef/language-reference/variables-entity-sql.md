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
# <a name="variables-entity-sql"></a><span data-ttu-id="aa86d-102">Proměnné (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="aa86d-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="aa86d-103">Proměnná</span><span class="sxs-lookup"><span data-stu-id="aa86d-103">Variable</span></span>  
 <span data-ttu-id="aa86d-104">Výraz proměnné je odkaz na pojmenovaný výraz definovaný v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="aa86d-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="aa86d-105">Odkaz na proměnnou musí být platným [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifikátorem, jak je definováno v [identifikátorech](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="aa86d-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="aa86d-106">Následující příklad ukazuje použití proměnné ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="aa86d-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="aa86d-107">`c` V klauzuli FROM je definice proměnné.</span><span class="sxs-lookup"><span data-stu-id="aa86d-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="aa86d-108">Použití `c` v klauzuli SELECT představuje odkaz na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="aa86d-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa86d-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa86d-109">See also</span></span>

- [<span data-ttu-id="aa86d-110">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="aa86d-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="aa86d-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa86d-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="aa86d-112">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="aa86d-112">Entity SQL Overview</span></span>](entity-sql-overview.md)

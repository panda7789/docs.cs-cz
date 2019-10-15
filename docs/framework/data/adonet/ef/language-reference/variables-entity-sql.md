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
# <a name="variables-entity-sql"></a><span data-ttu-id="67e17-102">Proměnné (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="67e17-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="67e17-103">Proměnná</span><span class="sxs-lookup"><span data-stu-id="67e17-103">Variable</span></span>  
 <span data-ttu-id="67e17-104">Výraz proměnné je odkaz na pojmenovaný výraz definovaný v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="67e17-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="67e17-105">Odkaz na proměnnou musí být platným identifikátorem [!INCLUDE[esql](../../../../../../includes/esql-md.md)], jak je definováno v [identifikátorech](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="67e17-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="67e17-106">Následující příklad ukazuje použití proměnné ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="67e17-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="67e17-107">@No__t-0 v klauzuli FROM je definicí proměnné.</span><span class="sxs-lookup"><span data-stu-id="67e17-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="67e17-108">Použití `c` v klauzuli SELECT představuje odkaz na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="67e17-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="67e17-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67e17-109">See also</span></span>

- [<span data-ttu-id="67e17-110">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="67e17-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="67e17-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="67e17-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="67e17-112">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="67e17-112">Entity SQL Overview</span></span>](entity-sql-overview.md)

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
# <a name="variables-entity-sql"></a><span data-ttu-id="673b9-102">Proměnné (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="673b9-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="673b9-103">Proměnná</span><span class="sxs-lookup"><span data-stu-id="673b9-103">Variable</span></span>  
 <span data-ttu-id="673b9-104">Výraz proměnné je odkaz na výraz s názvem definované v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="673b9-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="673b9-105">Odkaz na proměnnou, musí být platná [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifikátor, jak jsou definovány v [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="673b9-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="673b9-106">Následující příklad ukazuje použití proměnné ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="673b9-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="673b9-107">`c` v od klauzule je definice proměnné.</span><span class="sxs-lookup"><span data-stu-id="673b9-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="673b9-108">Použití `c` v SELECT klauzule představuje odkaz na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="673b9-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="673b9-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="673b9-109">See Also</span></span>  
 [<span data-ttu-id="673b9-110">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="673b9-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="673b9-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="673b9-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="673b9-112">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="673b9-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

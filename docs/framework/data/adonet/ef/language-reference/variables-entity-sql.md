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
# <a name="variables-entity-sql"></a><span data-ttu-id="449b1-102">Proměnné (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="449b1-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="449b1-103">Proměnná</span><span class="sxs-lookup"><span data-stu-id="449b1-103">Variable</span></span>  
 <span data-ttu-id="449b1-104">Výraz proměnné je odkaz na výraz s názvem definované v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="449b1-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="449b1-105">Odkaz na proměnnou, musí být platná [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifikátor, jak jsou definovány v [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="449b1-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="449b1-106">Následující příklad ukazuje použití proměnné ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="449b1-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="449b1-107">`c` v od klauzule je definice proměnné.</span><span class="sxs-lookup"><span data-stu-id="449b1-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="449b1-108">Použití `c` v SELECT klauzule představuje odkaz na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="449b1-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="449b1-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="449b1-109">See Also</span></span>  
 [<span data-ttu-id="449b1-110">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="449b1-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="449b1-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="449b1-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="449b1-112">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="449b1-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

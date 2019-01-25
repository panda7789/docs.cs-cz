---
title: Parametry (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 5fa050e43e4590f61c3011a1b9bb0937da7032a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632384"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="f012f-102">Parametry (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f012f-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="f012f-103">Parametry jsou proměnné, které jsou definovány mimo [!INCLUDE[esql](../../../../../../includes/esql-md.md)], obvykle prostřednictvím rozhraní API vazby, který používá hostitelský jazyk.</span><span class="sxs-lookup"><span data-stu-id="f012f-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="f012f-104">Každý parametr má název a typ.</span><span class="sxs-lookup"><span data-stu-id="f012f-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="f012f-105">Názvy parametrů jsou definovány ve výrazech dotazů s v (@) symbol jako předponu.</span><span class="sxs-lookup"><span data-stu-id="f012f-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="f012f-106">Jim umožňuje to rozlišit názvy vlastností nebo jiné názvy, které jsou definovány v dotazu.</span><span class="sxs-lookup"><span data-stu-id="f012f-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="f012f-107">Rozhraní API pro hostitelský jazyk vazby poskytuje rozhraní API pro vazby parametrů.</span><span class="sxs-lookup"><span data-stu-id="f012f-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f012f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f012f-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="f012f-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f012f-109">See also</span></span>
- [<span data-ttu-id="f012f-110">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f012f-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="f012f-111">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f012f-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

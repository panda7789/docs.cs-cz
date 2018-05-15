---
title: Parametry (entita SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: c8bdb54e52b4c0d189f3bff72bdb24785c1a9c27
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="a02d3-102">Parametry (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="a02d3-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="a02d3-103">Parametry jsou proměnné, které jsou definované mimo [!INCLUDE[esql](../../../../../../includes/esql-md.md)], obvykle prostřednictvím rozhraní API vazby, který je používán hostitelského jazyka.</span><span class="sxs-lookup"><span data-stu-id="a02d3-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="a02d3-104">Každý parametr má název a typ.</span><span class="sxs-lookup"><span data-stu-id="a02d3-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="a02d3-105">Názvy parametrů jsou definovány ve výrazech dotazů s na na (@) symbol jako předponu.</span><span class="sxs-lookup"><span data-stu-id="a02d3-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="a02d3-106">Je umožňuje to rozlišit z názvů vlastností nebo jiné názvy, které jsou definovány v dotazu.</span><span class="sxs-lookup"><span data-stu-id="a02d3-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="a02d3-107">Rozhraní API vazba hostitelského jazyka poskytuje rozhraní API pro vazby parametrů.</span><span class="sxs-lookup"><span data-stu-id="a02d3-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a02d3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a02d3-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="a02d3-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a02d3-109">See Also</span></span>  
 [<span data-ttu-id="a02d3-110">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a02d3-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="a02d3-111">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a02d3-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

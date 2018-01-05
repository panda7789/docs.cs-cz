---
title: Parametry (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4cbc13433b742cea1063cbd284690ce8cabbbfc4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="f4239-102">Parametry (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="f4239-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="f4239-103">Parametry jsou proměnné, které jsou definované mimo [!INCLUDE[esql](../../../../../../includes/esql-md.md)], obvykle prostřednictvím rozhraní API vazby, který je používán hostitelského jazyka.</span><span class="sxs-lookup"><span data-stu-id="f4239-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="f4239-104">Každý parametr má název a typ.</span><span class="sxs-lookup"><span data-stu-id="f4239-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="f4239-105">Názvy parametrů jsou definovány ve výrazech dotazů s na na (@) symbol jako předponu.</span><span class="sxs-lookup"><span data-stu-id="f4239-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="f4239-106">Je umožňuje to rozlišit z názvů vlastností nebo jiné názvy, které jsou definovány v dotazu.</span><span class="sxs-lookup"><span data-stu-id="f4239-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="f4239-107">Rozhraní API vazba hostitelského jazyka poskytuje rozhraní API pro vazby parametrů.</span><span class="sxs-lookup"><span data-stu-id="f4239-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4239-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4239-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4239-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4239-109">See Also</span></span>  
 [<span data-ttu-id="f4239-110">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f4239-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="f4239-111">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f4239-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

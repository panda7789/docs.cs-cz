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
ms.openlocfilehash: 2a3700b5f9bdc996b147609d86bcaed0ec0bb116
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="8b5f5-102">Parametry (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="8b5f5-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="8b5f5-103">Parametry jsou proměnné, které jsou definované mimo [!INCLUDE[esql](../../../../../../includes/esql-md.md)], obvykle prostřednictvím rozhraní API vazby, který je používán hostitelského jazyka.</span><span class="sxs-lookup"><span data-stu-id="8b5f5-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="8b5f5-104">Každý parametr má název a typ.</span><span class="sxs-lookup"><span data-stu-id="8b5f5-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="8b5f5-105">Názvy parametrů jsou definovány ve výrazech dotazů s na na (@) symbol jako předponu.</span><span class="sxs-lookup"><span data-stu-id="8b5f5-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="8b5f5-106">Je umožňuje to rozlišit z názvů vlastností nebo jiné názvy, které jsou definovány v dotazu.</span><span class="sxs-lookup"><span data-stu-id="8b5f5-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="8b5f5-107">Rozhraní API vazba hostitelského jazyka poskytuje rozhraní API pro vazby parametrů.</span><span class="sxs-lookup"><span data-stu-id="8b5f5-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b5f5-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b5f5-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b5f5-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b5f5-109">See Also</span></span>  
 [<span data-ttu-id="8b5f5-110">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="8b5f5-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="8b5f5-111">Přehled SQL entity</span><span class="sxs-lookup"><span data-stu-id="8b5f5-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

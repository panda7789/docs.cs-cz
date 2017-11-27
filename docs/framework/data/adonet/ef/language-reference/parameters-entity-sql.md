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
# <a name="parameters-entity-sql"></a>Parametry (entita SQL)
Parametry jsou proměnné, které jsou definované mimo [!INCLUDE[esql](../../../../../../includes/esql-md.md)], obvykle prostřednictvím rozhraní API vazby, který je používán hostitelského jazyka. Každý parametr má název a typ. Názvy parametrů jsou definovány ve výrazech dotazů s na na (@) symbol jako předponu. Je umožňuje to rozlišit z názvů vlastností nebo jiné názvy, které jsou definovány v dotazu.  
  
 Rozhraní API vazba hostitelského jazyka poskytuje rozhraní API pro vazby parametrů.  
  
## <a name="example"></a>Příklad  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Přehled SQL entity](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

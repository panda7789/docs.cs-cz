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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bb631a752bfe0e741b654ec6774a14c82c89157c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

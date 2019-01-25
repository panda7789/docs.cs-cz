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
# <a name="parameters-entity-sql"></a>Parametry (Entity SQL)
Parametry jsou proměnné, které jsou definovány mimo [!INCLUDE[esql](../../../../../../includes/esql-md.md)], obvykle prostřednictvím rozhraní API vazby, který používá hostitelský jazyk. Každý parametr má název a typ. Názvy parametrů jsou definovány ve výrazech dotazů s v (@) symbol jako předponu. Jim umožňuje to rozlišit názvy vlastností nebo jiné názvy, které jsou definovány v dotazu.  
  
 Rozhraní API pro hostitelský jazyk vazby poskytuje rozhraní API pro vazby parametrů.  
  
## <a name="example"></a>Příklad  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>Viz také:
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

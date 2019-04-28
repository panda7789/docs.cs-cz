---
title: Parametry (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 47a1514933904daa623adc151d50525f011e07a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760241"
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

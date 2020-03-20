---
title: Parametry (entita SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: e1bb633f7f7c7908a5f424991f20a5cd89aee5aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150011"
---
# <a name="parameters-entity-sql"></a>Parametry (entita SQL)
Parametry jsou proměnné, které [!INCLUDE[esql](../../../../../../includes/esql-md.md)]jsou definovány mimo , obvykle prostřednictvím rozhraní API vazby, které používá hostitelský jazyk. Každý parametr má název a typ. Názvy parametrů jsou definovány ve výrazech dotazu se symbolem at (@) jako předponou. To je rozptýluje od názvů vlastností nebo jiných názvů, které jsou definovány v dotazu.  
  
 Rozhraní API vazby hostitelského jazyka poskytuje rozhraní API pro parametry vazby.  
  
## <a name="example"></a>Příklad  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a>Viz také

- [Reference k Entity SQL](entity-sql-reference.md)
- [Přehled Entity SQL](entity-sql-overview.md)

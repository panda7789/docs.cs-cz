---
title: Parametry (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 8fbca4f10a7c2c3dbaffff978a536b87d31a8df4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319435"
---
# <a name="parameters-entity-sql"></a>Parametry (Entity SQL)
Parametry jsou proměnné, které jsou definovány mimo [!INCLUDE[esql](../../../../../../includes/esql-md.md)], obvykle prostřednictvím rozhraní API vazby, které používá jazyk hostitele. Každý parametr má název a typ. Názvy parametrů jsou definovány ve výrazech dotazů s symbolem (@) jako předponou. Tato vlastnost je nejednoznačná od názvů vlastností nebo jiných názvů, které jsou definovány v dotazu.  
  
 Rozhraní API pro vázání v hostitelském jazyce poskytuje rozhraní API pro parametry vazby.  
  
## <a name="example"></a>Příklad  
  
```sql  
SELECT c   
      FROM LOB.Customers AS c   
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Přehled Entity SQL](entity-sql-overview.md)

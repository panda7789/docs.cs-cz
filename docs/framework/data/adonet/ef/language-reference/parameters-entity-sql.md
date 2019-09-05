---
title: Parametry (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 723e40f523f8bb573e0ffcb1863ed0c082ea9d8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249589"
---
# <a name="parameters-entity-sql"></a>Parametry (Entity SQL)
Parametry jsou proměnné, které jsou definovány [!INCLUDE[esql](../../../../../../includes/esql-md.md)]mimo, obvykle prostřednictvím rozhraní API vazby, které používá jazyk hostitele. Každý parametr má název a typ. Názvy parametrů jsou definovány ve výrazech dotazů s symbolem (@) jako předponou. Tato vlastnost je nejednoznačná od názvů vlastností nebo jiných názvů, které jsou definovány v dotazu.  
  
 Rozhraní API pro vázání v hostitelském jazyce poskytuje rozhraní API pro parametry vazby.  
  
## <a name="example"></a>Příklad  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Přehled Entity SQL](entity-sql-overview.md)

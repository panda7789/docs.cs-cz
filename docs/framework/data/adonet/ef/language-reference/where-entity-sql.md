---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 8dd0e34a6669b2147052befb17b8f4ff8395aabc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248483"
---
# <a name="where-entity-sql"></a>WHERE (Entity SQL)
Klauzule WHERE je použita přímo za klauzulí [from](from-entity-sql.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Typ Boolean.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule WHERE má stejnou sémantiku, jak je popsáno v jazyce Transact-SQL. Omezuje objekty, které jsou vyprodukovány výrazem dotazu, omezením prvků zdrojových kolekcí na ty, které podmínku přecházejí.  
  
```  
select c from cs as c where e  
```  
  
 Výraz `e` musí být typu Boolean.  
  
 Klauzule WHERE se aplikuje přímo za klauzulí FROM a předtím, než se provede jakékoli seskupení, řazení nebo projekce. Všechny názvy elementů definované v klauzuli FROM jsou viditelné pro výraz klauzule WHERE.  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Výrazy dotazu](query-expressions-entity-sql.md)

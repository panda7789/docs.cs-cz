---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: b551d15d7de2cf07afc7455b7fd0a0faf6436ccf
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319187"
---
# <a name="where-entity-sql"></a>WHERE (Entity SQL)
Klauzule WHERE je použita přímo za klauzulí [from](from-entity-sql.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Typ Boolean.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule WHERE má stejnou sémantiku, jak je popsáno v jazyce Transact-SQL. Omezuje objekty, které jsou vyprodukovány výrazem dotazu, omezením prvků zdrojových kolekcí na ty, které podmínku přecházejí.  
  
```sql  
select c from cs as c where e  
```  
  
 Výraz `e` musí mít typ Boolean.  
  
 Klauzule WHERE se aplikuje přímo za klauzulí FROM a předtím, než se provede jakékoli seskupení, řazení nebo projekce. Všechny názvy elementů definované v klauzuli FROM jsou viditelné pro výraz klauzule WHERE.  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Výrazy dotazu](query-expressions-entity-sql.md)

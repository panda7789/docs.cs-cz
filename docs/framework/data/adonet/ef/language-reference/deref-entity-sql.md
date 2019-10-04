---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 27fc23a2be47ea00eff20aa8d2f559af5ae90387
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833895"
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)
Odkazuje na referenční hodnotu a vytvoří výsledek tohoto předaného odkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrací kolekci.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota odkazované entity  
  
## <a name="remarks"></a>Poznámky  
 Operátor DEREF odkazuje na referenční hodnotu a generuje výsledek tohoto odkázání. Například pokud `r` je odkaz typu ref @ no__t-1T >, `Deref(r)` je výraz typu `T`, který vede k entitě, na kterou odkazuje `r`. Pokud má referenční hodnota hodnotu null nebo je dangling (to znamená, že cíl odkazu neexistuje), výsledek operátoru DEREF má hodnotu null.  
  
## <a name="example"></a>Příklad  
 Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá operátor DEREF k tomu, aby převedl odkaz na referenční hodnotu a vytvořil výsledek tohoto odkázání. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat následující dotaz jako argument metodě ExecutePrimitiveTypeQuery:  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [REF](ref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [Strukturované typy s možnou hodnotou Null](nullable-structured-types-entity-sql.md)

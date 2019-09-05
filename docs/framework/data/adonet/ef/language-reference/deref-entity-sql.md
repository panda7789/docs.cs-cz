---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 10c5ecb2b44c85dccd758cc1cf63a152da045cc1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251082"
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)
Odkazuje na referenční hodnotu a vytvoří výsledek tohoto předaného odkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrací kolekci.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota odkazované entity  
  
## <a name="remarks"></a>Poznámky  
 Operátor DEREF odkazuje na referenční hodnotu a generuje výsledek tohoto odkázání. Například `r` Pokud je odkaz typu ref\<T >, `Deref(r)` je výraz typu `T` , který má za důsledek entitu, na kterou odkazuje `r`. Pokud má referenční hodnota hodnotu null nebo je dangling (to znamená, že cíl odkazu neexistuje), výsledek operátoru DEREF má hodnotu null.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz pomocí operátoru DEREF odkazuje na referenční hodnotu a vytvoří výsledek tohoto zpětného odkazu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.  
  
2. Předat následující dotaz jako argument metodě ExecutePrimitiveTypeQuery:  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [REF](ref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [Strukturované typy s možnou hodnotou Null](nullable-structured-types-entity-sql.md)

---
title: PAK (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: ba01a978c53b58f7e6c1ac9bc42a97277ac64bbc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319287"
---
# <a name="then-entity-sql"></a>PAK (Entity SQL)
Výsledek klauzule WHEN, když se vyhodnotí jako `true`.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `when_expression`  
 Libovolný platný logický výraz.  
  
 `then_expression`  
 Libovolný platný výraz dotazu, který vrací kolekci.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `when_expression` se vyhodnotí na hodnotu `true`, výsledkem bude odpovídající `then-expression`. Pokud žádné podmínky if nejsou splněné, je vyhodnocena hodnota `else-expression`. Pokud však není `else-expression`, výsledkem je hodnota null.  
  
 Příklad naleznete v tématu [case](case-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá výraz CASE k vyhodnocení sady výrazů `Boolean`. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecutePrimitiveTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a>Viz také:

- [CASE](case-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)

---
title: POTOM (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: d5f9f2b8c9d7397cbcd91fa52a95544fc66e4dce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184587"
---
# <a name="then-entity-sql"></a>POTOM (Entity SQL)
Výsledek klauzuli WHEN, když je vyhodnocen jako `true`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `when_expression`  
 Libovolný platný výraz Boolean.  
  
 `then_expression`  
 Libovolný výraz platný dotaz, který vrátí kolekci.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `when_expression` vyhodnocen na hodnotu `true`, výsledkem je odpovídající `then-expression`. Pokud není k dispozici z WHEN podmínky splněny, `else-expression` je vyhodnocen. Ale pokud neexistuje žádný `else-expression`, výsledek je null.  
  
 Příklad najdete v tématu [případ](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá k vyhodnocení sady výraz CASE `Boolean` výrazy. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Viz také:

- [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

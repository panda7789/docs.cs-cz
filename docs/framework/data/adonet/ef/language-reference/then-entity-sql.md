---
title: PAK (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: c64e440e8cd8f86706db69d923ba7085d0cb3b3a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248993"
---
# <a name="then-entity-sql"></a>PAK (Entity SQL)
Výsledek klauzule WHEN při vyhodnocování `true`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `when_expression`  
 Libovolný platný logický výraz.  
  
 `then_expression`  
 Libovolný platný výraz dotazu, který vrací kolekci.  
  
## <a name="remarks"></a>Poznámky  
 Je `when_expression` -li hodnota vyhodnocena na hodnotu `true`, výsledek je `then-expression`odpovídající. Pokud žádné podmínky if nejsou splněné, `else-expression` je vyhodnocena. Pokud ale ne `else-expression`, výsledek je null.  
  
 Příklad naleznete v tématu [case](case-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá výraz Case k vyhodnocení sady `Boolean` výrazů. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.  
  
2. Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Viz také:

- [CASE](case-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)

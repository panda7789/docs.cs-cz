---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 41036e629837bd5861368df545bed9423eac5b23
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251285"
---
# <a name="between-entity-sql"></a>BETWEEN (Entity SQL)
Určuje, zda výraz má za následek hodnotu v zadaném rozsahu. Výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Between má stejné funkce jako výraz Transact-SQL Between.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz pro otestování v rozsahu definovaném `begin_expression` a. `end_expression` `expression`musí být stejný typ jako i `begin_expression`. `end_expression`  
  
 `begin_expression`  
 Libovolný platný výraz. `begin_expression`musí být stejný typ jako i `expression`. `end_expression` `begin_expression`hodnota by měla být `end_expression`menší než, jinak vrácená hodnota bude negace.  
  
 `end_expression`  
 Libovolný platný výraz. `end_expression`musí být stejný typ jako i `expression`. `begin_expression`  
  
 NOT  
 Určuje, že výsledek mezi je negace.  
  
 AND  
 Funguje jako zástupný symbol, který `expression` indikuje, že by měl být v `begin_expression` rozsahu `end_expression`uvedeném a.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`, `expression` Pokud je mezi rozsahem, `begin_expression` který `end_expression`je určen a `false`; jinak. `null`Vrátí se, pokud `expression` je `null` , nebo `begin_expression` `end_expression` Pokud`null`je.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li určit výhradní rozsah, použijte operátory větší než (>) a menší než (<) místo mezi.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor BETWEEN k určení, zda výraz má za následek hodnotu v zadaném rozsahu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)

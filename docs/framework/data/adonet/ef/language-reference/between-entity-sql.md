---
title: MEZI (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: a0f5dd19c439861451b1e88c3ae35f9f265288fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150490"
---
# <a name="between-entity-sql"></a>MEZI (Entita SQL)
Určuje, zda má výraz za následek hodnotu v zadaném rozsahu. Výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] MEZI má stejné funkce jako výraz Transact-SQL MEZI.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Libovolný platný výraz, který chcete `begin_expression` testovat `end_expression`v rozsahu definovaném písmenem a). `expression`musí být stejného `begin_expression` typu `end_expression`jako oba a .  
  
 `begin_expression`  
 Libovolný platný výraz `begin_expression`musí být stejného `expression` typu `end_expression`jako oba a . `begin_expression`by měla `end_expression`být menší než , jinak bude vrácená hodnota negována.  
  
 `end_expression`  
 Libovolný platný výraz `end_expression`musí být stejného `expression` typu `begin_expression`jako oba a .  
  
 NOT  
 Určuje, že výsledek between být negována.  
  
 AND  
 Funguje jako zástupný `expression` symbol, který označuje by `begin_expression` `end_expression`měl být v rozsahu označeném a .  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`jestliže `expression` se nachází mezi `begin_expression` `end_expression`rozsahem označeným písmenem a) a b); v `false`opačném případě . `null`bude vrácena, `null` pokud `begin_expression` `end_expression` `null` `expression` je nebo pokud nebo je .  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li určit výhradní rozsah, použijte operátory větší než (>) a menší než (<) namísto BETWEEN.  
  
## <a name="example"></a>Příklad  
 Následující entita SQL dotaz používá operátor MEZI k určení, zda výraz má za následek hodnotu v zadanéoblasti. Dotaz je založen na adventureworks prodejní model. Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:  
  
1. Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Viz také

- [Reference k Entity SQL](entity-sql-reference.md)

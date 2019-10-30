---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 611e90f362bbc0eac521e1e1998fb85200169c19
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039939"
---
# <a name="between-entity-sql"></a>BETWEEN (Entity SQL)
Určuje, zda výraz má za následek hodnotu v zadaném rozsahu. Výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] mezi výrazem má stejné funkce jako výraz Transact-SQL BETWEEN.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz pro otestování v rozsahu definovaném `begin_expression` a `end_expression`. `expression` musí být stejného typu jako `begin_expression` i `end_expression`.  
  
 `begin_expression`  
 Libovolný platný výraz. `begin_expression` musí být stejného typu jako `expression` i `end_expression`. `begin_expression` by měl být menší než `end_expression`, jinak vrácená hodnota bude negace.  
  
 `end_expression`  
 Libovolný platný výraz. `end_expression` musí být stejného typu jako `expression` i `begin_expression`.  
  
 MĚNÍ  
 Určuje, že výsledek mezi je negace.  
  
 AND  
 Funguje jako zástupný symbol, který indikuje, že `expression` by měl být v rozsahu uvedeném `begin_expression` a `end_expression`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`, je-li `expression` mezi rozsahem určeným `begin_expression` a `end_expression`; v opačném případě `false`. Pokud je `expression` `null` nebo pokud `begin_expression` nebo `end_expression` `null`, vrátí se `null`.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li určit výhradní rozsah, použijte operátory větší než (>) a menší než (<) místo mezi.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor BETWEEN k určení, zda výraz má za následek hodnotu v zadaném rozsahu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)

---
title: PŘÍPAD (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 7c1e02d44c674bf262f92df1c43bec6e9f2143c5
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039932"
---
# <a name="case-entity-sql"></a>PŘÍPAD (Entity SQL)
Vyhodnocuje sadu `Boolean` výrazů pro určení výsledku.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Je zástupný symbol, který označuje, že je možné použít více `Boolean_expression` klauzulí `result_expression`.  
  
 PAK `result_expression`  
 Je výraz vrácený, když `Boolean_expression` vyhodnocuje jako `true`. `result expression` je libovolný platný výraz.  
  
 JINAK `else_result_expression`  
 Je výraz vrácený, pokud není vyhodnocena žádná operace porovnávání `true`. Pokud je tento argument vynechán a žádná operace porovnání není vyhodnocena jako `true`, CASE vrátí hodnotu null. `else_result_expression` je libovolný platný výraz. Datové typy `else_result_expression` a všechny `result_expression` musí být stejné nebo musí být implicitní převod.  
  
 Při `Boolean_expression`  
 Je výraz `Boolean` vyhodnocen při použití formátu případu hledání. `Boolean_expression` je libovolný platný výraz `Boolean`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí nejvyšší prioritu typu ze sady typů v `result_expression` a volitelné `else_result_expression`.  
  
## <a name="remarks"></a>Poznámky  
 Výraz Case [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se podobá výrazu Case jazyka Transact-SQL. Výraz Case použijete k vytvoření řady podmíněných testů, které určují, který výraz bude poskytovat odpovídající výsledek. Tato forma výrazu Case se vztahuje na řadu jednoho nebo více `Boolean` výrazů pro určení správného výsledného výrazu.  
  
 Funkce CASE vyhodnocuje `Boolean_expression` pro každou klauzuli WHEN v zadaném pořadí a vrátí `result_expression` prvního `Boolean_expression`, který se vyhodnotí jako `true`. Zbývající výrazy nejsou vyhodnocovány. Pokud není `Boolean_expression` vyhodnocena jako `true`, databázový stroj vrátí `else_result_expression`, pokud je zadána klauzule ELSE, nebo hodnotu null, pokud není zadána klauzule ELSE.  
  
 Příkaz CASE nemůže vracet multiset.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá výraz CASE k vyhodnocení sady `Boolean` výrazů za účelem určení výsledku. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecutePrimitiveTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Viz také:

- [THEN](then-entity-sql.md)
- [SELECT](select-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)

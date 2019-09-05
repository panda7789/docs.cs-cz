---
title: PŘÍPAD (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 79544f4180313a008669c56c4f2740c889043c6d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251251"
---
# <a name="case-entity-sql"></a>PŘÍPAD (Entity SQL)
Vyhodnotí sadu `Boolean` výrazů pro určení výsledku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Je zástupný symbol, který označuje, že `Boolean_expression` lze `result_expression` použít více klauzulí When Then.  
  
 STISKNUTÍM`result_expression`  
 Je výraz vrácený při `Boolean_expression` vyhodnocování. `true` `result expression`je libovolný platný výraz.  
  
 ELSE `else_result_expression`  
 Je výraz vrácený, pokud není vyhodnocena `true`žádná operace porovnání. Pokud je tento argument vynechán a žádná operace porovnání není vyhodnocena `true`jako, vrátí Case hodnotu null. `else_result_expression`je libovolný platný výraz. Datové typy `else_result_expression` a Any `result_expression` musí být stejné nebo musí být implicitní převod.  
  
 KDY`Boolean_expression`  
 `Boolean` Je výraz vyhodnocen při použití formátu případu hledání. `Boolean_expression`je libovolný platný `Boolean` výraz.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí nejvyšší prioritu typu ze sady typů v `result_expression` a volitelné. `else_result_expression`  
  
## <a name="remarks"></a>Poznámky  
 Výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Case se podobá výrazu Case Transact-SQL. Výraz Case použijete k vytvoření řady podmíněných testů, které určují, který výraz bude poskytovat odpovídající výsledek. Tato forma výrazu Case se vztahuje na řadu jednoho nebo více `Boolean` výrazů pro určení správného výsledného výrazu.  
  
 Funkce Case vyhodnocuje `Boolean_expression` každou klauzuli when v zadaném pořadí a vrátí `result_expression` `true`první `Boolean_expression` , která je vyhodnocena jako. Zbývající výrazy nejsou vyhodnocovány. Pokud není `true`vyhodnocena, databázový stroj vrátí `else_result_expression` klauzuli if, pokud je zadána klauzule else, nebo hodnotu null, pokud není zadána klauzule else. `Boolean_expression`  
  
 Příkaz CASE nemůže vracet multiset.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá výraz Case k vyhodnocení sady `Boolean` výrazů za účelem určení výsledku. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.  
  
2. Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Viz také:

- [THEN](then-entity-sql.md)
- [SELECT](select-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)

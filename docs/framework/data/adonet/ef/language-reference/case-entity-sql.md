---
title: PŘÍPAD (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: e44f48d040fc77bf702759be0c53a618cd84f9fc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334884"
---
# <a name="case-entity-sql"></a>PŘÍPAD (Entity SQL)
Vyhodnotí sadu `Boolean` výrazy k určení výsledků.  
  
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
 Je zástupný symbol, který označuje, že více při `Boolean_expression` pak `result_expression` klauzule můžete použít.  
  
 THEN `result_expression`  
 Výraz dochází při `Boolean_expression` vyhodnotí jako `true`. `result expression` Je libovolný platný výraz.  
  
 ELSE `else_result_expression`  
 Se výraz vrátí, pokud žádná operace porovnání vyhodnocen `true`. Pokud je tento argument vynechán a žádná operace porovnání vyhodnocen jako `true`, případě vrátí hodnotu null. `else_result_expression` Je libovolný platný výraz. Datové typy `else_result_expression` a jakékoli `result_expression` musí být stejný nebo musí být proveden implicitní převod.  
  
 KDY `Boolean_expression`  
 Je `Boolean` výraz vyhodnocen při použití hledaný případu formátu. `Boolean_expression` je libovolný platný `Boolean` výrazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí nejvyšší prioritu typ ze sady typů v `result_expression` a volitelné `else_result_expression`.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Výraz case vypadá podobně jako [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] výraz malá a velká. Výraz case můžete provádět řadu podmíněné testů, abyste zjistili výrazu, který předá odpovídající výsledek. Tato forma výraz case se vztahuje na řadu jeden nebo více `Boolean` výrazy k určení správné výsledný výraz.  
  
 Funkce CASE se vyhodnotí `Boolean_expression` pro každou klauzuli WHEN v pořadí zadané a vrátí `result_expression` prvního `Boolean_expression` vyhodnocenou nečíselnou `true`. Zbývající výrazy se nevyhodnocují. Pokud ne `Boolean_expression` vyhodnotí jako `true`, vrátí databázový stroj `else_result_expression` Pokud není zadána klauzule ELSE, nebo hodnotu null, pokud není zadána žádná klauzule ELSE.  
  
 CASE – příkaz nemůže vrátit použita třída multiset.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá k vyhodnocení sady výraz CASE `Boolean` výrazů, aby bylo možné zjistit výsledek. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Viz také:

- [THEN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)
- [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

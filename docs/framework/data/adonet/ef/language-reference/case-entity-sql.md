---
title: CASE (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 58b21d3be8e13a0a2204a4fd6d355f734207c509
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150464"
---
# <a name="case-entity-sql"></a>CASE (Entita SQL)
Vyhodnotí sadu `Boolean` výrazů k určení výsledku.  
  
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
  
## <a name="arguments"></a>Argumenty  
 `n`  
 Je zástupný symbol, který `Boolean_expression` `result_expression` označuje, že lze použít více klauzulí WHEN THEN.  
  
 Pak`result_expression`  
 Je výraz vrácena `Boolean_expression` při `true`vyhodnocuje na . `result expression`je libovolný platný výraz.  
  
 Jiného`else_result_expression`  
 Je výraz vrácena, pokud žádná `true`operace porovnání vyhodnotí . Pokud je tento argument vynechán a žádná `true`operace porovnání vyhodnocena na , funkce CASE vrátí hodnotu null. `else_result_expression`je libovolný platný výraz. Datové typy `else_result_expression` a `result_expression` všechny musí být stejné nebo musí být implicitní převod.  
  
 Kdy`Boolean_expression`  
 Je `Boolean` výraz vyhodnocen při použití prohledávaná case formát. `Boolean_expression`je libovolný `Boolean` platný výraz.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí nejvyšší typ priority ze sady typů `result_expression` v `else_result_expression`a volitelné .  
  
## <a name="remarks"></a>Poznámky  
 Výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] případu se podobá výrazu případu Transact-SQL. Výraz případu slouží k vytvoření řady podmíněných testů k určení, který výraz přinese odpovídající výsledek. Tato forma výrazu case se vztahuje na `Boolean` řadu jednoho nebo více výrazů k určení správného výsledného výrazu.  
  
 Funkce CASE `Boolean_expression` vyhodnotí pro každou klauzuli WHEN `result_expression` v `Boolean_expression` zadaném pořadí `true`a vrátí první, která je vyhodnocena . Zbývající výrazy nejsou vyhodnoceny. Pokud `Boolean_expression` žádné vyhodnotí `true`, databázový stroj vrátí `else_result_expression` pokud else klauzule je zadána nebo null hodnotu, pokud není zadána žádná klauzule ELSE.  
  
 Příkaz CASE nemůže vrátit vícesetovou sadu.  
  
## <a name="example"></a>Příklad  
 Následující dotaz ENTITY SQL používá výraz CASE `Boolean` k vyhodnocení sady výrazů za účelem určení výsledku. Dotaz je založen na adventureworks prodejní model. Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:  
  
1. Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Viz také

- [Pak](then-entity-sql.md)
- [Vyberte](select-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)

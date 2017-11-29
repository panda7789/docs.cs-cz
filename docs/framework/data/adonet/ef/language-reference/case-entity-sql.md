---
title: "PŘÍPAD (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f4e92d9a7c66d176357499bc831f07c56f36c90d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="case-entity-sql"></a>PŘÍPAD (entita SQL)
Vyhodnotí sadu `Boolean` výrazy k určení výsledku.  
  
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
  
 POTOM`result_expression`  
 Výraz dochází při `Boolean_expression` vyhodnocuje `true`. `result expression`je jakýkoli platný výraz.  
  
 ELSE`else_result_expression`  
 Je výraz vrácena, pokud žádná operace porovnání vyhodnocen `true`. Pokud je tento argument vynechán a žádná operace porovnání se vyhodnocuje `true`, případě vrátí hodnotu null. `else_result_expression`je jakýkoli platný výraz. Datové typy `else_result_expression` a jakýkoli `result_expression` musí být stejné nebo musí být implicitní převod.  
  
 KDY`Boolean_expression`  
 Je `Boolean` výrazu vyhodnoceného při použití vyhledávaná případu formátu. `Boolean_expression`je libovolný platný `Boolean` výraz.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí typ nejvyšší prioritu ze sady typy v `result_expression` a volitelné `else_result_expression`.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Případu výraz vypadá takto: [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] případ výraz. Výraz case použijete k provedení řady podmíněného testů, abyste zjistili, výrazu, který předá odpovídající výsledek. Tento formulář případu výrazu se vztahují na řadu jeden nebo více `Boolean` výrazy k určení správné výsledný výraz.  
  
 Funkce CASE vyhodnotí `Boolean_expression` pro každou klauzuli WHEN v pořadí zadané a vrátí `result_expression` prvního `Boolean_expression` , jehož výsledkem `true`. Zbývající výrazy nejsou vyhodnocena. Pokud žádné `Boolean_expression` vyhodnotí jako `true`, vrátí databázového stroje `else_result_expression` -li zadána klauzule ELSE, nebo hodnotu null, pokud není zadána žádná klauzule ELSE.  
  
 Příkaz CASE nemůže vrátit multimnožina.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá případu výraz k vyhodnocení sadu `Boolean` výrazy, aby bylo možné zjistit výsledek. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Viz také  
 [POTOM](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)  
 [VYBERTE](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

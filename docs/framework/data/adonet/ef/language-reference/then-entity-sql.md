---
title: PAK (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 99fd941c963ff87203d7b315beb606d40001224d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="then-entity-sql"></a>PAK (entita SQL)
Výsledek klauzuli WHEN vyhodnocení na `true`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `when_expression`  
 Platný logický výraz.  
  
 `then_expression`  
 Jakýkoli platný dotaz výraz, která vrátí kolekci.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `when_expression` vyhodnocen jako hodnota `true`, výsledkem je, odpovídající `then-expression`. Pokud není k dispozici z tím, kdy jsou splněny podmínky, `else-expression` vyhodnotí. Ale pokud neexistuje žádné `else-expression`, výsledkem je null.  
  
 Příklad, naleznete v části [případ](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá případu výraz k vyhodnocení sadu `Boolean` výrazy. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Viz také  
 [PŘÍPAD](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

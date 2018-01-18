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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d7a669cc87c14e4213d702b639a1956f04cb485d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
 [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

---
title: DEREF (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: bade65b36363aef1597ce4664e3e514141dee908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="deref-entity-sql"></a>DEREF (entita SQL)
Dereferences hodnota odkazu a vytváří výsledek této dereference.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Jakýkoli platný dotaz výraz, která vrátí kolekci.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota entity, který se odkazuje.  
  
## <a name="remarks"></a>Poznámky  
 Operátor DEREF dereferences hodnota odkazu a vytváří výsledek této dereference. Například pokud `r` odkaz typu ref\<T >, `Deref``(r)` je výraz typu `T` , vypočítá entita odkazuje `r`. Pokud hodnota odkaz má hodnotu null nebo je nepropojená (který je cílem odkazu neexistuje), výsledkem operátoru DEREF má hodnotu null.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu pomocí operátoru DEREF dereference produktu dereference výsledek a hodnota odkazu. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Následující dotaz předejte jako argument metodu ExecutePrimitiveTypeQuery:  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [Strukturované typy s možnou hodnotou Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)

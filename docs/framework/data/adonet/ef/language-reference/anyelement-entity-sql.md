---
title: ANYELEMENT (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6e74fbac9c2c57c653f55f76bf165d7eaebd9cee
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (entita SQL)
Extrahuje element z kolekce s více hodnotami.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný dotaz výraz, který vrátí kolekce k extrakci element z.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jednotlivých elementů v kolekci nebo libovolný element, pokud kolekce obsahuje více než jednu; Pokud je kolekce prázdná, vrátí `null`. Pokud `collection` je kolekce typu `Collection<T>`, pak `ANYELEMENT(collection)` je platný výraz, který poskytne instanci typu `T`.  
  
## <a name="remarks"></a>Poznámky  
 ANYELEMENT extrahuje libovolně zvolený element z kolekce s více hodnotami. Například v následujícím příkladu pokusí extrahovat singleton element ze sady `Customers`.  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor ANYELEMENT extrahovat element z kolekce s více hodnotami. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Strukturované typy s možnou hodnotou Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)

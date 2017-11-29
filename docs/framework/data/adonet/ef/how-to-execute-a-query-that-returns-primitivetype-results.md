---
title: "Postup: provedení dotazu, který vrátí výsledky PrimitiveType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 89c7ad8c6943aa335e81f1e1a475b01708b46eaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-a-query-that-returns-primitivetype-results"></a>Postup: provedení dotazu, který vrátí výsledky PrimitiveType
Toto téma ukazuje, jak k provedení příkazu pro koncepční model pomocí <xref:System.Data.EntityClient.EntityCommand>a jak načíst <xref:System.Data.Metadata.Edm.PrimitiveType> výsledky pomocí <xref:System.Data.EntityClient.EntityDataReader>.  
  
### <a name="to-run-the-code-in-this-example"></a>Spustí kód v tomto příkladu  
  
1.  Přidat [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) do projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Na stránce kódu pro aplikace, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Příklad  
 Tento příklad provede dotaz, který vrátí <xref:System.Data.Metadata.Edm.PrimitiveType> výsledek. Když je předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` funkce, funkce zobrazí průměrná cena seznam všech `Products`:  
  
 [!code-csharp[DP EntityServices Concepts 2#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#edm_avg)]  
  
 Pokud předáte parametrizovaného dotazu, takto <xref:System.Data.EntityClient.EntityParameter> objekty ke <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> vlastnost <xref:System.Data.EntityClient.EntityCommand> objektu.  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Zprostředkovatel EntityClient rozhraní Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)

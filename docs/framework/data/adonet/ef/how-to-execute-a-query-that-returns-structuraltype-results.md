---
title: "Postup: provedení dotazu, který vrátí výsledky StructuralType"
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
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b786fb54d8e588173cf79a5020f96c6a68ddecf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a>Postup: provedení dotazu, který vrátí výsledky StructuralType
Toto téma ukazuje, jak k provedení příkazu pro koncepční model pomocí <xref:System.Data.EntityClient.EntityCommand> objekt a jak načíst <xref:System.Data.Metadata.Edm.StructuralType> výsledky pomocí <xref:System.Data.EntityClient.EntityDataReader>. <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> a <xref:System.Data.Metadata.Edm.ComplexType> třídy jsou odvozeny od <xref:System.Data.Metadata.Edm.StructuralType> třídy.  
  
### <a name="to-run-the-code-in-this-example"></a>Spustí kód v tomto příkladu  
  
1.  Přidat [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) do projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Na stránce kódu pro aplikace, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Příklad  
 Tento příklad provede dotaz, který vrátí <xref:System.Data.Metadata.Edm.EntityType> výsledky. Když je předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` funkce, funkce zobrazí podrobnosti o `Products`:  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 Pokud předáte parametrizovaného dotazu, jako jsou následující, přidejte <xref:System.Data.EntityClient.EntityParameter> objekty ke <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> vlastnost <xref:System.Data.EntityClient.EntityCommand> objektu.  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Zprostředkovatel EntityClient rozhraní Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)

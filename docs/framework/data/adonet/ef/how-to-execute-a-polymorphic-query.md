---
title: "Postup: provedení polymorfní dotazu"
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
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4c5ee1a815ed638bc8e775abbb1c0541aa70d746
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-a-polymorphic-query"></a>Postup: provedení polymorfní dotazu
Toto téma ukazuje, jak provést polymorfní [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazování pomocí [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operátor.  
  
### <a name="to-run-the-code-in-this-example"></a>Spustí kód v tomto příkladu  
  
1.  Přidat [školní modelu](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac) do projektu a konfigurace projektu pro použití rozhraní Entity Framework. Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Na stránce kódu pro aplikace, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Upravit konceptuálního modelu má tabulka za hierrachy dědičnosti podle kroků v [návod: mapování dědičnosti - tabulky za hierarchie](http://msdn.microsoft.com/en-us/49b685cf-9db8-4d6d-b885-8837ed238f55).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor OFTYPE k získání a zobrazení kolekce pouze `OnsiteCourses` z kolekce `Courses`.  
  
 [!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
 [!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatel EntityClient rozhraní Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 [Jazyk SQL entity](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)

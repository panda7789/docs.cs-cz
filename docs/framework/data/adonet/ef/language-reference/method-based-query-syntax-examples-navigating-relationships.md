---
title: "Příklady syntaxe dotazů metoda: Navigace relací"
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
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 239e990c5a02962887e66f1bbc18358835006ac1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a>Příklady syntaxe dotazů metoda: Navigace relací
Navigační vlastnosti v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou vlastnosti zástupce používaná k nalezení entity na konci přidružení. Navigační vlastnosti umožnit uživateli přejít z jedné entity, nebo z jedné entity, která má entit v relaci prostřednictvím přidružení nastavit. Toto téma obsahuje příklady syntaxe dotazů metoda procházení vztahů pomocí navigačních vlastností v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.  
  
 Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.  
  
 V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Příklad  
 Následující příklad v používá syntaxi dotazu na základě metod <xref:System.Linq.Queryable.SelectMany%2A> metoda získat všechny objednávky kontaktů, jejichž příjmení je "Zhou". `Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce z `SalesOrderHeader` objekty pro každý kontakt.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu v syntaxi dotazu na základě metod <xref:System.Linq.Queryable.Select%2A> metodu za účelem získání všech kontakt ID a součet celkový splatnosti, obraťte se na každý jejichž příjmení je "Zhou". `Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce z `SalesOrderHeader` objekty pro každý kontakt. `Sum` Metoda používá `Contact.SalesOrderHeader` navigační vlastnost pro součet celkové kvůli všech objednávek pro každý kontakt.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad syntaxe dotazů metoda získá všechny objednávky kontaktů, jejichž příjmení je "Zhou". `Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce z `SalesOrderHeader` objekty pro každý kontakt. Jméno kontaktu a objednávky jsou vráceny v instanci anonymního typu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `SalesOrderHeader.Address` a `SalesOrderHeader.Contact` navigačních vlastností pro získání kolekce z `Address` a `Contact` objekty přidružené k každý pořadí. Příjmení kontaktu, adresu, prodeje pořadí číslo a celkový počet splatnosti pro každé pořadí města Seattle jsou vráceny v instanci anonymního typu.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Where` metody k vyhledání objednávky, které byly provedeny po 1. prosince 2003, a pak používá `order.SalesOrderDetail` navigační vlastnost pro získání podrobností o pro každé pořadí.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Viz také  
 [Navigační vlastnosti](http://msdn.microsoft.com/en-us/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
 [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

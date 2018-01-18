---
title: "Příklady syntaxe výrazu dotazu: Navigace relací"
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
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c029ce130e0bc8a6f959c6c27d863422794c22e5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a>Příklady syntaxe výrazu dotazu: Navigace relací
Navigační vlastnosti v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou vlastnosti zástupce používaná k nalezení entity na konci přidružení. Navigační vlastnosti umožnit uživateli přejít z jedné entity, nebo z jedné entity, která má entit v relaci prostřednictvím přidružení nastavit. Toto téma obsahuje příklady syntaxe výrazu dotazu procházení vztahů pomocí navigačních vlastností v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.  
  
 Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.  
  
 V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Queryable.Select%2A> metodu za účelem získání všech kontakt ID a součet celkový splatnosti, obraťte se na každý jejichž příjmení je "Zhou". `Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce z `SalesOrderHeader` objekty pro každý kontakt. `Sum` Metoda používá `Contact.SalesOrderHeader` navigační vlastnost pro součet celkové kvůli všech objednávek pro každý kontakt.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a>Příklad  
 Následující příklad načte všechny objednávky kontaktů, jejichž příjmení je "Zhou". `Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce z `SalesOrderHeader` objekty pro každý kontakt. Jméno kontaktu a objednávky jsou vráceny v instanci anonymního typu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `SalesOrderHeader.Address` a `SalesOrderHeader.Contact` získat navigační vlastnosti kolekce `Address` a `Contact` objekty přidružené k každý pořadí. Příjmení kontaktu, adresu, prodeje pořadí číslo a celkový počet splatnosti pro každé pořadí města Seattle jsou vráceny v instanci anonymního typu.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá `Where` metody k vyhledání objednávky, které byly provedeny po 1. prosince 2003, a pak používá `order.SalesOrderDetail` navigační vlastnost pro získání podrobností o pro každé pořadí.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Viz také  
 [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

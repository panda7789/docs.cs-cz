---
title: 'Příklady syntaxe dotazů založených na volání metody: Navigace v relacích'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: c749a7bb1575ee52418f0953ff8216bf4221b674
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250152"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a>Příklady syntaxe dotazů založených na volání metody: Navigace v relacích
Navigační vlastnosti v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nástroji jsou vlastnosti zkratky používané k vyhledání entit na koncích přidružení. Navigační vlastnosti umožňují uživateli přejít z jedné entity na jinou nebo z jedné entity na související entity prostřednictvím sady přidružení. V tomto tématu jsou uvedeny příklady syntaxe dotazů založených na metodách, jak procházet vztahy prostřednictvím vlastností navigace v LINQ to Entitiesch dotazech.  
  
 Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.  
  
 Příklady v tomto tématu používají následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Příklad  
 Následující příklad v syntaxi dotazu založeného na metodách používá <xref:System.Linq.Queryable.SelectMany%2A> metodu k získání všech objednávek kontaktů, jejichž příjmení je "Zhou". Navigační vlastnost se používá k získání `SalesOrderHeader` kolekce objektů pro každý kontakt. `Contact.SalesOrderHeader`  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad v syntaxi dotazu založeného na metodách používá <xref:System.Linq.Queryable.Select%2A> metodu k získání všech ID kontaktů a součtu celkového počtu všech kontaktů, jejichž příjmení je "Zhou". Navigační vlastnost se používá k získání `SalesOrderHeader` kolekce objektů pro každý kontakt. `Contact.SalesOrderHeader` `Sum` Metoda používávlastnostnavigacekcelkovémusoučtuzdůvodu`Contact.SalesOrderHeader` všech objednávek jednotlivých kontaktů.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad v syntaxi dotazu založeného na metodách získá všechny objednávky kontaktů, jejichž příjmení je "Zhou". Navigační vlastnost se používá k získání `SalesOrderHeader` kolekce objektů pro každý kontakt. `Contact.SalesOrderHeader` Jméno kontaktu a objednávky jsou vráceny anonymním typem.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `SalesOrderHeader.Address` navigační vlastnosti a `SalesOrderHeader.Contact` `Address` k získání kolekce objektů a `Contact` přidružených k jednotlivým objednávkám. Jméno kontaktu, Adresa ulice, číslo prodejní objednávky a celková hodnota v souvislosti s každým pořadím města v Seattlu jsou vráceny anonymním typem.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Where` metodu k vyhledání objednávek, které byly provedeny po 1. prosinci 2003, a poté `order.SalesOrderDetail` používá navigační vlastnost k získání podrobností pro každou objednávku.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Viz také:

- [Relace, navigační vlastnosti a cizí klíče](/ef/ef6/fundamentals/relationships)
- [Dotazy v technologii LINQ to Entities](queries-in-linq-to-entities.md)

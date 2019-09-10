---
title: 'Příklady syntaxe výrazů dotazů: Navigace v relacích'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: a99d7d31ce23629bf7a0f390244c1fe67b4554e3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854405"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a>Příklady syntaxe výrazů dotazů: Navigace v relacích
Navigační vlastnosti v Entity Framework jsou zástupci vlastností, které slouží k vyhledání entit na koncích přidružení. Navigační vlastnosti umožňují uživateli přejít z jedné entity na jinou nebo z jedné entity na související entity prostřednictvím sady přidružení. V tomto tématu najdete příklady v syntaxi výrazů dotazů, jak procházet vztahy prostřednictvím vlastností navigace v LINQ to Entitiesch dotazech.  
  
 Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.  
  
 Příklady v tomto tématu používají následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Queryable.Select%2A> metodu k získání všech ID kontaktů a součtu celkového počtu všech kontaktů, jejichž příjmení je "Zhou". Navigační vlastnost se používá k získání `SalesOrderHeader` kolekce objektů pro každý kontakt. `Contact.SalesOrderHeader` `Sum` Metoda používávlastnostnavigacekcelkovémusoučtuzdůvodu`Contact.SalesOrderHeader` všech objednávek jednotlivých kontaktů.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a>Příklad  
 Následující příklad získá všechny objednávky kontaktů, jejichž příjmení je "Zhou". Navigační vlastnost se používá k získání `SalesOrderHeader` kolekce objektů pro každý kontakt. `Contact.SalesOrderHeader` Jméno kontaktu a objednávky jsou vráceny anonymním typem.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a>Příklad  
 `SalesOrderHeader.Address` Následující příklad používá `Contact` navigační `SalesOrderHeader.Contact` vlastnosti a k získání kolekce objektů apřidruženýchkjednotlivýmobjednávkám.`Address` Jméno kontaktu, Adresa ulice, číslo prodejní objednávky a celková hodnota v souvislosti s každým pořadím města v Seattlu jsou vráceny anonymním typem.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá `Where` metodu k vyhledání objednávek, které byly provedeny po 1. prosinci 2003, a poté `order.SalesOrderDetail` používá navigační vlastnost k získání podrobností pro každou objednávku.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazy v technologii LINQ to Entities](queries-in-linq-to-entities.md)

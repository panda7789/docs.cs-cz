---
title: 'Příklady syntaxe výrazů dotazů: Navigace v relacích'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: 2133ae7902cc4746e00be75e7a801296073041e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614281"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a>Příklady syntaxe výrazů dotazů: Navigace v relacích
Vlastnosti navigace v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou místní vlastnosti používaná k nalezení entity na konci přidružení. Vlastnosti navigace umožní uživateli se mezi jednotlivými entitami přecházet do druhé nebo z entit souvisejících entit prostřednictvím přidružení nastavení. Toto téma obsahuje příklady v syntaxe výrazu dotazu procházení vztahů pomocí navigačních vlastností v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.  
  
 Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.  
  
 V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Linq.Queryable.Select%2A> metodu k získání všech ID kontaktu a součet celková částka každý od jejichž příjmení je "Zhou". `Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce `SalesOrderHeader` objekty pro každého kontaktu. `Sum` Metoda používá `Contact.SalesOrderHeader` navigační vlastnost pro celkový součet vypršení platnosti všech objednávek pro každého kontaktu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a>Příklad  
 Následující příklad získá všechny objednávky kontaktů, jejichž příjmení je "Zhou". `Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce `SalesOrderHeader` objekty pro každého kontaktu. Jméno kontaktu a objednávky jsou vráceny v anonymním typu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `SalesOrderHeader.Address` a `SalesOrderHeader.Contact` získat navigační vlastnosti kolekce `Address` a `Contact` objekty přidružené k jednotlivé objednávky. Příjmení kontaktu, adresa, prodejní objednávky, čísla a celkový počet termínem pro jednotlivé objednávky na město Seattle jsou vráceny v anonymním typu.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu `Where` metody k vyhledání objednávky, které byly provedeny po 1. prosince 2003 a pak použije `order.SalesOrderDetail` vlastnosti navigace použít k získání podrobností každé objednávky.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

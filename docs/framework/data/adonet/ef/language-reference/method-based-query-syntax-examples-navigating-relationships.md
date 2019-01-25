---
title: 'Příklady syntaxe dotazů založených na volání metody: Navigace v relacích'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: 450fa284254c9a78a287c922424f0deaafd7534f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692243"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a>Příklady syntaxe dotazů založených na volání metody: Navigace v relacích
Vlastnosti navigace v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou místní vlastnosti používaná k nalezení entity na konci přidružení. Vlastnosti navigace umožní uživateli se mezi jednotlivými entitami přecházet do druhé nebo z entit souvisejících entit prostřednictvím přidružení nastavení. Toto téma obsahuje příklady syntaxe dotazů založených na volání metody procházení vztahů pomocí navigačních vlastností v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.  
  
 Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.  
  
 V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Příklad  
 Následující příklad použití syntaxe dotazů založených na volání metody <xref:System.Linq.Queryable.SelectMany%2A> metodu k získání všech objednávek kontaktů, jejichž příjmení je "Zhou". `Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce `SalesOrderHeader` objekty pro každého kontaktu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu v syntaxi dotazů založených na volání metody <xref:System.Linq.Queryable.Select%2A> metodu k získání všech ID kontaktu a součet celková částka každý od jejichž příjmení je "Zhou". `Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce `SalesOrderHeader` objekty pro každého kontaktu. `Sum` Metoda používá `Contact.SalesOrderHeader` navigační vlastnost pro celkový součet vypršení platnosti všech objednávek pro každého kontaktu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad v syntaxi dotazů založených na volání metody získá všechny objednávky kontaktů, jejichž příjmení je "Zhou". `Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce `SalesOrderHeader` objekty pro každého kontaktu. Jméno kontaktu a objednávky jsou vráceny v anonymním typu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `SalesOrderHeader.Address` a `SalesOrderHeader.Contact` navigačních vlastností pro získání kolekce `Address` a `Contact` objekty přidružené k jednotlivé objednávky. Příjmení kontaktu, adresa, prodejní objednávky, čísla a celkový počet termínem pro jednotlivé objednávky na město Seattle jsou vráceny v anonymním typu.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Where` metody k vyhledání objednávky, které byly provedeny po 1. prosince 2003 a pak použije `order.SalesOrderDetail` vlastnosti navigace použít k získání podrobností každé objednávky.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Viz také:
- [Navigační vlastnosti](https://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)
- [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

---
title: 'Příklady syntaxe dotazů založených na volání metody: Filtrování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e40e314c-eb30-4f44-a054-41e511e35832
ms.openlocfilehash: 0795784f4090fca02c89cdfb396d217620b1ba68
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948240"
---
# <a name="method-based-query-syntax-examples-filtering"></a>Příklady syntaxe dotazů založených na volání metody: Filtrování
Příklady v tomto tématu ukazují, jak používat `Where` metody a `Where…Contains` k dotazování [modelu prodeje společnosti AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe dotazu založeného na metodách. Poznámka, kde...`Contains` nelze použít jako součást [zkompilovaného dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).  
  
 Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.  
  
 Příklady v tomto tématu používají následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a>Where  
  
### <a name="example"></a>Příklad  
 Následující příklad vrátí všechny online objednávky.  
  
 [!code-csharp[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1_mq)]
 [!code-vb[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vrátí objednávky, kde je množství objednávky větší než 2 a menší než 6.  
  
 [!code-csharp[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2_mq)]
 [!code-vb[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vrátí všechny červené barevné produkty.  
  
 [!code-csharp[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3_mq)]
 [!code-vb[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá `Where` metodu k vyhledání objednávek, které byly provedeny po 1. prosinci 2003 a poté `order.SalesOrderDetail` pomocí vlastnosti navigace Získá podrobnosti pro každou objednávku.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty_mq)]
 [!code-vb[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty_mq)]  
  
## <a name="wherecontains"></a>Kde... Zobrazí  
  
### <a name="example"></a>Příklad  
 Následující příklad používá pole jako součást `Where…Contains` klauzule pro vyhledání všech produktů, které `ProductModelID` mají, které odpovídají hodnotě v poli.  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#3)]
 [!code-vb[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#3)]  
  
> [!NOTE]
> Jako `Where…Contains` součást predikátu v klauzuli můžete <xref:System.Array>použít, <xref:System.Collections.Generic.List%601>nebo, nebo kolekci libovolného typu, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Můžete také deklarovat a inicializovat kolekci v rámci LINQ to Entitiesho dotazu. Další informace najdete v dalším příkladu.  
  
### <a name="example"></a>Příklad  
 Následující příklad deklaruje a inicializuje pole v `Where…Contains` klauzuli pro vyhledání všech produktů, které `ProductModelID` mají nebo `Size` , které odpovídají hodnotě v polích.  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#4)]
 [!code-vb[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

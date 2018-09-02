---
title: 'Příklady syntaxe dotazů založených na volání metody: Dělení (LINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
ms.openlocfilehash: 6664336b1873008ae193120ce800f9d266f58857
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402310"
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a>Příklady syntaxe dotazů založených na volání metody: Dělení (LINQ
Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, a <xref:System.Linq.Enumerable.TakeWhile%2A> metody pro dotazování <xref:System.Data.DataSet> pomocí syntaxe výrazu dotazu.  
  
 `FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.  
  
 V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Další informace najdete v tématu [postupy: vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="skip"></a>Skip  
  
### <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech, ale prvních pět kontakty `Contact` tabulky.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech, ale prvních dvou adres v Praze.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a>SkipWhile –  
  
### <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> a <xref:System.Linq.Enumerable.SkipWhile%2A> metody vrátí produkty `Product` tabulku s větší než 300.00 ceníku.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a>Take  
  
### <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Linq.Enumerable.Take%2A> metodu k získání pouze prvních pět kontakty z `Contact` tabulky.  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Linq.Enumerable.Take%2A> metodu k získání prvními třemi adresami v Seattlu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a>TakeWhile –  
  
### <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> a <xref:System.Linq.Enumerable.TakeWhile%2A> vrátit produkty `Product` tabulku s cenami seznamu menší než 300.00.  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a>Viz také  
 [Načtení dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Přehled standardních operátorů dotazu](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)

---
title: 'Příklady syntaxe dotazů založených na volání metody: Dělení (LINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
ms.openlocfilehash: 7e01bd9702ae267f80ecf24de0c0cc90d638a84c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783597"
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a>Příklady syntaxe dotazů založených na volání metody: Dělení (LINQ
Příklady v tomto tématu <xref:System.Linq.Enumerable.Skip%2A>ukazují, jak použít <xref:System.Linq.Enumerable.TakeWhile%2A> metody, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>a pro dotazování <xref:System.Data.DataSet> pomocí syntaxe výrazu dotazu.  
  
 Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`  
  
 V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.  
  
 Příklady v tomto tématu používají následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="skip"></a>Skip  
  
### <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech, ale prvních pět kontaktů `Contact` tabulky.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech kromě prvních dvou adres v Praze.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a>SkipWhile –  
  
### <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Linq.Enumerable.OrderBy%2A> se <xref:System.Linq.Enumerable.SkipWhile%2A> používají metody a `Product` k vrácení produktů z tabulky se ceníkovou cenou větší než 300,00.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a>Take  
  
### <a name="example"></a>Příklad  
 V tomto příkladu se <xref:System.Linq.Enumerable.Take%2A> pomocí metody načte jenom prvních pět kontaktů `Contact` z tabulky.  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Enumerable.Take%2A> metodu k získání prvních tří adres v Praze.  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a>TakeWhile –  
  
### <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Linq.Enumerable.OrderBy%2A> se <xref:System.Linq.Enumerable.TakeWhile%2A> pomocí a vrátí produkty z `Product` tabulky se ceníkovou cenou menší než 300,00.  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a>Viz také:

- [Načtení dat do datové sady](loading-data-into-a-dataset.md)
- [Příklady LINQ to DataSet](linq-to-dataset-examples.md)
- [Přehled standardních operátorů dotazůC#()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Přehled standardních operátorů dotazů (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

---
title: 'Příklady syntaxe dotazů metoda: Řazení (LINQ na DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: 9a5a518740191eac067550d35e936a6f4ff09710
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765357"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a>Příklady syntaxe dotazů metoda: Řazení (LINQ na DataSet)
V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, a <xref:System.Linq.Enumerable.ThenBy%2A> metody pro dotazování <xref:System.Data.DataSet> a řazení výsledků pomocí syntaxe dotazu metoda.  
  
 `FillDataSet` Metodu použitou v těchto příkladech je uveden v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 V příkladech v tomto tématu použijte kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.  
  
 V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Další informace najdete v tématu [postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="orderby"></a>Řadit podle  
  
### <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> metoda s vlastní porovnávací funkci udělat velká a malá písmena řazení příjmení.  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a>Reverse  
  
### <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Enumerable.Reverse%2A> metodu pro vytvoření seznam řadí kde `OrderDate` je starší než 20. února 2002.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a>ThenBy  
  
### <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> a <xref:System.Linq.Enumerable.ThenBy%2A> metody s vlastní porovnávací funkci první seřadit seznam ceny a pak proveďte velká a malá písmena sestupné řazení názvy produktů.  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a>Viz také  
 [Načtení dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Přehled standardních operátorů dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)

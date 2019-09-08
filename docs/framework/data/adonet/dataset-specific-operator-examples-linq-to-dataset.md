---
title: Příklady operátorů specifických pro datovou sadu (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 6a9dc82e0bb065b455c0208daaf2d28a74cd7e34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784198"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a>Příklady operátorů specifických pro datovou sadu (LINQ to DataSet)
Příklady v tomto tématu ukazují, jak používat <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metodu <xref:System.Data.DataRowComparer> a třídu.  
  
 Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`  
  
 V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.  
  
 Příklady v tomto tématu používají následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="copytodatatable"></a>CopyToDataTable  
  
### <a name="example"></a>Příklad  
 Tento příklad načte <xref:System.Data.DataTable> s výsledky dotazu <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> pomocí metody.  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a>DataRowComparer  
  
### <a name="example"></a>Příklad  
 Tento příklad porovnává dva různé datové řádky pomocí <xref:System.Data.DataRowComparer>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a>Viz také:

- [Načtení dat do datové sady](loading-data-into-a-dataset.md)
- [Příklady LINQ to DataSet](linq-to-dataset-examples.md)

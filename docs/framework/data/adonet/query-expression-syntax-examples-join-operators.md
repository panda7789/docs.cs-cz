---
title: 'Příklady syntaxe výrazů dotazů: Připojte se k operátory (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f4d86667-3392-470d-a076-5ca6cbb660f6
ms.openlocfilehash: 7bd8576358cf8e8981bcb4728f47d56d11fcd8a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683437"
---
# <a name="query-expression-syntax-examples-join-operators-linq-to-dataset"></a>Příklady syntaxe výrazů dotazů: Připojte se k operátory (LINQ to DataSet)
Připojení je důležité operace v dotazech, které se zaměřují zdroje dat, které jste žádné relace navigaci k sobě navzájem, jako je například tabulek relační databáze. Přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat. je spojení dvou datových zdrojů. Další informace najdete v tématu [přehled standardních operátorů dotazu](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.GroupJoin%2A> a <xref:System.Linq.Enumerable.Join%2A> metody pro dotazování <xref:System.Data.DataSet> pomocí syntaxe výrazu dotazu.  
  
 `FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.  
  
 V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Další informace najdete v tématu [jak: Vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="groupjoin"></a>GroupJoin  
  
### <a name="example"></a>Příklad  
 V tomto příkladu se provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes `SalesOrderHeader` a `SalesOrderDetail` tabulky a vyhledá počet objednávek pro zákazníka. Spojení skupiny je ekvivalentem levé vnější spojení, která vrátí všechny prvky objektu prvního zdroje dat (levý) i v případě, že žádné korelační prvky jsou ve zdroji dat jiné.  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a>Příklad  
 V tomto příkladu se provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes `Contact` a `SalesOrderHeader` tabulky. Spojení skupiny je ekvivalentem levé vnější spojení, která vrátí všechny prvky objektu prvního zdroje dat (levý) i v případě, že žádné korelační prvky jsou ve zdroji dat jiné.  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a>Join  
  
### <a name="example"></a>Příklad  
 V tomto příkladu provádí spojení `SalesOrderHeader` a `SalesOrderDetail` tabulky k získání online objednávky z srpnu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Viz také:
- [Načtení dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [Přehled standardních operátorů dotazu](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)

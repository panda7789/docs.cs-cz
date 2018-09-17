---
title: Dotazy na typové datové sady
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: d956fd5f07c108146d20623bcf811266380c132c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45963741"
---
# <a name="query-typed-datasets"></a>Dotazování typové datové sady

Pokud schéma <xref:System.Data.DataSet> je znám v době návrhu aplikací, doporučujeme použít zadaný <xref:System.Data.DataSet> při použití technologie LINQ to DataSet. Zadaný <xref:System.Data.DataSet> je třída, která je odvozena z <xref:System.Data.DataSet>. V důsledku toho dědí všechny metody, události a vlastnosti <xref:System.Data.DataSet>. Kromě toho typovaného <xref:System.Data.DataSet> poskytuje silného typu metody, události a vlastnosti. To znamená, že dostanete tabulky a sloupce podle názvu, namísto použití metody založené na kolekci. Díky tomu dotazy, jednodušší a lépe čitelný. Další informace najdete v tématu [typované datové sady](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).

Technologie LINQ to DataSet také podporuje dotazování typovaného <xref:System.Data.DataSet>. S typovaného <xref:System.Data.DataSet>, není nutné museli používat obecná <xref:System.Data.DataRowExtensions.Field%2A> metoda nebo <xref:System.Data.DataRowExtensions.SetField%2A> metody pro přístup k datům sloupce. Názvy vlastností jsou k dispozici v době kompilace, protože je součástí informací o typu <xref:System.Data.DataSet>. Technologie LINQ to DataSet poskytuje přístup k hodnotám sloupce jako správný typ, tak, aby při kompilaci kódu místo v době běhu jsou zachyceny chyby typu neshoda.

Před zahájením dotazování typovaného <xref:System.Data.DataSet>, musíte vygenerovat třídu pomocí **Návrhář DataSet** v sadě Visual Studio. Další informace najdete v tématu [vytvoření a konfigurace datové sady](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).

## <a name="example"></a>Příklad

Následující příklad ukazuje dotaz nad typovaného <xref:System.Data.DataSet>:

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a>Viz také:

- [Dotazy na datové sady](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Dotazy na křížovou tabulku](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [Dotazy na jednu tabulku](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)

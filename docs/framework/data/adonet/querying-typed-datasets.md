---
title: Dotazy na typové datové sady
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 55714c4dae73cd17a849cc35681797dfa4266e3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782964"
---
# <a name="query-typed-datasets"></a>Datové sady s typovým dotazem

Pokud je schéma v <xref:System.Data.DataSet> době návrhu aplikace známo, doporučujeme při použití LINQ to DataSet zadat <xref:System.Data.DataSet> typ. Typ je třída, která je odvozena z typu <xref:System.Data.DataSet>. <xref:System.Data.DataSet> V takovém případě dědí všechny metody, události a vlastnosti <xref:System.Data.DataSet>. Kromě toho zadaný <xref:System.Data.DataSet> typ poskytuje metody, události a vlastnosti silného typu. To znamená, že můžete získat přístup k tabulkám a sloupcům podle názvu namísto použití metod založených na kolekcích. Díky tomu jsou dotazy jednodušší a čitelnější. Další informace najdete v tématu [typové datové sady](./dataset-datatable-dataview/typed-datasets.md).

LINQ to DataSet také podporuje dotazování na typovaném <xref:System.Data.DataSet>typu. Se zadaným typem <xref:System.Data.DataSet>není nutné pro přístup k datům sloupce používat obecnou <xref:System.Data.DataRowExtensions.Field%2A> metodu <xref:System.Data.DataRowExtensions.SetField%2A> nebo metodu. Názvy vlastností jsou k dispozici v době kompilace, protože informace o typu jsou <xref:System.Data.DataSet>obsaženy v. LINQ to DataSet poskytuje přístup k hodnotám sloupců jako správný typ, takže pokud je kód kompilován při kompilaci namísto za běhu, jsou zachyceny chyby typu Neshoda typů.

Předtím <xref:System.Data.DataSet>, než můžete začít dotazovat se na typ, musíte vygenerovat třídu pomocí **Návrháře DataSet v sadě** Visual Studio. Další informace najdete v tématu [Vytvoření a konfigurace datových sad](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).

## <a name="example"></a>Příklad

Následující příklad ukazuje dotaz na základě zadaného <xref:System.Data.DataSet>typu:

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

- [Dotazy na datové sady](querying-datasets-linq-to-dataset.md)
- [Dotazy na křížovou tabulku](cross-table-queries-linq-to-dataset.md)
- [Dotazy na jednu tabulku](single-table-queries-linq-to-dataset.md)

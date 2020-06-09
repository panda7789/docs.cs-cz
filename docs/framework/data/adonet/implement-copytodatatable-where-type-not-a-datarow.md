---
title: 'Postupy: Implementace CopyToDataTable<T>, kde obecný typ není DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: a1427747d03f01e52f1ee7ad1fc11d47d310edbe
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590602"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>Postupy: Implementace CopyToDataTable\<T>, kde obecný typ není DataRow
<xref:System.Data.DataTable>Objekt se často používá pro datovou vazbu. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metoda přijímá výsledky dotazu a kopíruje data do <xref:System.Data.DataTable> , které lze následně použít pro datovou vazbu. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metody však pracují pouze na <xref:System.Collections.Generic.IEnumerable%601> zdroji, kde je obecný parametr `T` typu <xref:System.Data.DataRow> . I když je to užitečné, neumožňuje vytvářet tabulky ze sekvencí skalárních typů, od dotazů, které jsou anonymní typy projektu, nebo z dotazů, které provádějí spojení s tabulkou.  
  
 Toto téma popisuje, jak implementovat dvě vlastní `CopyToDataTable<T>` metody rozšíření, které přijímají obecný parametr `T` jiného typu než <xref:System.Data.DataRow> . Logika pro vytvoření <xref:System.Data.DataTable> ze <xref:System.Collections.Generic.IEnumerable%601> zdroje je obsažena ve `ObjectShredder<T>` třídě, která je poté zabalena do dvou přetížených `CopyToDataTable<T>` rozšiřujících metod. `Shred`Metoda `ObjectShredder<T>` třídy vrátí vyplněné <xref:System.Data.DataTable> a akceptuje tři vstupní parametry: <xref:System.Collections.Generic.IEnumerable%601> zdroj, a <xref:System.Data.DataTable> a <xref:System.Data.LoadOption> výčet. Počáteční schéma vráceného <xref:System.Data.DataTable> je založeno na schématu typu `T` . Pokud je jako vstup zadána stávající tabulka, schéma musí být konzistentní se schématem typu `T` . Každá veřejná vlastnost a pole typu `T` je převedena na typ <xref:System.Data.DataColumn> ve vrácené tabulce. Pokud zdrojová sekvence obsahuje typ odvozený z `T` , je schéma vrácených tabulek rozšířeno pro všechny další veřejné vlastnosti nebo pole.  
  
 Příklady použití vlastních `CopyToDataTable<T>` metod naleznete v tématu [vytvoření objektu DataTable z dotazu](creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Implementace vlastních \<T> metod CopyToDataTable ve vaší aplikaci  
  
1. Implementujte `ObjectShredder<T>` třídu pro vytvoření <xref:System.Data.DataTable> ze <xref:System.Collections.Generic.IEnumerable%601> zdroje:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    Předchozí příklad předpokládá, že vlastnosti a pole nemůžou `DataColumn` mít typy hodnot s možnou hodnotou null. Chcete-li zpracovat vlastnosti a pole s typy hodnot s možnou hodnotou null, použijte následující kód:

    ```csharp
    // Nullable-aware code for properties.
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);

    // Nullable-aware code for fields.
    DataColumn dc = table.Columns.Contains(f.Name) ? table.Columns[f.Name] : table.Columns.Add(f.Name, Nullable.GetUnderlyingType(f.FieldType) ?? f.FieldType);
    ```

2. Implementujte vlastní `CopyToDataTable<T>` metody rozšíření ve třídě:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. Přidejte `ObjectShredder<T>` `CopyToDataTable<T>` do své aplikace metody třídy a rozšíření.  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a>Viz také

- [Vytvoření datové tabulky z dotazu](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [Průvodce programováním](programming-guide-linq-to-dataset.md)

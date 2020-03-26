---
title: 'Postupy: Implementace CopyToDataTable<T>, kde obecný typ není DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 6c14e87c5caede4fea52867d9f184f3f64a5ed3b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249640"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>Postup: Implementujte CopyToDataTable\<T> kde obecný typ T není datarow
Objekt <xref:System.Data.DataTable> se často používá pro datové vazby. Metoda <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> přebírá výsledky dotazu a zkopíruje <xref:System.Data.DataTable>data do , který pak lze použít pro datové vazby. Metody <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> však pracují pouze <xref:System.Collections.Generic.IEnumerable%601> na zdroji, `T` kde je <xref:System.Data.DataRow>obecný parametr typu . I když je to užitečné, neumožňuje tabulky, které mají být vytvořeny z posloupnosti skalární typy, z dotazů, které projekt anonymní typy nebo z dotazů, které provádějí spojení tabulky.  
  
 Toto téma popisuje, jak `CopyToDataTable<T>` implementovat dvě vlastní `T` metody rozšíření, <xref:System.Data.DataRow>které přijímají obecný parametr typu než . Logika pro <xref:System.Data.DataTable> vytvoření <xref:System.Collections.Generic.IEnumerable%601> ze zdroje je `ObjectShredder<T>` obsažena ve třídě, která je `CopyToDataTable<T>` pak zabalena do dvou přetížených rozšiřujících metod. Metoda `Shred` `ObjectShredder<T>` třídy vrátí vyplněný <xref:System.Data.DataTable> a přijímá tři vstupní <xref:System.Collections.Generic.IEnumerable%601> parametry: <xref:System.Data.DataTable>zdroj, a a <xref:System.Data.LoadOption> výčet. Počáteční schéma vrácené <xref:System.Data.DataTable> je založeno na schématu typu `T`. Pokud existující tabulka je k dispozici jako vstup, schéma musí být konzistentní se `T`schématem typu . Každá veřejná vlastnost a `T` pole typu <xref:System.Data.DataColumn> je převedena na a ve vrácené tabulce. Pokud zdrojová sekvence obsahuje typ `T`odvozený od , je schéma vrácené tabulky rozbaleno pro všechny další veřejné vlastnosti nebo pole.  
  
 Příklady použití vlastních `CopyToDataTable<T>` metod naleznete v [tématu Vytvoření datatable z dotazu](creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Implementace vlastních metod CopyToDataTable\<T> ve vaší aplikaci  
  
1. Implementujte `ObjectShredder<T>` třídu <xref:System.Data.DataTable> k <xref:System.Collections.Generic.IEnumerable%601> vytvoření ze zdroje:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    Předchozí příklad předpokládá, že vlastnosti `DataColumn` nejsou null typy hodnot. Chcete-li zpracovat vlastnosti s typy hodnot s možnou hodnotou s hodnotou null, použijte následující kód:

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. Implementujte `CopyToDataTable<T>` vlastní metody rozšíření ve třídě:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. Přidejte `ObjectShredder<T>` třídy a `CopyToDataTable<T>` rozšíření metody do aplikace.  
  
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
- [Programovací příručka](programming-guide-linq-to-dataset.md)

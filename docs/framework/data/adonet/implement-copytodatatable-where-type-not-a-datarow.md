---
title: 'Postupy: Implementace CopyToDataTable<T>, kde obecný typ není DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 27df5e88b93914d317f0f59c704382bde67534d2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794998"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>Postupy: Implementujte\<CopyToDataTable T >, kde obecný typ T není DataRow.
<xref:System.Data.DataTable> Objekt se často používá pro datovou vazbu. Metoda přijímá výsledky dotazu a kopíruje data <xref:System.Data.DataTable>do, které lze následně použít pro datovou vazbu. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metody však pracují pouze <xref:System.Collections.Generic.IEnumerable%601> na zdroji, kde je obecný parametr `T` typu <xref:System.Data.DataRow>. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> I když je to užitečné, neumožňuje vytvářet tabulky ze sekvencí skalárních typů, od dotazů, které jsou anonymní typy projektu, nebo z dotazů, které provádějí spojení s tabulkou.  
  
 Toto téma popisuje, jak implementovat dvě vlastní `CopyToDataTable<T>` metody rozšíření, které přijímají obecný `T` parametr jiného typu než <xref:System.Data.DataRow>. Logika <xref:System.Data.DataTable> pro vytvoření <xref:System.Collections.Generic.IEnumerable%601> ze `CopyToDataTable<T>` zdroje je obsažena ve třídě,kterájepotézabalenadodvoupřetíženýchrozšiřujícíchmetod.`ObjectShredder<T>` <xref:System.Data.DataTable> <xref:System.Data.LoadOption> <xref:System.Data.DataTable>Metoda třídy vrátí vyplněné a akceptuje tři vstupní parametry: <xref:System.Collections.Generic.IEnumerable%601> zdroj, a a výčet. `ObjectShredder<T>` `Shred` Počáteční schéma vráceného <xref:System.Data.DataTable> je založeno na schématu typu `T`. Pokud je jako vstup zadána stávající tabulka, schéma musí být konzistentní se schématem typu `T`. Každá veřejná vlastnost a pole typu je převedena `T` <xref:System.Data.DataColumn> na typ ve vrácené tabulce. Pokud zdrojová sekvence obsahuje typ odvozený z `T`, je schéma vrácených tabulek rozšířeno pro všechny další veřejné vlastnosti nebo pole.  
  
 Příklady použití vlastních `CopyToDataTable<T>` metod naleznete v tématu [vytvoření objektu DataTable z dotazu](creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Implementace vlastních metod CopyToDataTable\<T > v aplikaci  
  
1. Implementujte <xref:System.Data.DataTable> <xref:System.Collections.Generic.IEnumerable%601> třídu pro vytvoření ze zdroje: `ObjectShredder<T>`  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    Předchozí příklad předpokládá, že vlastnosti `DataColumn` typu neumožňují hodnotu null. Chcete-li zpracovat vlastnosti s typy s možnou hodnotou null, použijte následující kód:

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. Implementujte vlastní `CopyToDataTable<T>` metody rozšíření ve třídě:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. Přidejte do své aplikace `CopyToDataTable<T>` metody třídyarozšíření.`ObjectShredder<T>`  
  
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
  
## <a name="see-also"></a>Viz také:

- [Vytvoření datové tabulky z dotazu](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [Průvodce programováním](programming-guide-linq-to-dataset.md)

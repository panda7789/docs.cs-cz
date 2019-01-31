---
title: 'Postupy: Implementace CopyToDataTable<T> kde obecný typ není DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 1f79bd421d4c504556074468f8ab7e032d3eca43
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288155"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>Postupy: Implementace CopyToDataTable\<T > kde obecný typ není DataRow
<xref:System.Data.DataTable> Objektu se často používá k vytváření datových vazeb. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda přijímá výsledky dotazu a zkopíruje data do <xref:System.Data.DataTable>, který potom slouží pro vytváření datových vazeb. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metody, ale pracovat pouze s <xref:System.Collections.Generic.IEnumerable%601> zdroje kde obecný parametr `T` je typu <xref:System.Data.DataRow>. I když to je užitečné, neumožňuje tabulky, který se má vytvořit ze sekvence Skalární typy, dotazy, které anonymní typy projektů nebo dotazy, které provádějí spoje tabulky platná.  
  
 Toto téma popisuje, jak implementovat dvě vlastní `CopyToDataTable<T>` rozšiřující metody, které přijímají obecný parametr `T` typu jiného než <xref:System.Data.DataRow>. Logiku pro vytvoření <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> je součástí zdroje `ObjectShredder<T>` třídu, která je následně zabalené v dvě přetížené `CopyToDataTable<T>` metody rozšíření. `Shred` Metodu `ObjectShredder<T>` třída vrací vyplněné <xref:System.Data.DataTable> a přijímá tři vstupní parametry: <xref:System.Collections.Generic.IEnumerable%601> zdroje, <xref:System.Data.DataTable>a <xref:System.Data.LoadOption> výčtu. Počáteční schématu vráceného <xref:System.Data.DataTable> je na základě schématu typu `T`. Pokud je existující tabulky je zadán jako vstup, musí být konzistentní se schématem typu schématu `T`. Každé veřejné vlastnosti a pole typu `T` je převedena na <xref:System.Data.DataColumn> ve vrácené tabulce. Pokud zdrojové sekvence obsahuje typ odvozený z `T`, se rozšířit schéma vrácené tabulky pro všechny další veřejné vlastnosti nebo pole.  
  
 Příklady použití vlastní `CopyToDataTable<T>` metody, naleznete v tématu [vytvoření datové tabulky z dotazu](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>K implementaci vlastních CopyToDataTable\<T > metodami v aplikaci  
  
1.  Implementace `ObjectShredder<T>` třídy za účelem vytvoření <xref:System.Data.DataTable> ze <xref:System.Collections.Generic.IEnumerable%601> zdroje:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    Předchozí příklad předpokládá, že vlastnosti `DataColumn` nejsou typy připouštějící hodnotu Null. Zpracování vlastností s typy s možnou hodnotou Null, použijte následující kód:

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2.  Implementovat vlastní `CopyToDataTable<T>` rozšiřující metody ve třídě:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  Přidat `ObjectShredder<T>` třídy a `CopyToDataTable<T>` rozšiřující metody pro vaši aplikaci.  
  
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
- [Vytvoření datové tabulky z dotazu](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)
- [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)

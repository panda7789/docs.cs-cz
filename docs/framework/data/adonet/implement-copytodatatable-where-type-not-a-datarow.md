---
title: 'Postupy: implementace CopyToDataTable&lt;T&gt; kde obecného typu T není DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 77adcd1f2070ba3ccfe036d37384a7a855ebf132
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-implement-copytodatatablelttgt-where-the-generic-type-t-is-not-a-datarow"></a>Postupy: implementace CopyToDataTable&lt;T&gt; kde obecného typu T není DataRow
<xref:System.Data.DataTable> Objektu se často používá pro datovou vazbu. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda přebírá výsledky dotazu a zkopíruje data do <xref:System.Data.DataTable>, který pak může být použit pro datovou vazbu. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metody, ale pracovat pouze v <xref:System.Collections.Generic.IEnumerable%601> zdroje kde obecný parametr `T` je typu <xref:System.Data.DataRow>. I když to je užitečné, neumožňuje tabulky má být vytvořen z posloupnost Skalární typy, dotazy, které anonymní typy projektů nebo dotazy, které provádějí spoje tabulky platná.  
  
 Toto téma popisuje, jak implementovat dvě vlastní `CopyToDataTable<T>` rozšiřující metody, které přijímají obecný parametr `T` typu jinak než <xref:System.Data.DataRow>. Logika pro vytvoření <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> je součástí zdroje `ObjectShredder<T>` třídy, která je vnořena ve dvou přetížený `CopyToDataTable<T>` rozšiřující metody. `Shred` Metodu `ObjectShredder<T>` třída vrátí vyplněný <xref:System.Data.DataTable> a přijímá tři vstupní parametry: <xref:System.Collections.Generic.IEnumerable%601> zdroje, <xref:System.Data.DataTable>a <xref:System.Data.LoadOption> – výčet. Schéma počáteční vrácený <xref:System.Data.DataTable> je založena na schéma typu `T`. Pokud se stávající tabulka je zadaný jako vstup, schéma musí být konzistentní se schématem typu `T`. Každé veřejné vlastnosti a pole typu `T` jsou převedeny na <xref:System.Data.DataColumn> ve vrácené tabulce. Pokud zdrojové sekvence obsahuje typ odvozený z `T`, je rozšířit schéma vrácené tabulky pro všechny další veřejné vlastnosti nebo pole.  
  
 Příklady použití vlastní `CopyToDataTable<T>` metody, najdete v části [vytváření DataTable z dotaz](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>K implementaci vlastních CopyToDataTable\<T > metody v aplikaci  
  
1.  Implementace `ObjectShredder<T>` třídy za účelem vytvoření <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> zdroje:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  
  
2.  Implementovat vlastní `CopyToDataTable<T>` rozšiřující metody ve třídě:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  Přidat `ObjectShredder<T>` třídy a `CopyToDataTable<T>` rozšiřující metody pro vaše aplikace.  
  
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
 [Vytvoření datové tabulky z dotazu](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)

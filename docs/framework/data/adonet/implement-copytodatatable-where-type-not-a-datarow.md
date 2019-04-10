---
title: 'Postupy: Implementace CopyToDataTable<T>, kde obecný typ není DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 120b4bf22e310bee73ba006cfe5a060d0ecd9d65
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338940"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="5c288-102">Postupy: Implementace CopyToDataTable\<T > kde obecný typ není DataRow</span><span class="sxs-lookup"><span data-stu-id="5c288-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="5c288-103"><xref:System.Data.DataTable> Objektu se často používá k vytváření datových vazeb.</span><span class="sxs-lookup"><span data-stu-id="5c288-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="5c288-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda přijímá výsledky dotazu a zkopíruje data do <xref:System.Data.DataTable>, který potom slouží pro vytváření datových vazeb.</span><span class="sxs-lookup"><span data-stu-id="5c288-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="5c288-105"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metody, ale pracovat pouze s <xref:System.Collections.Generic.IEnumerable%601> zdroje kde obecný parametr `T` je typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="5c288-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="5c288-106">I když to je užitečné, neumožňuje tabulky, který se má vytvořit ze sekvence Skalární typy, dotazy, které anonymní typy projektů nebo dotazy, které provádějí spoje tabulky platná.</span><span class="sxs-lookup"><span data-stu-id="5c288-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="5c288-107">Toto téma popisuje, jak implementovat dvě vlastní `CopyToDataTable<T>` rozšiřující metody, které přijímají obecný parametr `T` typu jiného než <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="5c288-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="5c288-108">Logiku pro vytvoření <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> je součástí zdroje `ObjectShredder<T>` třídu, která je následně zabalené v dvě přetížené `CopyToDataTable<T>` metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5c288-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="5c288-109">`Shred` Metodu `ObjectShredder<T>` třída vrací vyplněné <xref:System.Data.DataTable> a přijímá tři vstupní parametry: <xref:System.Collections.Generic.IEnumerable%601> zdroje, <xref:System.Data.DataTable>a <xref:System.Data.LoadOption> výčtu.</span><span class="sxs-lookup"><span data-stu-id="5c288-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="5c288-110">Počáteční schématu vráceného <xref:System.Data.DataTable> je na základě schématu typu `T`.</span><span class="sxs-lookup"><span data-stu-id="5c288-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="5c288-111">Pokud je existující tabulky je zadán jako vstup, musí být konzistentní se schématem typu schématu `T`.</span><span class="sxs-lookup"><span data-stu-id="5c288-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="5c288-112">Každé veřejné vlastnosti a pole typu `T` je převedena na <xref:System.Data.DataColumn> ve vrácené tabulce.</span><span class="sxs-lookup"><span data-stu-id="5c288-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="5c288-113">Pokud zdrojové sekvence obsahuje typ odvozený z `T`, se rozšířit schéma vrácené tabulky pro všechny další veřejné vlastnosti nebo pole.</span><span class="sxs-lookup"><span data-stu-id="5c288-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="5c288-114">Příklady použití vlastní `CopyToDataTable<T>` metody, naleznete v tématu [vytvoření datové tabulky z dotazu](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="5c288-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="5c288-115">K implementaci vlastních CopyToDataTable\<T > metodami v aplikaci</span><span class="sxs-lookup"><span data-stu-id="5c288-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="5c288-116">Implementace `ObjectShredder<T>` třídy za účelem vytvoření <xref:System.Data.DataTable> ze <xref:System.Collections.Generic.IEnumerable%601> zdroje:</span><span class="sxs-lookup"><span data-stu-id="5c288-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="5c288-117">Předchozí příklad předpokládá, že vlastnosti `DataColumn` nejsou typy připouštějící hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="5c288-117">The preceding example assumes that the properties of the `DataColumn` are not nullable types.</span></span> <span data-ttu-id="5c288-118">Zpracování vlastností s typy s možnou hodnotou Null, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="5c288-118">To handle properties with nullable types, use the following code:</span></span>

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. <span data-ttu-id="5c288-119">Implementovat vlastní `CopyToDataTable<T>` rozšiřující metody ve třídě:</span><span class="sxs-lookup"><span data-stu-id="5c288-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="5c288-120">Přidat `ObjectShredder<T>` třídy a `CopyToDataTable<T>` rozšiřující metody pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5c288-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5c288-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c288-121">See also</span></span>

- [<span data-ttu-id="5c288-122">Vytvoření datové tabulky z dotazu</span><span class="sxs-lookup"><span data-stu-id="5c288-122">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="5c288-123">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="5c288-123">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)

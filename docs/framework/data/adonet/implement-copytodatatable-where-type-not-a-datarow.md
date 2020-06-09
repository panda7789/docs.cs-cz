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
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="d6388-102">Postupy: Implementace CopyToDataTable\<T>, kde obecný typ není DataRow</span><span class="sxs-lookup"><span data-stu-id="d6388-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="d6388-103"><xref:System.Data.DataTable>Objekt se často používá pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="d6388-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="d6388-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metoda přijímá výsledky dotazu a kopíruje data do <xref:System.Data.DataTable> , které lze následně použít pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="d6388-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="d6388-105"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metody však pracují pouze na <xref:System.Collections.Generic.IEnumerable%601> zdroji, kde je obecný parametr `T` typu <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="d6388-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="d6388-106">I když je to užitečné, neumožňuje vytvářet tabulky ze sekvencí skalárních typů, od dotazů, které jsou anonymní typy projektu, nebo z dotazů, které provádějí spojení s tabulkou.</span><span class="sxs-lookup"><span data-stu-id="d6388-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="d6388-107">Toto téma popisuje, jak implementovat dvě vlastní `CopyToDataTable<T>` metody rozšíření, které přijímají obecný parametr `T` jiného typu než <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="d6388-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="d6388-108">Logika pro vytvoření <xref:System.Data.DataTable> ze <xref:System.Collections.Generic.IEnumerable%601> zdroje je obsažena ve `ObjectShredder<T>` třídě, která je poté zabalena do dvou přetížených `CopyToDataTable<T>` rozšiřujících metod.</span><span class="sxs-lookup"><span data-stu-id="d6388-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="d6388-109">`Shred`Metoda `ObjectShredder<T>` třídy vrátí vyplněné <xref:System.Data.DataTable> a akceptuje tři vstupní parametry: <xref:System.Collections.Generic.IEnumerable%601> zdroj, a <xref:System.Data.DataTable> a <xref:System.Data.LoadOption> výčet.</span><span class="sxs-lookup"><span data-stu-id="d6388-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="d6388-110">Počáteční schéma vráceného <xref:System.Data.DataTable> je založeno na schématu typu `T` .</span><span class="sxs-lookup"><span data-stu-id="d6388-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="d6388-111">Pokud je jako vstup zadána stávající tabulka, schéma musí být konzistentní se schématem typu `T` .</span><span class="sxs-lookup"><span data-stu-id="d6388-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="d6388-112">Každá veřejná vlastnost a pole typu `T` je převedena na typ <xref:System.Data.DataColumn> ve vrácené tabulce.</span><span class="sxs-lookup"><span data-stu-id="d6388-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="d6388-113">Pokud zdrojová sekvence obsahuje typ odvozený z `T` , je schéma vrácených tabulek rozšířeno pro všechny další veřejné vlastnosti nebo pole.</span><span class="sxs-lookup"><span data-stu-id="d6388-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="d6388-114">Příklady použití vlastních `CopyToDataTable<T>` metod naleznete v tématu [vytvoření objektu DataTable z dotazu](creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="d6388-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="d6388-115">Implementace vlastních \<T> metod CopyToDataTable ve vaší aplikaci</span><span class="sxs-lookup"><span data-stu-id="d6388-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="d6388-116">Implementujte `ObjectShredder<T>` třídu pro vytvoření <xref:System.Data.DataTable> ze <xref:System.Collections.Generic.IEnumerable%601> zdroje:</span><span class="sxs-lookup"><span data-stu-id="d6388-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="d6388-117">Předchozí příklad předpokládá, že vlastnosti a pole nemůžou `DataColumn` mít typy hodnot s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="d6388-117">The preceding example assumes that the properties and fields of the `DataColumn` are not nullable value types.</span></span> <span data-ttu-id="d6388-118">Chcete-li zpracovat vlastnosti a pole s typy hodnot s možnou hodnotou null, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="d6388-118">To handle properties and fields with nullable value types, use the following code:</span></span>

    ```csharp
    // Nullable-aware code for properties.
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);

    // Nullable-aware code for fields.
    DataColumn dc = table.Columns.Contains(f.Name) ? table.Columns[f.Name] : table.Columns.Add(f.Name, Nullable.GetUnderlyingType(f.FieldType) ?? f.FieldType);
    ```

2. <span data-ttu-id="d6388-119">Implementujte vlastní `CopyToDataTable<T>` metody rozšíření ve třídě:</span><span class="sxs-lookup"><span data-stu-id="d6388-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="d6388-120">Přidejte `ObjectShredder<T>` `CopyToDataTable<T>` do své aplikace metody třídy a rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d6388-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6388-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6388-121">See also</span></span>

- [<span data-ttu-id="d6388-122">Vytvoření datové tabulky z dotazu</span><span class="sxs-lookup"><span data-stu-id="d6388-122">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="d6388-123">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="d6388-123">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)

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
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="1dffb-102">Postupy: Implementujte\<CopyToDataTable T >, kde obecný typ T není DataRow.</span><span class="sxs-lookup"><span data-stu-id="1dffb-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="1dffb-103"><xref:System.Data.DataTable> Objekt se často používá pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="1dffb-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="1dffb-104">Metoda přijímá výsledky dotazu a kopíruje data <xref:System.Data.DataTable>do, které lze následně použít pro datovou vazbu. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A></span><span class="sxs-lookup"><span data-stu-id="1dffb-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="1dffb-105">Metody však pracují pouze <xref:System.Collections.Generic.IEnumerable%601> na zdroji, kde je obecný parametr `T` typu <xref:System.Data.DataRow>. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A></span><span class="sxs-lookup"><span data-stu-id="1dffb-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="1dffb-106">I když je to užitečné, neumožňuje vytvářet tabulky ze sekvencí skalárních typů, od dotazů, které jsou anonymní typy projektu, nebo z dotazů, které provádějí spojení s tabulkou.</span><span class="sxs-lookup"><span data-stu-id="1dffb-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="1dffb-107">Toto téma popisuje, jak implementovat dvě vlastní `CopyToDataTable<T>` metody rozšíření, které přijímají obecný `T` parametr jiného typu než <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="1dffb-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="1dffb-108">Logika <xref:System.Data.DataTable> pro vytvoření <xref:System.Collections.Generic.IEnumerable%601> ze `CopyToDataTable<T>` zdroje je obsažena ve třídě,kterájepotézabalenadodvoupřetíženýchrozšiřujícíchmetod.`ObjectShredder<T>`</span><span class="sxs-lookup"><span data-stu-id="1dffb-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="1dffb-109"><xref:System.Data.DataTable> <xref:System.Data.LoadOption> <xref:System.Data.DataTable>Metoda třídy vrátí vyplněné a akceptuje tři vstupní parametry: <xref:System.Collections.Generic.IEnumerable%601> zdroj, a a výčet. `ObjectShredder<T>` `Shred`</span><span class="sxs-lookup"><span data-stu-id="1dffb-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="1dffb-110">Počáteční schéma vráceného <xref:System.Data.DataTable> je založeno na schématu typu `T`.</span><span class="sxs-lookup"><span data-stu-id="1dffb-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="1dffb-111">Pokud je jako vstup zadána stávající tabulka, schéma musí být konzistentní se schématem typu `T`.</span><span class="sxs-lookup"><span data-stu-id="1dffb-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="1dffb-112">Každá veřejná vlastnost a pole typu je převedena `T` <xref:System.Data.DataColumn> na typ ve vrácené tabulce.</span><span class="sxs-lookup"><span data-stu-id="1dffb-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="1dffb-113">Pokud zdrojová sekvence obsahuje typ odvozený z `T`, je schéma vrácených tabulek rozšířeno pro všechny další veřejné vlastnosti nebo pole.</span><span class="sxs-lookup"><span data-stu-id="1dffb-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="1dffb-114">Příklady použití vlastních `CopyToDataTable<T>` metod naleznete v tématu [vytvoření objektu DataTable z dotazu](creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="1dffb-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="1dffb-115">Implementace vlastních metod CopyToDataTable\<T > v aplikaci</span><span class="sxs-lookup"><span data-stu-id="1dffb-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="1dffb-116">Implementujte <xref:System.Data.DataTable> <xref:System.Collections.Generic.IEnumerable%601> třídu pro vytvoření ze zdroje: `ObjectShredder<T>`</span><span class="sxs-lookup"><span data-stu-id="1dffb-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="1dffb-117">Předchozí příklad předpokládá, že vlastnosti `DataColumn` typu neumožňují hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="1dffb-117">The preceding example assumes that the properties of the `DataColumn` are not nullable types.</span></span> <span data-ttu-id="1dffb-118">Chcete-li zpracovat vlastnosti s typy s možnou hodnotou null, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="1dffb-118">To handle properties with nullable types, use the following code:</span></span>

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. <span data-ttu-id="1dffb-119">Implementujte vlastní `CopyToDataTable<T>` metody rozšíření ve třídě:</span><span class="sxs-lookup"><span data-stu-id="1dffb-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="1dffb-120">Přidejte do své aplikace `CopyToDataTable<T>` metody třídyarozšíření.`ObjectShredder<T>`</span><span class="sxs-lookup"><span data-stu-id="1dffb-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1dffb-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1dffb-121">See also</span></span>

- [<span data-ttu-id="1dffb-122">Vytvoření datové tabulky z dotazu</span><span class="sxs-lookup"><span data-stu-id="1dffb-122">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="1dffb-123">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="1dffb-123">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)

---
title: "Postupy: implementace CopyToDataTable&lt;T&gt; kde obecného typu T není DataRow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 44e54ef54173636246da1847d177cf4fd99ea818
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-copytodatatablelttgt-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="0c44a-102">Postupy: implementace CopyToDataTable&lt;T&gt; kde obecného typu T není DataRow</span><span class="sxs-lookup"><span data-stu-id="0c44a-102">How to: Implement CopyToDataTable&lt;T&gt; Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="0c44a-103"><xref:System.Data.DataTable> Objektu se často používá pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="0c44a-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="0c44a-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda přebírá výsledky dotazu a zkopíruje data do <xref:System.Data.DataTable>, který pak může být použit pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="0c44a-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="0c44a-105"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metody, ale pracovat pouze v <xref:System.Collections.Generic.IEnumerable%601> zdroje kde obecný parametr `T` je typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="0c44a-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="0c44a-106">I když to je užitečné, neumožňuje tabulky má být vytvořen z posloupnost Skalární typy, dotazy, které anonymní typy projektů nebo dotazy, které provádějí spoje tabulky platná.</span><span class="sxs-lookup"><span data-stu-id="0c44a-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="0c44a-107">Toto téma popisuje, jak implementovat dvě vlastní `CopyToDataTable<T>` rozšiřující metody, které přijímají obecný parametr `T` typu jinak než <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="0c44a-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="0c44a-108">Logika pro vytvoření <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> je součástí zdroje `ObjectShredder<T>` třídy, která je vnořena ve dvou přetížený `CopyToDataTable<T>` rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="0c44a-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="0c44a-109">`Shred` Metodu `ObjectShredder<T>` třída vrátí vyplněný <xref:System.Data.DataTable> a přijímá tři vstupní parametry: <xref:System.Collections.Generic.IEnumerable%601> zdroje, <xref:System.Data.DataTable>a <xref:System.Data.LoadOption> – výčet.</span><span class="sxs-lookup"><span data-stu-id="0c44a-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="0c44a-110">Schéma počáteční vrácený <xref:System.Data.DataTable> je založena na schéma typu `T`.</span><span class="sxs-lookup"><span data-stu-id="0c44a-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="0c44a-111">Pokud se stávající tabulka je zadaný jako vstup, schéma musí být konzistentní se schématem typu `T`.</span><span class="sxs-lookup"><span data-stu-id="0c44a-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="0c44a-112">Každé veřejné vlastnosti a pole typu `T` jsou převedeny na <xref:System.Data.DataColumn> ve vrácené tabulce.</span><span class="sxs-lookup"><span data-stu-id="0c44a-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="0c44a-113">Pokud zdrojové sekvence obsahuje typ odvozený z `T`, je rozšířit schéma vrácené tabulky pro všechny další veřejné vlastnosti nebo pole.</span><span class="sxs-lookup"><span data-stu-id="0c44a-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="0c44a-114">Příklady použití vlastní `CopyToDataTable<T>` metody, najdete v části [vytváření DataTable z dotaz](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="0c44a-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="0c44a-115">K implementaci vlastních CopyToDataTable\<T > metody v aplikaci</span><span class="sxs-lookup"><span data-stu-id="0c44a-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1.  <span data-ttu-id="0c44a-116">Implementace `ObjectShredder<T>` třídy za účelem vytvoření <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> zdroje:</span><span class="sxs-lookup"><span data-stu-id="0c44a-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  
  
2.  <span data-ttu-id="0c44a-117">Implementovat vlastní `CopyToDataTable<T>` rozšiřující metody ve třídě:</span><span class="sxs-lookup"><span data-stu-id="0c44a-117">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  <span data-ttu-id="0c44a-118">Přidat `ObjectShredder<T>` třídy a `CopyToDataTable<T>` rozšiřující metody pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="0c44a-118">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c44a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c44a-119">See Also</span></span>  
 [<span data-ttu-id="0c44a-120">Vytváření DataTable z dotazu</span><span class="sxs-lookup"><span data-stu-id="0c44a-120">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 [<span data-ttu-id="0c44a-121">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="0c44a-121">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)

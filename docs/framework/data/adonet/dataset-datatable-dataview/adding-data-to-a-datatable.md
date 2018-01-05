---
title: "Přidání dat do DataTable"
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
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 91aa84b0a3d381512faf74f350dc4b43e9a3c598
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="e5238-102">Přidání dat do DataTable</span><span class="sxs-lookup"><span data-stu-id="e5238-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="e5238-103">Po vytvoření <xref:System.Data.DataTable> a definovat jeho strukturu pomocí sloupců a omezení, můžete přidat nové řádky dat do tabulky.</span><span class="sxs-lookup"><span data-stu-id="e5238-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="e5238-104">Pokud chcete přidat nový řádek, deklarovat nové proměnné jako typ <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="e5238-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="e5238-105">Nový **DataRow** při volání se vrátí objekt <xref:System.Data.DataTable.NewRow%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e5238-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="e5238-106">**DataTable** pak vytvoří **DataRow** objektu podle struktura tabulky, podle definice <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="e5238-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="e5238-107">Následující příklad ukazuje, jak vytvořit nový řádek voláním **NewRow** metoda.</span><span class="sxs-lookup"><span data-stu-id="e5238-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="e5238-108">Potom můžete upravit nově přidané řádku pomocí index nebo název sloupce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e5238-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="e5238-109">Po vloží se data do nového řádku **přidat** metoda se používá k přidání řádku, který má <xref:System.Data.DataRowCollection>, uvedené v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e5238-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="e5238-110">Můžete také zavolat **přidat** metodu přidejte nový řádek předáním v pole hodnot, zadané jako <xref:System.Object>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e5238-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="e5238-111">Předávání pole hodnoty, zadané jako **objekt**do **přidat** metoda vytvoří nový řádek v tabulce a nastaví její hodnoty ve sloupcích na hodnoty v poli objektu.</span><span class="sxs-lookup"><span data-stu-id="e5238-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="e5238-112">Všimněte si, že jsou hodnoty v poli postupně namapovat na sloupce, podle pořadí, ve kterém se zobrazí v tabulce.</span><span class="sxs-lookup"><span data-stu-id="e5238-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="e5238-113">Následující příklad přidá 10 řádků do nově vytvořený **zákazníci** tabulky.</span><span class="sxs-lookup"><span data-stu-id="e5238-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)   
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5238-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5238-114">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="e5238-115">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="e5238-115">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="e5238-116">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="e5238-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

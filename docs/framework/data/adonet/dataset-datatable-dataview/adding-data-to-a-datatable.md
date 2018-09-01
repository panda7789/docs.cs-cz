---
title: Přidání dat do datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: c1ebe2d735924c559f450f4041884dc9845e4fe0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396082"
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="ba009-102">Přidání dat do datové tabulky</span><span class="sxs-lookup"><span data-stu-id="ba009-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="ba009-103">Po vytvoření <xref:System.Data.DataTable> a definovat jeho strukturu pomocí sloupců a omezení, můžete přidat nové řádky dat do tabulky.</span><span class="sxs-lookup"><span data-stu-id="ba009-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="ba009-104">Chcete-li přidat nový řádek, deklarovat novou proměnnou jako typ <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="ba009-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="ba009-105">Nový **DataRow** objekt je vrácen při volání <xref:System.Data.DataTable.NewRow%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ba009-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="ba009-106">**DataTable** vytvoří **DataRow** objektu na základě struktury tabulky, tak jak je definoval <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="ba009-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="ba009-107">Následující příklad ukazuje, jak vytvořit nový řádek voláním **NewRow** metody.</span><span class="sxs-lookup"><span data-stu-id="ba009-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="ba009-108">Pak můžete pracovat s nově přidaný řádek pomocí index nebo název sloupce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ba009-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="ba009-109">Po vložení dat do nového řádku, **přidat** metoda se používá k přidání řádku, který má <xref:System.Data.DataRowCollection>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ba009-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="ba009-110">Můžete také volat **přidat** způsob, jak přidat nový řádek předáním pole hodnot, zadaný jako <xref:System.Object>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ba009-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="ba009-111">Předá pole hodnot typu **objekt**, možnosti **přidat** metoda vytvoří nový řádek do tabulky a nastaví její hodnoty sloupců na hodnoty v poli objektu.</span><span class="sxs-lookup"><span data-stu-id="ba009-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="ba009-112">Všimněte si, že hodnoty v poli odpovídají postupně na sloupce v pořadí, v jakém jsou uvedeny v tabulce.</span><span class="sxs-lookup"><span data-stu-id="ba009-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="ba009-113">Následující příklad přidá 10 řádků na nově vytvořený **zákazníkům** tabulky.</span><span class="sxs-lookup"><span data-stu-id="ba009-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ba009-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba009-114">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="ba009-115">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="ba009-115">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="ba009-116">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ba009-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

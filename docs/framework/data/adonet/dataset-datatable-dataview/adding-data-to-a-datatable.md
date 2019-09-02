---
title: Přidání dat do datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 91c635e2bc2ed617e8c45171d9ec7d7359b9ca88
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205488"
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="598d2-102">Přidání dat do datové tabulky</span><span class="sxs-lookup"><span data-stu-id="598d2-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="598d2-103">Po vytvoření <xref:System.Data.DataTable> a definování struktury pomocí sloupců a omezení můžete do tabulky přidat nové řádky dat.</span><span class="sxs-lookup"><span data-stu-id="598d2-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="598d2-104">Chcete-li přidat nový řádek, deklarujte novou proměnnou jako <xref:System.Data.DataRow>typ.</span><span class="sxs-lookup"><span data-stu-id="598d2-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="598d2-105">Při volání <xref:System.Data.DataTable.NewRow%2A> metody je vrácen nový objekt DataRow.</span><span class="sxs-lookup"><span data-stu-id="598d2-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="598d2-106">Objekt **DataTable** potom vytvoří objekt **DataRow** na základě struktury tabulky, jak je definováno v <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="598d2-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="598d2-107">Následující příklad ukazuje, jak vytvořit nový řádek voláním metody **NewRow** .</span><span class="sxs-lookup"><span data-stu-id="598d2-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="598d2-108">Následně můžete pomocí indexu nebo názvu sloupce manipulovat s nově přidaným řádkem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="598d2-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="598d2-109">Po vložení dat do nového řádku je použita metoda **Add** k přidání řádku do <xref:System.Data.DataRowCollection>, který je zobrazen v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="598d2-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="598d2-110">Můžete také zavolat metodu **Add** pro přidání nového řádku předáním pole hodnot, <xref:System.Object>jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="598d2-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="598d2-111">Předání pole hodnot, které je zadáno jako **objekt**, do metody **Add** vytvoří nový řádek v tabulce a nastaví hodnoty jejich sloupce na hodnoty v poli objektů.</span><span class="sxs-lookup"><span data-stu-id="598d2-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="598d2-112">Všimněte si, že hodnoty v poli jsou podle pořadí, ve kterém jsou uvedeny v tabulce, porovnány se sloupci.</span><span class="sxs-lookup"><span data-stu-id="598d2-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="598d2-113">Následující příklad přidá 10 řádků do tabulky nově vytvořené **zákazníky** .</span><span class="sxs-lookup"><span data-stu-id="598d2-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="598d2-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="598d2-114">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="598d2-115">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="598d2-115">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="598d2-116">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="598d2-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

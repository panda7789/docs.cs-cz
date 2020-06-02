---
title: Přidání dat do datové tabulky
description: Chcete-li přidat nové řádky dat do tabulky v ADO.NET, po vytvoření objektu DataTable a definování jeho struktury pomocí sloupců a omezení, přečtěte si tento ukázkový kód.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 94ebc97d5f90b5bb92186ba6f33015633bd01127
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286931"
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="42526-103">Přidání dat do datové tabulky</span><span class="sxs-lookup"><span data-stu-id="42526-103">Adding Data to a DataTable</span></span>
<span data-ttu-id="42526-104">Po vytvoření <xref:System.Data.DataTable> a definování struktury pomocí sloupců a omezení můžete do tabulky přidat nové řádky dat.</span><span class="sxs-lookup"><span data-stu-id="42526-104">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="42526-105">Chcete-li přidat nový řádek, deklarujte novou proměnnou jako typ <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="42526-105">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="42526-106">Při volání metody je vrácen nový objekt **DataRow** <xref:System.Data.DataTable.NewRow%2A> .</span><span class="sxs-lookup"><span data-stu-id="42526-106">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="42526-107">Objekt **DataTable** potom vytvoří objekt **DataRow** na základě struktury tabulky, jak je definováno v <xref:System.Data.DataColumnCollection> .</span><span class="sxs-lookup"><span data-stu-id="42526-107">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="42526-108">Následující příklad ukazuje, jak vytvořit nový řádek voláním metody **NewRow** .</span><span class="sxs-lookup"><span data-stu-id="42526-108">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="42526-109">Následně můžete pomocí indexu nebo názvu sloupce manipulovat s nově přidaným řádkem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="42526-109">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="42526-110">Po vložení dat do nového řádku je použita metoda **Add** k přidání řádku do, který je <xref:System.Data.DataRowCollection> zobrazen v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="42526-110">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="42526-111">Můžete také zavolat metodu **Add** pro přidání nového řádku předáním pole hodnot, jak je <xref:System.Object> znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="42526-111">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="42526-112">Předání pole hodnot, které je zadáno jako **objekt**, do metody **Add** vytvoří nový řádek v tabulce a nastaví hodnoty jejich sloupce na hodnoty v poli objektů.</span><span class="sxs-lookup"><span data-stu-id="42526-112">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="42526-113">Všimněte si, že hodnoty v poli jsou podle pořadí, ve kterém jsou uvedeny v tabulce, porovnány se sloupci.</span><span class="sxs-lookup"><span data-stu-id="42526-113">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="42526-114">Následující příklad přidá 10 řádků do tabulky nově vytvořené **zákazníky** .</span><span class="sxs-lookup"><span data-stu-id="42526-114">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="42526-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="42526-115">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="42526-116">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="42526-116">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="42526-117">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="42526-117">ADO.NET Overview</span></span>](../ado-net-overview.md)

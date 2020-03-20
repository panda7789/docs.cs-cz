---
title: Přidání dat do datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 02d7f94259cc56513be404c5539ca7015d5f3533
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151530"
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="3e83d-102">Přidání dat do datové tabulky</span><span class="sxs-lookup"><span data-stu-id="3e83d-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="3e83d-103">Po vytvoření <xref:System.Data.DataTable> a definování jeho struktury pomocí sloupců a omezení můžete do tabulky přidat nové řádky dat.</span><span class="sxs-lookup"><span data-stu-id="3e83d-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="3e83d-104">Chcete-li přidat nový řádek, deklarujte novou proměnnou jako typ <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="3e83d-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="3e83d-105">Nový **Objekt DataRow** je vrácena <xref:System.Data.DataTable.NewRow%2A> při volání metody.</span><span class="sxs-lookup"><span data-stu-id="3e83d-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="3e83d-106">**DataTable** pak vytvoří **Objekt DataRow** na základě struktury tabulky, <xref:System.Data.DataColumnCollection>jak je definováno .</span><span class="sxs-lookup"><span data-stu-id="3e83d-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="3e83d-107">Následující příklad ukazuje, jak vytvořit nový řádek voláním **NewRow** metoda.</span><span class="sxs-lookup"><span data-stu-id="3e83d-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="3e83d-108">Nově přidaný řádek pak můžete manipulovat pomocí indexu nebo názvu sloupce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3e83d-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="3e83d-109">Po vložení dat do nového řádku se metoda **Add** použije <xref:System.Data.DataRowCollection>k přidání řádku do následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="3e83d-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="3e83d-110">Můžete také volat **Add** metoda přidat nový řádek předáním v poli <xref:System.Object>hodnot, zadali jako , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3e83d-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="3e83d-111">Předáním pole hodnot zadaných jako **Object** **vytvoříte** nový řádek uvnitř tabulky a nastavíte jeho hodnoty sloupců na hodnoty v poli objektů.</span><span class="sxs-lookup"><span data-stu-id="3e83d-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="3e83d-112">Všimněte si, že hodnoty v poli jsou spárovány se sloupci na základě pořadí, ve kterém se zobrazují v tabulce.</span><span class="sxs-lookup"><span data-stu-id="3e83d-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="3e83d-113">Následující příklad přidá 10 řádků do nově vytvořené tabulky **Zákazníci.**</span><span class="sxs-lookup"><span data-stu-id="3e83d-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3e83d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e83d-114">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="3e83d-115">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="3e83d-115">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="3e83d-116">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3e83d-116">ADO.NET Overview</span></span>](../ado-net-overview.md)

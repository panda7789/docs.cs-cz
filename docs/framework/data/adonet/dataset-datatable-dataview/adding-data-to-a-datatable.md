---
title: Přidání dat do datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: ec4ad84a39afe21ef77507732e5e0e417d45f3e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104283"
---
# <a name="adding-data-to-a-datatable"></a>Přidání dat do datové tabulky
Po vytvoření <xref:System.Data.DataTable> a definovat jeho strukturu pomocí sloupců a omezení, můžete přidat nové řádky dat do tabulky. Chcete-li přidat nový řádek, deklarovat novou proměnnou jako typ <xref:System.Data.DataRow>. Nový **DataRow** objekt je vrácen při volání <xref:System.Data.DataTable.NewRow%2A> metody. **DataTable** vytvoří **DataRow** objektu na základě struktury tabulky, tak jak je definoval <xref:System.Data.DataColumnCollection>.  
  
 Následující příklad ukazuje, jak vytvořit nový řádek voláním **NewRow** metody.  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Pak můžete pracovat s nově přidaný řádek pomocí index nebo název sloupce, jak je znázorněno v následujícím příkladu.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Po vložení dat do nového řádku, **přidat** metoda se používá k přidání řádku, který má <xref:System.Data.DataRowCollection>, jak je znázorněno v následujícím kódu.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Můžete také volat **přidat** způsob, jak přidat nový řádek předáním pole hodnot, zadaný jako <xref:System.Object>, jak je znázorněno v následujícím příkladu.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 Předá pole hodnot typu **objekt**, možnosti **přidat** metoda vytvoří nový řádek do tabulky a nastaví její hodnoty sloupců na hodnoty v poli objektu. Všimněte si, že hodnoty v poli odpovídají postupně na sloupce v pořadí, v jakém jsou uvedeny v tabulce.  
  
 Následující příklad přidá 10 řádků na nově vytvořený **zákazníkům** tabulky.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

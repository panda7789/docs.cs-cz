---
title: Přidání dat do DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: c58f64dba0bceb4a35c67e16193a6627837436e0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="adding-data-to-a-datatable"></a>Přidání dat do DataTable
Po vytvoření <xref:System.Data.DataTable> a definovat jeho strukturu pomocí sloupců a omezení, můžete přidat nové řádky dat do tabulky. Pokud chcete přidat nový řádek, deklarovat nové proměnné jako typ <xref:System.Data.DataRow>. Nový **DataRow** při volání se vrátí objekt <xref:System.Data.DataTable.NewRow%2A> metoda. **DataTable** pak vytvoří **DataRow** objektu podle struktura tabulky, podle definice <xref:System.Data.DataColumnCollection>.  
  
 Následující příklad ukazuje, jak vytvořit nový řádek voláním **NewRow** metoda.  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Potom můžete upravit nově přidané řádku pomocí index nebo název sloupce, jak je znázorněno v následujícím příkladu.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Po vloží se data do nového řádku **přidat** metoda se používá k přidání řádku, který má <xref:System.Data.DataRowCollection>, uvedené v následujícím kódu.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Můžete také zavolat **přidat** metodu přidejte nový řádek předáním v pole hodnot, zadané jako <xref:System.Object>, jak je znázorněno v následujícím příkladu.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 Předávání pole hodnoty, zadané jako **objekt**do **přidat** metoda vytvoří nový řádek v tabulce a nastaví její hodnoty ve sloupcích na hodnoty v poli objektu. Všimněte si, že jsou hodnoty v poli postupně namapovat na sloupce, podle pořadí, ve kterém se zobrazí v tabulce.  
  
 Následující příklad přidá 10 řádků do nově vytvořený **zákazníci** tabulky.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 29ba4a62b2c896e4ce5fa01929307ee82753495f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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

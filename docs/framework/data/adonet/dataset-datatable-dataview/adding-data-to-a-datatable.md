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
# <a name="adding-data-to-a-datatable"></a>Přidání dat do datové tabulky
Po vytvoření <xref:System.Data.DataTable> a definování struktury pomocí sloupců a omezení můžete do tabulky přidat nové řádky dat. Chcete-li přidat nový řádek, deklarujte novou proměnnou jako <xref:System.Data.DataRow>typ. Při volání <xref:System.Data.DataTable.NewRow%2A> metody je vrácen nový objekt DataRow. Objekt **DataTable** potom vytvoří objekt **DataRow** na základě struktury tabulky, jak je definováno v <xref:System.Data.DataColumnCollection>.  
  
 Následující příklad ukazuje, jak vytvořit nový řádek voláním metody **NewRow** .  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Následně můžete pomocí indexu nebo názvu sloupce manipulovat s nově přidaným řádkem, jak je znázorněno v následujícím příkladu.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Po vložení dat do nového řádku je použita metoda **Add** k přidání řádku do <xref:System.Data.DataRowCollection>, který je zobrazen v následujícím kódu.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Můžete také zavolat metodu **Add** pro přidání nového řádku předáním pole hodnot, <xref:System.Object>jak je znázorněno v následujícím příkladu.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 Předání pole hodnot, které je zadáno jako **objekt**, do metody **Add** vytvoří nový řádek v tabulce a nastaví hodnoty jejich sloupce na hodnoty v poli objektů. Všimněte si, že hodnoty v poli jsou podle pořadí, ve kterém jsou uvedeny v tabulce, porovnány se sloupci.  
  
 Následující příklad přidá 10 řádků do tabulky nově vytvořené **zákazníky** .  
  
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
- [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

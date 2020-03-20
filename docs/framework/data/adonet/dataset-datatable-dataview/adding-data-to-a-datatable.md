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
# <a name="adding-data-to-a-datatable"></a>Přidání dat do datové tabulky
Po vytvoření <xref:System.Data.DataTable> a definování jeho struktury pomocí sloupců a omezení můžete do tabulky přidat nové řádky dat. Chcete-li přidat nový řádek, deklarujte novou proměnnou jako typ <xref:System.Data.DataRow>. Nový **Objekt DataRow** je vrácena <xref:System.Data.DataTable.NewRow%2A> při volání metody. **DataTable** pak vytvoří **Objekt DataRow** na základě struktury tabulky, <xref:System.Data.DataColumnCollection>jak je definováno .  
  
 Následující příklad ukazuje, jak vytvořit nový řádek voláním **NewRow** metoda.  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Nově přidaný řádek pak můžete manipulovat pomocí indexu nebo názvu sloupce, jak je znázorněno v následujícím příkladu.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Po vložení dat do nového řádku se metoda **Add** použije <xref:System.Data.DataRowCollection>k přidání řádku do následujícího kódu.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Můžete také volat **Add** metoda přidat nový řádek předáním v poli <xref:System.Object>hodnot, zadali jako , jak je znázorněno v následujícím příkladu.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 Předáním pole hodnot zadaných jako **Object** **vytvoříte** nový řádek uvnitř tabulky a nastavíte jeho hodnoty sloupců na hodnoty v poli objektů. Všimněte si, že hodnoty v poli jsou spárovány se sloupci na základě pořadí, ve kterém se zobrazují v tabulce.  
  
 Následující příklad přidá 10 řádků do nově vytvořené tabulky **Zákazníci.**  
  
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

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)
- [Přehled ADO.NET](../ado-net-overview.md)

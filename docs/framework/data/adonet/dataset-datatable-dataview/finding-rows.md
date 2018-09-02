---
title: Hledání řádků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: daa8097bc5dfee203f988915b1e4a8bdcd2c50e0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408081"
---
# <a name="finding-rows"></a>Hledání řádků
Můžete hledat pomocí řádků podle jejich hodnoty klíče řazení <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>. Rozlišování velikosti písmen vyhledávání hodnoty v **najít** a **FindRows** metody je určeno **CaseSensitive** vlastnost základního <xref:System.Data.DataTable>. Hledání hodnoty musí odpovídat existující hodnoty klíče řazení v plné výši k vrácení výsledku.  
  
 **Najít** metoda vrátí celé číslo s indexem <xref:System.Data.DataRowView> , které by odpovídalo kritériím hledání. Pokud více než jeden řádek odpovídá kritériím hledání, pouze index první odpovídající **DataRowView** je vrácena. Pokud se nenajdou žádné shody, **najít** vrátí hodnotu -1.  
  
 Chcete-li vrátit výsledky hledání, které odpovídají více řádků, použijte **FindRows** metody. **FindRows** funguje stejně jako **najít** metody, s tím rozdílem, že se vrátí **DataRowView** pole, které odkazuje na všechny odpovídající řádky **DataView**. Pokud se nenajdou žádné shody, **DataRowView** pole bude prázdný.  
  
 Použít **najít** nebo **FindRows** metod je nutné zadat řazení order buď nastavením **ApplyDefaultSort** k **true** nebo s použitím **Řazení** vlastnost. Pokud není zadána žádná pořadí řazení, je vyvolána výjimka.  
  
 **Najít** a **FindRows** metody pole hodnot, které přijímají jako vstup, jehož délka shoduje s počtem sloupců v pořadí řazení. V případě řazení na jeden sloupec můžete předat hodnotu single. Pro pořadí řazení, který obsahuje více sloupců můžete předat pole objektů. Všimněte si, že pro řazení do více sloupců, hodnoty v poli objektu musí odpovídat pořadí sloupce zadané v **řazení** vlastnost **DataView**.  
  
 Následující příklad kódu ukazuje **najít** proti volané metody **DataView** s jedním sloupcem pořadí řazení.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 Pokud vaše **řazení** vlastnost určuje více sloupců, musí předat objekt pole s hodnotami vyhledávání pro každý sloupec v pořadí zadaném **řazení** vlastnosti, jako v následujícím příkladu kódu.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [Zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

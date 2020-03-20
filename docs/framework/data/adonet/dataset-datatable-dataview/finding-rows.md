---
title: Hledání řádků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: cfd4587f0dde7687ecf88bf6b31c44b90a2287ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151140"
---
# <a name="finding-rows"></a>Hledání řádků
Řádky můžete vyhledávat podle jejich hodnot klíče <xref:System.Data.DataView.Find%2A> řazení <xref:System.Data.DataView.FindRows%2A> pomocí <xref:System.Data.DataView>metody a . Rozlišování malých a velkých písmen vyhledávacích hodnot v find **a** **findrows** metody je určena **CaseSensitive** vlastnost podkladové <xref:System.Data.DataTable>. Vyhledávací hodnoty musí odpovídat existující hodnoty klíče řazení v plném rozsahu, aby se vrátil výsledek.  
  
 Find **Find** Metoda vrátí celé číslo s indexem, <xref:System.Data.DataRowView> který odpovídá kritériím vyhledávání. Pokud více než jeden řádek odpovídá kritériím hledání, je vrácen pouze index první odpovídající **DataRowView.** Pokud nejsou nalezeny žádné shody, **Find** vrátí -1.  
  
 Chcete-li vrátit výsledky hledání, které odpovídají více řádkům, použijte metodu **FindRows.** **FindRows** funguje stejně jako **Find** metoda, s tím rozdílem, že vrátí **DataRowView** pole, které odkazuje na všechny odpovídající řádky v **DataView**. Pokud nejsou nalezeny žádné shody, pole **DataRowView** bude prázdné.  
  
 Chcete-li použít metody **Find** nebo **FindRows,** musíte zadat pořadí řazení buď nastavením **ApplyDefaultSort** na **true,** nebo pomocí vlastnosti **Seřadit.** Pokud není zadáno žádné pořadí řazení, je vyvolána výjimka.  
  
 **Find** a **FindRows** Metody trvat pole hodnot jako vstup, jehož délka odpovídá počtu sloupců v pořadí řazení. V případě řazení na jednom sloupci můžete předat jednu hodnotu. U pořadí řazení obsahujících více sloupců předáte pole objektů. Všimněte si, že pro řazení na více sloupcích musí hodnoty v poli objektů odpovídat pořadí sloupců zadaných ve vlastnosti **Sort** **zobrazení DataView**.  
  
 Následující příklad kódu ukazuje **Find** metoda volána proti **DataView** s pořadí řazení jednoho sloupce.  
  
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
  
 Pokud vaše vlastnost **Sort** určuje více sloupců, musíte předat pole objektů s vyhledávacími hodnotami pro každý sloupec v pořadí určeném vlastností **Seřadit,** jako v následujícím příkladu kódu.  
  
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

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [Zobrazení dat](dataviews.md)
- [Přehled ADO.NET](../ado-net-overview.md)

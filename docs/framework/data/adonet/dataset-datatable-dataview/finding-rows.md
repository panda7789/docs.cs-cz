---
title: Hledání řádků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: ad10557a55b498fe004bff6ce89801e975e7138b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786327"
---
# <a name="finding-rows"></a>Hledání řádků
Můžete vyhledat řádky podle jejich hodnot klíče řazení pomocí <xref:System.Data.DataView.Find%2A> metod <xref:System.Data.DataView>a <xref:System.Data.DataView.FindRows%2A> . Rozlišuje velká a malá písmena vyhledávacích hodnot v metodách **find** a **FindRows** je určena vlastností **CaseSensitive** podkladového <xref:System.Data.DataTable>výrazu. Aby bylo možné vrátit výsledek, musí hodnoty hledání odpovídat existujícím hodnotám klíčového řazení v celém rozsahu.  
  
 Metoda **find** vrátí celé číslo s indexem <xref:System.Data.DataRowView> , který odpovídá kritériím hledání. Pokud kritériím vyhledávání odpovídá více než jeden řádek, vrátí se pouze index prvního odpovídajícího **DataRowViewu** . Nejsou-li nalezeny žádné shody, funkce **find** vrátí hodnotu-1.  
  
 Chcete-li vrátit výsledky hledání, které odpovídají více řádkům, použijte metodu **FindRows** . **FindRows** funguje stejně jako metoda **find** s tím rozdílem, že vrátí pole **DataRowView** , které odkazuje na všechny odpovídající řádky v objektu **DataView**. Pokud se nenajde žádná shoda, pole **DataRowView** bude prázdné.  
  
 Chcete-li použít metody **find** nebo **FindRows** , je nutné zadat pořadí řazení buď nastavením **ApplyDefaultSort** na **hodnotu true** nebo pomocí vlastnosti **Sort** . Pokud není zadáno žádné pořadí řazení, je vyvolána výjimka.  
  
 Metody **find** a **FindRows** přebírají pole hodnot jako vstup, jejichž délka odpovídá počtu sloupců v pořadí řazení. V případě řazení v jednom sloupci můžete předat jednu hodnotu. Pro pořadí řazení obsahující více sloupců předáte pole objektů. Všimněte si, že pro řazení více sloupců musí hodnoty v poli objektu odpovídat pořadí sloupců, které jsou zadány ve vlastnosti **Sort** objektu **DataView**.  
  
 Následující příklad kódu ukazuje metodu **find** , která je volána proti zobrazení **DataView** s jedním sloupcem řazení.  
  
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
  
 Pokud vlastnost **Sort** určuje více sloupců, musíte předat pole objektu s hodnotami hledání pro každý sloupec v pořadí určeném vlastností **Sort** , jak je uvedeno v následujícím příkladu kódu.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [Zobrazení dat](dataviews.md)
- [Přehled ADO.NET](../ado-net-overview.md)

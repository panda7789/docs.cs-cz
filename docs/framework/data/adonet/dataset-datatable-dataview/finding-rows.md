---
title: "Vyhledání řádků"
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
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e9ede2dbf0718a4ca1d8025af3ce60c256afc867
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="finding-rows"></a>Vyhledání řádků
Můžete vyhledat řádků podle jejich hodnot pro klíč řazení s použitím <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>. Rozlišování velkých a malých písmen vyhledávání hodnot v **najít** a **FindRows** je dáno metody **CaseSensitive** vlastnost základní <xref:System.Data.DataTable>. Hledání hodnoty musí odpovídat existující řazení klíčové hodnoty jako celek cílem vrátit výsledek.  
  
 **Najít** metoda vrátí celé číslo s index <xref:System.Data.DataRowView> odpovídající kritériím hledání. Pokud více než jeden řádek odpovídá kritéria hledání, pouze index první odpovídající **DataRowView** je vrácen. Pokud nejsou nalezeny žádné shody, **najít** vrátí hodnotu -1.  
  
 Chcete-li vrátit výsledky hledání, které odpovídají více řádků, použijte **FindRows** metoda. **FindRows** funguje stejně jako **najít** metoda, s výjimkou toho, které se vrátí **DataRowView** pole, která odkazuje na všechny odpovídající řádky v **DataView**. Pokud nejsou nalezeny žádné shody, **DataRowView** pole bude prázdný.  
  
 Použít **najít** nebo **FindRows** metody, je nutné zadat řazení pořadí buď nastavení **ApplyDefaultSort** k **true** nebo pomocí **Řazení** vlastnost. Pokud není zadaný žádný pořadí řazení, je vyvolána výjimka.  
  
 **Najít** a **FindRows** metody přijímají pole hodnot jako vstup, jehož délka odpovídá počtu sloupců v pořadí řazení. V případě řazení na jeden sloupec můžete předat jednu hodnotu. Pro pořadí řazení obsahující více sloupců předáte pole objektů. Všimněte si, že pro řazení do více sloupců, hodnoty v poli objektu musí odpovídat pořadí sloupců zadaných v **řazení** vlastnost **DataView**.  
  
 Následující příklad kódu ukazuje **najít** metoda volána proti **DataView** s jedním sloupcem pořadí řazení.  
  
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
  
 Pokud vaše **řazení** vlastnost určuje více sloupců, je nutné předat pole objektů s hodnotami vyhledávání pro každý sloupec v pořadí zadaném **řazení** vlastnosti, jako v následujícím příkladu kódu.  
  
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
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

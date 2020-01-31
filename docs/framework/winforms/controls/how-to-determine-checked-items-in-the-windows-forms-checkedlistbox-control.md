---
title: Určení zkontrolovaných položek v ovládacím prvku CheckedListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 5854f7e6be759daeb604458ea8554d3c98ed39c2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743249"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Postupy: Určení zaškrtnutých položek v ovládacím prvku Windows Forms CheckedListBox
Při prezentaci dat v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.CheckedListBox> můžete buď iterovat přes kolekci uloženou ve vlastnosti <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>, nebo krokovat seznam pomocí metody <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> k určení, které položky jsou zaškrtnuty. Metoda <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> přebírá jako argument číslo indexu položky a vrátí `true` nebo `false`. Na rozdíl od toho, co byste mohli očekávat, vlastnosti <xref:System.Windows.Forms.ListBox.SelectedItems%2A> a <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> neurčují, které položky jsou zaškrtnuté. určují, které položky jsou zvýrazněny.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>Určení zkontrolovaných položek v ovládacím prvku CheckedListBox  
  
1. Iterujte pomocí kolekce <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>, počínaje hodnotou 0, protože kolekce je založená na nule. Všimněte si, že tato metoda vám poskytne číslo položky v seznamu zkontrolovaných položek, ne na celkový seznam. Takže pokud není první položka v seznamu zaškrtnutá a je zaškrtnuta druhá položka, zobrazí se v následujícím kódu text jako "kontrolovaná položka 1 = MyListItem2".  
  
    ```vb  
    ' Determine if there are any items checked.  
    If CheckedListBox1.CheckedItems.Count <> 0 Then  
       ' If so, loop through all checked items and print results.  
       Dim x As Integer  
       Dim s As String = ""  
       For x = 0 To CheckedListBox1.CheckedItems.Count - 1  
          s = s & "Checked Item " & (x + 1).ToString & " = " & CheckedListBox1.CheckedItems(x).ToString & ControlChars.CrLf  
       Next x  
       MessageBox.Show(s)  
    End If  
    ```  
  
    ```csharp  
    // Determine if there are any items checked.  
    if(checkedListBox1.CheckedItems.Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       string s = "";  
       for(int x = 0; x < checkedListBox1.CheckedItems.Count ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
       MessageBox.Show(s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x < checkedListBox1->CheckedItems->Count; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - nebo –  
  
2. Projděte kolekci <xref:System.Windows.Forms.CheckedListBox.Items%2A>, počínaje hodnotou 0, protože je kolekce založená na nule a zavolejte metodu <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> pro každou položku. Všimněte si, že tato metoda vám poskytne číslo položky v celkovém seznamu, takže pokud není první položka v seznamu zaškrtnuta a je zaškrtnuta druhá položka, zobrazí se něco jako "položka 2 = MyListItem2".  
  
    ```vb  
    Dim i As Integer  
    Dim s As String  
    s = "Checked Items:" & ControlChars.CrLf  
    For i = 0 To (CheckedListBox1.Items.Count - 1)  
       If CheckedListBox1.GetItemChecked(i) = True Then  
          s = s & "Item " & (i + 1).ToString & " = " & CheckedListBox1.Items(i).ToString & ControlChars.CrLf  
       End If  
    Next  
    MessageBox.Show(s)  
    ```  
  
    ```csharp  
    int i;  
    string s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1.Items.Count-1); i++)  
    {  
       if (checkedListBox1.GetItemChecked(i))  
       {  
          s = s + "Item " + (i+1).ToString() + " = " + checkedListBox1.Items[i].ToString() + "\n";  
       }  
    }  
    MessageBox.Show (s);  
    ```  
  
    ```cpp  
    int i;  
    String ^ s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1->Items->Count-1); i++)  
    {  
       if (checkedListBox1->GetItemChecked(i))  
       {  
          s = String::Concat(s, "Item ", (i+1).ToString(), " = ",  
             checkedListBox1->Item[i]->ToString(), "\n");  
       }  
    }  
    MessageBox::Show(s);  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)

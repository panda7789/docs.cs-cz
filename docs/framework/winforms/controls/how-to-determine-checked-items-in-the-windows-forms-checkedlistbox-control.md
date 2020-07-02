---
title: Určení zkontrolovaných položek v ovládacím prvku CheckedListBox
description: Naučte se určit kontrolované položky v model Windows Forms ovládacím prvku CheckedListBox pomocí iterace v kolekci uložené ve vlastnosti CheckedItems.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: fd8845ef83da7406ff4f1468506a23e3f4d386a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618347"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Postupy: Určení zaškrtnutých položek v ovládacím prvku Windows Forms CheckedListBox
Při prezentaci dat v <xref:System.Windows.Forms.CheckedListBox> ovládacím prvku model Windows Forms můžete buď iterovat přes kolekci uloženou ve <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> vlastnosti, nebo krokovat seznam pomocí <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metody k určení, které položky jsou zaškrtnuty. <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>Metoda přijímá číslo indexu položky jako svůj argument a vrátí `true` nebo `false` . Na rozdíl od toho, co byste mohli očekávat, <xref:System.Windows.Forms.ListBox.SelectedItems%2A> <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> vlastnosti a neurčují, které položky jsou zaškrtnuty. určují, které položky jsou zvýrazněny.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>Určení zkontrolovaných položek v ovládacím prvku CheckedListBox  
  
1. Iterujte přes <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> kolekci, počínaje 0, protože kolekce je založená na nule. Všimněte si, že tato metoda vám poskytne číslo položky v seznamu zkontrolovaných položek, ne na celkový seznam. Takže pokud není první položka v seznamu zaškrtnutá a je zaškrtnuta druhá položka, zobrazí se v následujícím kódu text jako "kontrolovaná položka 1 = MyListItem2".  
  
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
  
     - ani  
  
2. Projděte si <xref:System.Windows.Forms.CheckedListBox.Items%2A> kolekci od 0, od 0, protože je kolekce založená na nule a zavolejte <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metodu pro každou položku. Všimněte si, že tato metoda vám poskytne číslo položky v celkovém seznamu, takže pokud není první položka v seznamu zaškrtnuta a je zaškrtnuta druhá položka, zobrazí se něco jako "položka 2 = MyListItem2".  
  
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

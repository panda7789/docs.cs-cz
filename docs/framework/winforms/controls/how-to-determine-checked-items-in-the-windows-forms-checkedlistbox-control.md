---
title: Určení zaškrtnutých položek v ovládacím prvku CheckedListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 5d93a63e9c1c6aae91ecfe83590c59450a565afe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182194"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Postupy: Určení zaškrtnutých položek v ovládacím prvku Windows Forms CheckedListBox
Při prezentaci dat <xref:System.Windows.Forms.CheckedListBox> v ovládacím prvku Windows Forms můžete iterate prostřednictvím kolekce uložené ve <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> vlastnosti nebo krokovat seznam pomocí <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metody k určení, které položky jsou kontrolovány. Metoda <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> přebírá číslo indexu položky jako `true` `false`jeho argument a vrátí nebo . Na rozdíl od toho, <xref:System.Windows.Forms.ListBox.SelectedItems%2A> co <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> byste mohli očekávat, a vlastnosti neurčují, které položky jsou kontrolovány; určují, které položky jsou zvýrazněny.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>Určení zaškrtnutých položek v ovládacím prvku CheckedListBox  
  
1. Iterát prostřednictvím <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> kolekce, počínaje 0, protože kolekce je na základě nuly. Všimněte si, že tato metoda vám číslo položky v seznamu zaškrtnutých položek, nikoli celkový seznam. Pokud tedy není zaškrtnuta první položka v seznamu a druhá položka je zaškrtnuta, zobrazí se v níže uvedeném kódu text jako "Checked Item 1 = MyListItem2".  
  
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
  
     - nebo -  
  
2. Krokovat <xref:System.Windows.Forms.CheckedListBox.Items%2A> kolekce, počínaje 0, protože kolekce je na <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> základě nuly a volání metody pro každou položku. Všimněte si, že tato metoda vám číslo položky v celkovém seznamu, takže pokud první položka v seznamu není zaškrtnuta a druhá položka je zaškrtnuta, zobrazí se něco jako "Položka 2 = MyListItem2".  
  
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
  
## <a name="see-also"></a>Viz také

- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)

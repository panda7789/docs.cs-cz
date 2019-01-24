---
title: 'Postupy: Určení zaškrtnutých položek v ovládacím prvku Windows Forms CheckedListBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: e1f8f7fa1f3f351314ac1d454d591f46654d8f81
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643595"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Postupy: Určení zaškrtnutých položek v ovládacím prvku Windows Forms CheckedListBox
Při zobrazení dat ve Windows Forms <xref:System.Windows.Forms.CheckedListBox> ovládacího prvku, můžete buď iterovat uložených v kolekci <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> vlastnost nebo kroku pomocí seznamu <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metodou ke zjištění, které položky jsou kontrolovány. <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> Metoda přijímá číslo indexu položky jako svůj argument a vrátí `true` nebo `false`. Rozporu s dalo očekávat <xref:System.Windows.Forms.ListBox.SelectedItems%2A> a <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> vlastnosti neurčují položky, které zjišťována; určují, které položky jsou zvýrazněné.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>K určení zaškrtnutých položek v ovládacím prvku CheckedListBox  
  
1.  Iterovat přes <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> kolekce, počínaje 0, protože kolekce je založený na nule. Všimněte si, že tato metoda získáte počet položek v seznamu zaškrtnutých položek není celkový přehled. Takže pokud není zaškrtnuto políčko na první položku v seznamu a je druhá položka zaškrtnuta, následující kód zobrazí text jako "zaškrtnutá položka 1 = MyListItem2".  
  
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
  
2.  Projít <xref:System.Windows.Forms.CheckedListBox.Items%2A> kolekce, protože kolekce je založený na nule, začínajícím hodnotou 0 a volání <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metoda pro každou položku. Všimněte si, že tato metoda získáte počet položek v seznamu celkové, pokud první položku v seznamu není zaškrtnuto a druhá položka je zaškrtnuto, zobrazí něco jako "položka 2 = MyListItem2".  
  
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
- [Ovládací prvky Windows Forms používané k výpisu možností](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)

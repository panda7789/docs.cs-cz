---
title: "Postupy: Určení zaškrtnutých položek v ovládacím prvku Windows Forms CheckedListBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63960740b2fc0cb2c96f9a853480f37857c7901b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Postupy: Určení zaškrtnutých položek v ovládacím prvku Windows Forms CheckedListBox
Při zobrazení dat uložených v systému Windows Forms <xref:System.Windows.Forms.CheckedListBox> ovládací prvek, můžete buď iterovat uložené v kolekci <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> vlastnost, nebo krok prostřednictvím seznamu <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metoda k určení, které položky se kontroluje. <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> Metoda přebírá číslo indexu položky jako její argument a vrátí `true` nebo `false`. Na rozdíl od mohou očekávat <xref:System.Windows.Forms.ListBox.SelectedItems%2A> a <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> vlastnosti není určeno, které položky se kontroluje; určují, které položky se zvýrazněnou.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>K určení zaškrtnutých položek v ovládacím prvku CheckedListBox  
  
1.  Iterace <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> kolekce, začínající na 0, protože kolekce je počítáno od nuly. Všimněte si, že tato metoda vám poskytne počet položek v seznamu zkontrolovat položky, ne celkový seznam. Takže pokud není zaškrtnuta možnost první položky v seznamu a druhá položka je zaškrtnuta, následující kód zobrazí text jako "zaškrtnuté položky 1 = MyListItem2".  
  
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
       for(int x = 0; x <= checkedListBox1.CheckedItems.Count - 1 ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
    MessageBox.Show (s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x <= checkedListBox1->CheckedItems->Count - 1; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - nebo –  
  
2.  Jednotlivé kroky <xref:System.Windows.Forms.CheckedListBox.Items%2A> kolekce začínající na 0, protože kolekce je počítáno od nuly a volání <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metoda pro každou položku. Všimněte si, že tato metoda vám poskytne počet položek v seznamu celkové, pokud první položku v seznamu nastavení není kontrolován a druhá položka je zaškrtnuta možnost zobrazí něco jako "položka 2 = MyListItem2".  
  
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
 [Ovládací prvky Windows Forms používané k výpisu možností](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)

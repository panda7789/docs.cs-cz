---
title: 'Postupy: Přístup ke konkrétním položkám v ovládacím prvku Windows Forms ComboBox, ListBox nebo CheckedListBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ComboBox control [Windows Forms], accessing items
- ListBox control [Windows Forms], returning item information
- list boxes [Windows Forms], accessing items
- ListBox control [Windows Forms], accessing items
- combo boxes [Windows Forms], accessing items
- CheckedListBox control [Windows Forms], accessing items
ms.assetid: 1216742f-bcf9-4ff8-8a62-d7c9053c2b96
ms.openlocfilehash: 731527f2d6adb206fa4d8bc4bc2e488c61b86200
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-specific-items-in-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Postupy: Přístup ke konkrétním položkám v ovládacím prvku Windows Forms ComboBox, ListBox nebo CheckedListBox
Přístup ke konkrétní položky ve Windows Forms – pole se seznamem, seznamu nebo pole se seznamem zaškrtnuté je nezbytné úlohy. Umožňuje programu určit, co je v seznamu, na dané pozici.  
  
### <a name="to-access-a-specific-item"></a>Pro přístup k určité položce  
  
1.  Dotaz `Items` kolekce s použitím indexu konkrétní položky:  
  
    ```vb  
    Private Function GetItemText(i As Integer) As String  
       ' Return the text of the item using the index:  
       Return ComboBox1.Items(i).ToString  
    End Function  
    ```  
  
    ```csharp  
    private string GetItemText(int i)  
    {  
       // Return the text of the item using the index:  
       return (comboBox1.Items[i].ToString());  
    }  
    ```  
  
    ```cpp  
    private:  
       String^ GetItemText(int i)  
       {  
          // Return the text of the item using the index:  
          return (comboBox1->Items->Item[i]->ToString());  
       }  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [Ovládací prvky Windows Forms používané k výpisu možností](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)

---
title: 'Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
ms.openlocfilehash: 881996563acef36a1981ca6236c155b8fc56ef0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013202"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox
Windows Forms <xref:System.Windows.Forms.CheckBox> ovládacího prvku se používá k uživatelům True/False nebo možnosti Ano nebo ne. Ovládací prvek zobrazí zaškrtávací políčko, pokud je vybrána.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Nastavení možností pomocí ovládacích prvků CheckBox  
  
1. Zkoumat hodnoty <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnosti k určení stavu a tuto hodnotu můžete nastavit možnost.  
  
     Ve vzorovém kódu níže, kdy <xref:System.Windows.Forms.CheckBox> ovládacího prvku <xref:System.Windows.Forms.CheckBox.CheckedChanged> událost se vyvolá, formuláře <xref:System.Windows.Forms.Control.AllowDrop%2A> je nastavena na `false` Pokud je zaškrtnuto zaškrtávací políčko. To je užitečné v situacích, ve které chcete omezit interakci s uživatelem.  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.CheckBox>
- [Přehled ovládacího prvku CheckBox](checkbox-control-overview-windows-forms.md)
- [Postupy: Reakce na Windows Forms kliknutí na zaškrtávací políčko](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [Ovládací prvek CheckBox](checkbox-control-windows-forms.md)

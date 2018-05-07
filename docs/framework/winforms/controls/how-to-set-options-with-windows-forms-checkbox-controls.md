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
ms.openlocfilehash: dc9e7b1aea74874c66bf9eb96a5b919ed9b4b73b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox
Windows Forms <xref:System.Windows.Forms.CheckBox> řízení se používá k dát uživatelům True/False nebo možnosti Ano/Ne. Tento ovládací prvek zobrazí zaškrtnutí, pokud je vybrána.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Nastavení možností pomocí ovládacích prvků CheckBox  
  
1.  Zkontrolujte hodnotu <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost, abyste zjistili její stav a použít tuto hodnotu nastavit možnost.  
  
     V ukázce kódu níže, kdy <xref:System.Windows.Forms.CheckBox> ovládacího prvku <xref:System.Windows.Forms.CheckBox.CheckedChanged> událost se vyvolá, formuláře <xref:System.Windows.Forms.Control.AllowDrop%2A> je nastavena na `false` Pokud je zaškrtnuto políčko. To je užitečné v situacích, kde chcete omezit interakci s uživatelem.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.CheckBox>  
 [Přehled ovládacího prvku CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [Ovládací prvek CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)

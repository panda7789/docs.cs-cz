---
title: Nastavení možností pomocí ovládacích prvků CheckBox
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
ms.openlocfilehash: 00b467836d8e60aeee51a010a6384abf7dd73c56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141845"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox
Ovládací prvek <xref:System.Windows.Forms.CheckBox> Windows Forms se používá k poskytnutí možností True/False nebo Yes/No uživatelům. Ovládací prvek zobrazí zaškrtnutí, když je vybrán.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Nastavení možností pomocí ovládacích prvků CheckBox  
  
1. Zkontrolujte hodnotu <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnosti k určení jejího stavu a použijte tuto hodnotu k nastavení možnosti.  
  
     V následující ukázce <xref:System.Windows.Forms.CheckBox> kódu, <xref:System.Windows.Forms.CheckBox.CheckedChanged> když je vyvolána <xref:System.Windows.Forms.Control.AllowDrop%2A> událost ovládacího `false` prvku, vlastnost formuláře je nastavena na pokud je zaškrtnuto políčko. To je užitečné v situacích, kdy chcete omezit interakci s uživatelem.  
  
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

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox – přehled ovládacího prvku](checkbox-control-overview-windows-forms.md)
- [Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [Ovládací prvek ovládacího prvku CheckBox](checkbox-control-windows-forms.md)

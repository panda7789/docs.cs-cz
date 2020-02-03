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
ms.openlocfilehash: 84198eab42aa02b1bb37fa16a3c4247a37f58a10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746763"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox
Model Windows Forms <xref:System.Windows.Forms.CheckBox> ovládací prvek slouží k udělení možností pro uživatele true/false nebo ano/ne. Při výběru ovládacího prvku se zobrazí značka zaškrtnutí.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Nastavení možností pomocí ovládacích prvků CheckBox  
  
1. Zkontrolujte hodnotu vlastnosti <xref:System.Windows.Forms.CheckBox.Checked%2A> a určete její stav a pomocí této hodnoty nastavte možnost.  
  
     V níže uvedeném příkladu kódu je při vyvolání události <xref:System.Windows.Forms.CheckBox.CheckedChanged> ovládacího prvku <xref:System.Windows.Forms.CheckBox> nastavena vlastnost <xref:System.Windows.Forms.Control.AllowDrop%2A> formuláře na `false`, pokud je zaškrtnuté políčko. To je užitečné v situacích, kdy chcete omezit interakci s uživatelem.  
  
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
- [Přehled ovládacího prvku CheckBox](checkbox-control-overview-windows-forms.md)
- [Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [Ovládací prvek CheckBox](checkbox-control-windows-forms.md)

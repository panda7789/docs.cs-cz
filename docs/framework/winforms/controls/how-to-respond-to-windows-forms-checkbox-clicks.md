---
title: Reakce na kliknutí na ovládací prvek CheckBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Click event [Windows Forms], CheckBox control
- CheckBox control [Windows Forms], Click events
- events [Windows Forms], Click events
- double-clicks
- check boxes [Windows Forms], responding to events
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
ms.openlocfilehash: ba2afb52939a6274978ce725dac19b5622419b99
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735664"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox
Vždy, když uživatel klikne na ovládací prvek model Windows Forms <xref:System.Windows.Forms.CheckBox>, dojde k události <xref:System.Windows.Forms.Control.Click>. Aplikaci můžete programovat k provedení určité akce v závislosti na stavu zaškrtávacího políčka.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Reakce na kliknutí na zaškrtávací políčko  
  
1. V obslužné rutině události <xref:System.Windows.Forms.Control.Click> pomocí vlastnosti <xref:System.Windows.Forms.CheckBox.Checked%2A> určete stav ovládacího prvku a proveďte potřebné akce.  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the   
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the   
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    > Pokud se uživatel pokusí dvakrát kliknout na ovládací prvek <xref:System.Windows.Forms.CheckBox>, každé kliknutí se zpracuje samostatně; To znamená, <xref:System.Windows.Forms.CheckBox> ovládací prvek nepodporuje událost dvojitého kliknutí.  
  
    > [!NOTE]
    > Je-li vlastnost <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> `true` (výchozí), <xref:System.Windows.Forms.CheckBox> při kliknutí na ni automaticky vybere nebo zruší zaškrtnutí. V opačném případě je nutné ručně nastavit vlastnost <xref:System.Windows.Forms.CheckBox.Checked%2A>, když dojde k události <xref:System.Windows.Forms.Control.Click>.  
  
     Můžete také použít ovládací prvek <xref:System.Windows.Forms.CheckBox> k určení postupu.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Určení postupu při kliknutí na zaškrtávací políčko  
  
1. Použijte příkaz Case pro dotaz na hodnotu vlastnosti <xref:System.Windows.Forms.CheckBox.CheckState%2A>, abyste zjistili, jaký je průběh akce. Je-li vlastnost <xref:System.Windows.Forms.CheckBox.ThreeState%2A> nastavena na hodnotu `true`, může vlastnost <xref:System.Windows.Forms.CheckBox.CheckState%2A> vracet tři možné hodnoty, které reprezentují políčko zaškrtnuto, políčko není zaškrtnuto nebo třetí neurčitý stav, v němž je pole zobrazeno s ztlumeným vzhledem k označení možnosti není k dispozici.  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select   
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    > Pokud je vlastnost <xref:System.Windows.Forms.CheckBox.ThreeState%2A> nastavena na hodnotu `true`, vrátí <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost `true` pro <xref:System.Windows.Forms.CheckState.Checked> i <xref:System.Windows.Forms.CheckState.Indeterminate>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.CheckBox>
- [Přehled ovládacího prvku CheckBox](checkbox-control-overview-windows-forms.md)
- [Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Ovládací prvek CheckBox](checkbox-control-windows-forms.md)

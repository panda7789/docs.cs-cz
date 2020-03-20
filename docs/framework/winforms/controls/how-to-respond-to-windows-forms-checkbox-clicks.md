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
ms.openlocfilehash: 6ff20c443519446d3804b325924cb3c5cbedea97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141923"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox
Kdykoli uživatel klepne na <xref:System.Windows.Forms.CheckBox> ovládací <xref:System.Windows.Forms.Control.Click> prvek Windows Forms, dojde k události. Aplikaci můžete naprogramovat tak, aby provedla určitou akci v závislosti na stavu zaškrtávacího políčka.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Chcete-li reagovat na kliknutí Na checkbox  
  
1. V <xref:System.Windows.Forms.Control.Click> obslužné <xref:System.Windows.Forms.CheckBox.Checked%2A> rutině události použijte vlastnost k určení stavu ovládacího prvku a proveďte všechny nezbytné akce.  
  
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
    > Pokud se uživatel pokusí poklepat na <xref:System.Windows.Forms.CheckBox> ovládací prvek, každé kliknutí bude zpracováno samostatně. to znamená, <xref:System.Windows.Forms.CheckBox> že ovládací prvek nepodporuje událost poklepání.  
  
    > [!NOTE]
    > Když <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> je `true` vlastnost (výchozí), <xref:System.Windows.Forms.CheckBox> je automaticky vybrána nebo vymazána po klepnutí. V opačném případě je <xref:System.Windows.Forms.CheckBox.Checked%2A> nutné ručně <xref:System.Windows.Forms.Control.Click> nastavit vlastnost, když dojde k události.  
  
     Ovládací <xref:System.Windows.Forms.CheckBox> prvek můžete také použít k určení průběhu akce.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Určení postupu po klepnutí na zaškrtávací políčko  
  
1. Pomocí příkazu case můžete zadat <xref:System.Windows.Forms.CheckBox.CheckState%2A> dotaz na hodnotu vlastnosti k určení postupu. Pokud <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je vlastnost `true`nastavena <xref:System.Windows.Forms.CheckBox.CheckState%2A> na , může vlastnost vrátit tři možné hodnoty, které představují zaškrtnuté políčko, nezaškrtnuté políčko nebo třetí neurčitý stav, ve kterém je pole zobrazeno se ztlumeným vzhledem, což znamená, že možnost není k dispozici.  
  
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
    > Pokud <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je vlastnost `true`nastavena <xref:System.Windows.Forms.CheckBox.Checked%2A> na `true` , <xref:System.Windows.Forms.CheckState.Checked> <xref:System.Windows.Forms.CheckState.Indeterminate>vlastnost vrátí pro obě a .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox – přehled ovládacího prvku](checkbox-control-overview-windows-forms.md)
- [Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Ovládací prvek ovládacího prvku CheckBox](checkbox-control-windows-forms.md)

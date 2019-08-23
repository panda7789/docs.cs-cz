---
title: 'Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox'
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
ms.openlocfilehash: 7ff6b2aad9ef0775547af57f11af28839e69637c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914983"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox
<xref:System.Windows.Forms.CheckBox> Pokaždé<xref:System.Windows.Forms.Control.Click> , když uživatel klikne na ovládací prvek model Windows Forms, dojde k události. Aplikaci můžete programovat k provedení určité akce v závislosti na stavu zaškrtávacího políčka.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Reakce na kliknutí na zaškrtávací políčko  
  
1. V obslužné rutině <xref:System.Windows.Forms.CheckBox.Checked%2A>událostipoužijte vlastnost k určení stavu ovládacího prvku a proveďte potřebné akce. <xref:System.Windows.Forms.Control.Click>  
  
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
    > Pokud se uživatel pokusí dvakrát kliknout <xref:System.Windows.Forms.CheckBox> na ovládací prvek, každé kliknutí bude zpracováno samostatně; to znamená <xref:System.Windows.Forms.CheckBox> , že ovládací prvek nepodporuje událost dvojitého kliknutí.  
  
    > [!NOTE]
    > Pokud je <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> `true` vlastnost (výchozí), při kliknutí se <xref:System.Windows.Forms.CheckBox> automaticky vybere nebo zruší její zaškrtnutí. V opačném případě je nutné ručně <xref:System.Windows.Forms.CheckBox.Checked%2A> nastavit vlastnost, <xref:System.Windows.Forms.Control.Click> Jakmile dojde k události.  
  
     Můžete také použít <xref:System.Windows.Forms.CheckBox> ovládací prvek k určení postupu.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Určení postupu při kliknutí na zaškrtávací políčko  
  
1. Použijte příkaz Case pro dotaz na hodnotu <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnosti pro určení postupu. Pokud je `true`vlastnost nastavena na, <xref:System.Windows.Forms.CheckBox.CheckState%2A> může vlastnost vracet tři možné hodnoty, které reprezentují políčko zaškrtnuto, políčko není zaškrtnuto nebo třetí neurčitý stav, ve kterém se pole zobrazuje s neaktivním. <xref:System.Windows.Forms.CheckBox.ThreeState%2A> vzhled označující, že možnost není k dispozici  
  
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
    > `true` <xref:System.Windows.Forms.CheckBox.Checked%2A> `true`Pokud je vlastnost nastavena na, vrátí vlastnost pro i <xref:System.Windows.Forms.CheckState.Checked>. <xref:System.Windows.Forms.CheckState.Indeterminate> <xref:System.Windows.Forms.CheckBox.ThreeState%2A>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.CheckBox>
- [Přehled ovládacího prvku CheckBox](checkbox-control-overview-windows-forms.md)
- [Postupy: Nastavení možností pomocí model Windows Forms ovládacích prvků CheckBox](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Ovládací prvek CheckBox](checkbox-control-windows-forms.md)

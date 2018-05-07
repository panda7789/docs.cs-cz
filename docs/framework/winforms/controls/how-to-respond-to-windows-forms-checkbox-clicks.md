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
ms.openlocfilehash: aa8a15d4f55fb1dd47fdf004fa05091ec88fe03e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox
Vždy, když uživatel klikne na tlačítko Windows Forms <xref:System.Windows.Forms.CheckBox> ovládací prvek, <xref:System.Windows.Forms.Control.Click> dojde k události. Můžete naprogramovat aplikace provádět některé akce v závislosti na stavu zaškrtávacího políčka.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Reakce na kliknutí na zaškrtávací políčko  
  
1.  V <xref:System.Windows.Forms.Control.Click> obslužné rutiny události, použijte <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnosti k určení stavu ovládacího prvku a provádět veškeré potřebné akce.  
  
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
    >  Pokud se uživatel pokusí dvakrát klikněte <xref:System.Windows.Forms.CheckBox> ovládací prvek, každý klikněte na tlačítko se zpracovávají odděleně; který je, <xref:System.Windows.Forms.CheckBox> ovládací prvek nepodporuje událost poklikejte na soubor.  
  
    > [!NOTE]
    >  Když <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> vlastnost je `true` (výchozí), <xref:System.Windows.Forms.CheckBox> je automaticky vybrána nebo vymazána po klepnutí. Jinak, musíte ručně nastavit <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost při <xref:System.Windows.Forms.Control.Click> dojde k události.  
  
     Můžete také <xref:System.Windows.Forms.CheckBox> ovládacího prvku, opatření, která.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>K určení postupu akce při zaškrtávací políčko Po kliknutí na  
  
1.  Použijte příkaz case dotazovat hodnotu <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnosti k určení opatření, která. Když <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je nastavena na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnost může vracet třemi možnými hodnotami, které představují se zaškrtnutým políčkem, políčko nezaškrtnuté vrácení nebo jiného neurčitého stavu ve kterém se zobrazí pole s neaktivní vzhled, který indikuje možnost není k dispozici.  
  
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
    >  Když <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je nastavena na `true`, <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost vrátí `true` pro obě <xref:System.Windows.Forms.CheckState.Checked> a <xref:System.Windows.Forms.CheckState.Indeterminate>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.CheckBox>  
 [Přehled ovládacího prvku CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [Ovládací prvek CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)

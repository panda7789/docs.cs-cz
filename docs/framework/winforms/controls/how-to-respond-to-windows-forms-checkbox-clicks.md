---
title: 'Postupy: Reakce na Windows Forms kliknutí na zaškrtávací políčko'
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
ms.openlocfilehash: cf9a7c51c0054c34dbce40f3a2dfa68c62f3a4e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726322"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Postupy: Reakce na Windows Forms kliknutí na zaškrtávací políčko
Vždy, když uživatel klepne na tlačítko Windows Forms <xref:System.Windows.Forms.CheckBox> ovládací prvek, <xref:System.Windows.Forms.Control.Click> dojde k události. Můžete naprogramovat aplikace provádět některé akce v závislosti na stavu zaškrtávacího políčka.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Reakce na kliknutí na zaškrtávací políčko  
  
1.  V <xref:System.Windows.Forms.Control.Click> obslužná rutina události, použijte <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnosti k určení stavu ovládacího prvku a proveďte všechny potřebné akce.  
  
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
    >  Pokud se uživatel pokusí dvakrát klikněte na <xref:System.Windows.Forms.CheckBox> ovládacího prvku, každý klikněte na tlačítko se zpracovávají odděleně; to znamená, <xref:System.Windows.Forms.CheckBox> ovládací prvek nepodporuje dvakrát klikněte na událost.  
  
    > [!NOTE]
    >  Když <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> vlastnost `true` (výchozí), <xref:System.Windows.Forms.CheckBox> automaticky zaškrtnuto nebo Ne, když dojde ke kliknutí na. V opačném případě je nutné ručně nastavit <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost při <xref:System.Windows.Forms.Control.Click> dojde k události.  
  
     Můžete také použít <xref:System.Windows.Forms.CheckBox> ovládacího prvku k určení postupu.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>K určení postupu při zaškrtávací políčko dojde ke kliknutí na  
  
1.  Použití příkazu case k dotazování hodnotu <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnosti k určení postupu. Když <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je nastavena na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnosti může vrátit tří možných hodnot, které představují se zaškrtnutým políčkem, pole vrácení není zaškrtnuto nebo třetí neurčitého stavu bude zobrazeno s neaktivní vzhled, který indikuje možnost není k dispozici.  
  
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
    >  Když <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je nastavena na `true`, <xref:System.Windows.Forms.CheckBox.Checked%2A> vrátí vlastnost `true` pro obě <xref:System.Windows.Forms.CheckState.Checked> a <xref:System.Windows.Forms.CheckState.Indeterminate>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.CheckBox>
- [Přehled ovládacího prvku CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)
- [Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Ovládací prvek CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)

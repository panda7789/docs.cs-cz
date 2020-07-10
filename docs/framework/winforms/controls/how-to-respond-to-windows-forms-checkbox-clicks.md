---
title: Reakce na kliknutí na ovládací prvek CheckBox
description: Naučte se programovat aplikaci model Windows Forms k provedení určité akce v závislosti na stavu zaškrtávacího políčka.
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
ms.openlocfilehash: 58944bc421f990343b6c58484aaab3d79c8bda5e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174494"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox
Pokaždé, když uživatel klikne na <xref:System.Windows.Forms.CheckBox> ovládací prvek model Windows Forms, <xref:System.Windows.Forms.Control.Click> dojde k události. Aplikaci můžete programovat k provedení určité akce v závislosti na stavu zaškrtávacího políčka.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Reakce na kliknutí na zaškrtávací políčko  
  
1. V <xref:System.Windows.Forms.Control.Click> obslužné rutině události použijte <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost k určení stavu ovládacího prvku a proveďte potřebné akce.  
  
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
    > Pokud se uživatel pokusí dvakrát kliknout na <xref:System.Windows.Forms.CheckBox> ovládací prvek, každé kliknutí bude zpracováno samostatně; to znamená, že <xref:System.Windows.Forms.CheckBox> ovládací prvek nepodporuje událost dvojitého kliknutí.  
  
    > [!NOTE]
    > Pokud <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> je vlastnost `true` (výchozí), při kliknutí se <xref:System.Windows.Forms.CheckBox> automaticky vybere nebo zruší její zaškrtnutí. V opačném případě je nutné ručně nastavit <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost, jakmile <xref:System.Windows.Forms.Control.Click> dojde k události.  
  
     Můžete také použít <xref:System.Windows.Forms.CheckBox> ovládací prvek k určení postupu.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Určení postupu při kliknutí na zaškrtávací políčko  
  
1. Použijte příkaz Case pro dotaz na hodnotu <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnosti pro určení postupu. Pokud <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je vlastnost nastavena na hodnotu `true` , <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnost může vracet tři možné hodnoty, které reprezentují políčko zaškrtnuto, políčko není zaškrtnuto nebo třetí neurčitý stav, v němž je pole zobrazeno s ztlumeným vzhledem k označení možnosti není k dispozici.  
  
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
    > Pokud <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je vlastnost nastavena na `true` , <xref:System.Windows.Forms.CheckBox.Checked%2A> vrátí vlastnost `true` pro i <xref:System.Windows.Forms.CheckState.Checked> <xref:System.Windows.Forms.CheckState.Indeterminate> .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox – přehled ovládacího prvku](checkbox-control-overview-windows-forms.md)
- [Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Ovládací prvek CheckBox](checkbox-control-windows-forms.md)

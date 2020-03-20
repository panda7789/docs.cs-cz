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
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="9e4f2-102">Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="9e4f2-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="9e4f2-103">Kdykoli uživatel klepne na <xref:System.Windows.Forms.CheckBox> ovládací <xref:System.Windows.Forms.Control.Click> prvek Windows Forms, dojde k události.</span><span class="sxs-lookup"><span data-stu-id="9e4f2-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="9e4f2-104">Aplikaci můžete naprogramovat tak, aby provedla určitou akci v závislosti na stavu zaškrtávacího políčka.</span><span class="sxs-lookup"><span data-stu-id="9e4f2-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="9e4f2-105">Chcete-li reagovat na kliknutí Na checkbox</span><span class="sxs-lookup"><span data-stu-id="9e4f2-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="9e4f2-106">V <xref:System.Windows.Forms.Control.Click> obslužné <xref:System.Windows.Forms.CheckBox.Checked%2A> rutině události použijte vlastnost k určení stavu ovládacího prvku a proveďte všechny nezbytné akce.</span><span class="sxs-lookup"><span data-stu-id="9e4f2-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="9e4f2-107">Pokud se uživatel pokusí poklepat na <xref:System.Windows.Forms.CheckBox> ovládací prvek, každé kliknutí bude zpracováno samostatně. to znamená, <xref:System.Windows.Forms.CheckBox> že ovládací prvek nepodporuje událost poklepání.</span><span class="sxs-lookup"><span data-stu-id="9e4f2-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9e4f2-108">Když <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> je `true` vlastnost (výchozí), <xref:System.Windows.Forms.CheckBox> je automaticky vybrána nebo vymazána po klepnutí.</span><span class="sxs-lookup"><span data-stu-id="9e4f2-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="9e4f2-109">V opačném případě je <xref:System.Windows.Forms.CheckBox.Checked%2A> nutné ručně <xref:System.Windows.Forms.Control.Click> nastavit vlastnost, když dojde k události.</span><span class="sxs-lookup"><span data-stu-id="9e4f2-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="9e4f2-110">Ovládací <xref:System.Windows.Forms.CheckBox> prvek můžete také použít k určení průběhu akce.</span><span class="sxs-lookup"><span data-stu-id="9e4f2-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="9e4f2-111">Určení postupu po klepnutí na zaškrtávací políčko</span><span class="sxs-lookup"><span data-stu-id="9e4f2-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="9e4f2-112">Pomocí příkazu case můžete zadat <xref:System.Windows.Forms.CheckBox.CheckState%2A> dotaz na hodnotu vlastnosti k určení postupu.</span><span class="sxs-lookup"><span data-stu-id="9e4f2-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="9e4f2-113">Pokud <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je vlastnost `true`nastavena <xref:System.Windows.Forms.CheckBox.CheckState%2A> na , může vlastnost vrátit tři možné hodnoty, které představují zaškrtnuté políčko, nezaškrtnuté políčko nebo třetí neurčitý stav, ve kterém je pole zobrazeno se ztlumeným vzhledem, což znamená, že možnost není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9e4f2-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="9e4f2-114">Pokud <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je vlastnost `true`nastavena <xref:System.Windows.Forms.CheckBox.Checked%2A> na `true` , <xref:System.Windows.Forms.CheckState.Checked> <xref:System.Windows.Forms.CheckState.Indeterminate>vlastnost vrátí pro obě a .</span><span class="sxs-lookup"><span data-stu-id="9e4f2-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4f2-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e4f2-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="9e4f2-116">CheckBox – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="9e4f2-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="9e4f2-117">Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="9e4f2-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="9e4f2-118">Ovládací prvek ovládacího prvku CheckBox</span><span class="sxs-lookup"><span data-stu-id="9e4f2-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)

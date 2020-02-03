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
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="79867-102">Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="79867-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="79867-103">Vždy, když uživatel klikne na ovládací prvek model Windows Forms <xref:System.Windows.Forms.CheckBox>, dojde k události <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="79867-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="79867-104">Aplikaci můžete programovat k provedení určité akce v závislosti na stavu zaškrtávacího políčka.</span><span class="sxs-lookup"><span data-stu-id="79867-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="79867-105">Reakce na kliknutí na zaškrtávací políčko</span><span class="sxs-lookup"><span data-stu-id="79867-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="79867-106">V obslužné rutině události <xref:System.Windows.Forms.Control.Click> pomocí vlastnosti <xref:System.Windows.Forms.CheckBox.Checked%2A> určete stav ovládacího prvku a proveďte potřebné akce.</span><span class="sxs-lookup"><span data-stu-id="79867-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="79867-107">Pokud se uživatel pokusí dvakrát kliknout na ovládací prvek <xref:System.Windows.Forms.CheckBox>, každé kliknutí se zpracuje samostatně; To znamená, <xref:System.Windows.Forms.CheckBox> ovládací prvek nepodporuje událost dvojitého kliknutí.</span><span class="sxs-lookup"><span data-stu-id="79867-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="79867-108">Je-li vlastnost <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> `true` (výchozí), <xref:System.Windows.Forms.CheckBox> při kliknutí na ni automaticky vybere nebo zruší zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="79867-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="79867-109">V opačném případě je nutné ručně nastavit vlastnost <xref:System.Windows.Forms.CheckBox.Checked%2A>, když dojde k události <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="79867-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="79867-110">Můžete také použít ovládací prvek <xref:System.Windows.Forms.CheckBox> k určení postupu.</span><span class="sxs-lookup"><span data-stu-id="79867-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="79867-111">Určení postupu při kliknutí na zaškrtávací políčko</span><span class="sxs-lookup"><span data-stu-id="79867-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="79867-112">Použijte příkaz Case pro dotaz na hodnotu vlastnosti <xref:System.Windows.Forms.CheckBox.CheckState%2A>, abyste zjistili, jaký je průběh akce.</span><span class="sxs-lookup"><span data-stu-id="79867-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="79867-113">Je-li vlastnost <xref:System.Windows.Forms.CheckBox.ThreeState%2A> nastavena na hodnotu `true`, může vlastnost <xref:System.Windows.Forms.CheckBox.CheckState%2A> vracet tři možné hodnoty, které reprezentují políčko zaškrtnuto, políčko není zaškrtnuto nebo třetí neurčitý stav, v němž je pole zobrazeno s ztlumeným vzhledem k označení možnosti není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="79867-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="79867-114">Pokud je vlastnost <xref:System.Windows.Forms.CheckBox.ThreeState%2A> nastavena na hodnotu `true`, vrátí <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost `true` pro <xref:System.Windows.Forms.CheckState.Checked> i <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="79867-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79867-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="79867-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="79867-116">Přehled ovládacího prvku CheckBox</span><span class="sxs-lookup"><span data-stu-id="79867-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="79867-117">Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="79867-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="79867-118">Ovládací prvek CheckBox</span><span class="sxs-lookup"><span data-stu-id="79867-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)

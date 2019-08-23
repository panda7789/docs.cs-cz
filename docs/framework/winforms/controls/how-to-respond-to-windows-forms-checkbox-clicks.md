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
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="8d0c8-102">Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="8d0c8-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="8d0c8-103"><xref:System.Windows.Forms.CheckBox> Pokaždé<xref:System.Windows.Forms.Control.Click> , když uživatel klikne na ovládací prvek model Windows Forms, dojde k události.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="8d0c8-104">Aplikaci můžete programovat k provedení určité akce v závislosti na stavu zaškrtávacího políčka.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="8d0c8-105">Reakce na kliknutí na zaškrtávací políčko</span><span class="sxs-lookup"><span data-stu-id="8d0c8-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="8d0c8-106">V obslužné rutině <xref:System.Windows.Forms.CheckBox.Checked%2A>událostipoužijte vlastnost k určení stavu ovládacího prvku a proveďte potřebné akce. <xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="8d0c8-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="8d0c8-107">Pokud se uživatel pokusí dvakrát kliknout <xref:System.Windows.Forms.CheckBox> na ovládací prvek, každé kliknutí bude zpracováno samostatně; to znamená <xref:System.Windows.Forms.CheckBox> , že ovládací prvek nepodporuje událost dvojitého kliknutí.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8d0c8-108">Pokud je <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> `true` vlastnost (výchozí), při kliknutí se <xref:System.Windows.Forms.CheckBox> automaticky vybere nebo zruší její zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="8d0c8-109">V opačném případě je nutné ručně <xref:System.Windows.Forms.CheckBox.Checked%2A> nastavit vlastnost, <xref:System.Windows.Forms.Control.Click> Jakmile dojde k události.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="8d0c8-110">Můžete také použít <xref:System.Windows.Forms.CheckBox> ovládací prvek k určení postupu.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="8d0c8-111">Určení postupu při kliknutí na zaškrtávací políčko</span><span class="sxs-lookup"><span data-stu-id="8d0c8-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="8d0c8-112">Použijte příkaz Case pro dotaz na hodnotu <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnosti pro určení postupu.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="8d0c8-113">Pokud je `true`vlastnost nastavena na, <xref:System.Windows.Forms.CheckBox.CheckState%2A> může vlastnost vracet tři možné hodnoty, které reprezentují políčko zaškrtnuto, políčko není zaškrtnuto nebo třetí neurčitý stav, ve kterém se pole zobrazuje s neaktivním. <xref:System.Windows.Forms.CheckBox.ThreeState%2A> vzhled označující, že možnost není k dispozici</span><span class="sxs-lookup"><span data-stu-id="8d0c8-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="8d0c8-114">`true` <xref:System.Windows.Forms.CheckBox.Checked%2A> `true`Pokud je vlastnost nastavena na, vrátí vlastnost pro i <xref:System.Windows.Forms.CheckState.Checked>. <xref:System.Windows.Forms.CheckState.Indeterminate> <xref:System.Windows.Forms.CheckBox.ThreeState%2A></span><span class="sxs-lookup"><span data-stu-id="8d0c8-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d0c8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d0c8-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="8d0c8-116">Přehled ovládacího prvku CheckBox</span><span class="sxs-lookup"><span data-stu-id="8d0c8-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="8d0c8-117">Postupy: Nastavení možností pomocí model Windows Forms ovládacích prvků CheckBox</span><span class="sxs-lookup"><span data-stu-id="8d0c8-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="8d0c8-118">Ovládací prvek CheckBox</span><span class="sxs-lookup"><span data-stu-id="8d0c8-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)

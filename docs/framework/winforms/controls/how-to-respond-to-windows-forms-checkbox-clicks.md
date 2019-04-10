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
ms.openlocfilehash: 77f93dae2a91f282c6746c3fec3fb5f567cae2e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211982"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="bb63a-102">Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="bb63a-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="bb63a-103">Vždy, když uživatel klepne na tlačítko Windows Forms <xref:System.Windows.Forms.CheckBox> ovládací prvek, <xref:System.Windows.Forms.Control.Click> dojde k události.</span><span class="sxs-lookup"><span data-stu-id="bb63a-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="bb63a-104">Můžete naprogramovat aplikace provádět některé akce v závislosti na stavu zaškrtávacího políčka.</span><span class="sxs-lookup"><span data-stu-id="bb63a-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="bb63a-105">Reakce na kliknutí na zaškrtávací políčko</span><span class="sxs-lookup"><span data-stu-id="bb63a-105">To respond to CheckBox clicks</span></span>  
  
1.  <span data-ttu-id="bb63a-106">V <xref:System.Windows.Forms.Control.Click> obslužná rutina události, použijte <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnosti k určení stavu ovládacího prvku a proveďte všechny potřebné akce.</span><span class="sxs-lookup"><span data-stu-id="bb63a-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    >  <span data-ttu-id="bb63a-107">Pokud se uživatel pokusí dvakrát klikněte na <xref:System.Windows.Forms.CheckBox> ovládacího prvku, každý klikněte na tlačítko se zpracovávají odděleně; to znamená, <xref:System.Windows.Forms.CheckBox> ovládací prvek nepodporuje dvakrát klikněte na událost.</span><span class="sxs-lookup"><span data-stu-id="bb63a-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb63a-108">Když <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> vlastnost `true` (výchozí), <xref:System.Windows.Forms.CheckBox> automaticky zaškrtnuto nebo Ne, když dojde ke kliknutí na.</span><span class="sxs-lookup"><span data-stu-id="bb63a-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="bb63a-109">V opačném případě je nutné ručně nastavit <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost při <xref:System.Windows.Forms.Control.Click> dojde k události.</span><span class="sxs-lookup"><span data-stu-id="bb63a-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="bb63a-110">Můžete také použít <xref:System.Windows.Forms.CheckBox> ovládacího prvku k určení postupu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="bb63a-111">K určení postupu při zaškrtávací políčko dojde ke kliknutí na</span><span class="sxs-lookup"><span data-stu-id="bb63a-111">To determine a course of action when a check box is clicked</span></span>  
  
1.  <span data-ttu-id="bb63a-112">Použití příkazu case k dotazování hodnotu <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnosti k určení postupu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="bb63a-113">Když <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je nastavena na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnosti může vrátit tří možných hodnot, které představují se zaškrtnutým políčkem, pole vrácení není zaškrtnuto nebo třetí neurčitého stavu bude zobrazeno s neaktivní vzhled, který indikuje možnost není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="bb63a-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    >  <span data-ttu-id="bb63a-114">Když <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je nastavena na `true`, <xref:System.Windows.Forms.CheckBox.Checked%2A> vrátí vlastnost `true` pro obě <xref:System.Windows.Forms.CheckState.Checked> a <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="bb63a-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb63a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb63a-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="bb63a-116">Přehled ovládacího prvku CheckBox</span><span class="sxs-lookup"><span data-stu-id="bb63a-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="bb63a-117">Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="bb63a-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="bb63a-118">Ovládací prvek CheckBox</span><span class="sxs-lookup"><span data-stu-id="bb63a-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)

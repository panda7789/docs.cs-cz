---
title: "Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f15adb84f92c9434d6835e80f08bf1d9bd500ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="1fff7-102">Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="1fff7-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="1fff7-103">Vždy, když uživatel klikne na tlačítko Windows Forms <xref:System.Windows.Forms.CheckBox> ovládací prvek, <xref:System.Windows.Forms.Control.Click> dojde k události.</span><span class="sxs-lookup"><span data-stu-id="1fff7-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="1fff7-104">Můžete naprogramovat aplikace provádět některé akce v závislosti na stavu zaškrtávacího políčka.</span><span class="sxs-lookup"><span data-stu-id="1fff7-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="1fff7-105">Reakce na kliknutí na zaškrtávací políčko</span><span class="sxs-lookup"><span data-stu-id="1fff7-105">To respond to CheckBox clicks</span></span>  
  
1.  <span data-ttu-id="1fff7-106">V <xref:System.Windows.Forms.Control.Click> obslužné rutiny události, použijte <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnosti k určení stavu ovládacího prvku a provádět veškeré potřebné akce.</span><span class="sxs-lookup"><span data-stu-id="1fff7-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    >  <span data-ttu-id="1fff7-107">Pokud se uživatel pokusí dvakrát klikněte <xref:System.Windows.Forms.CheckBox> ovládací prvek, každý klikněte na tlačítko se zpracovávají odděleně; který je, <xref:System.Windows.Forms.CheckBox> ovládací prvek nepodporuje událost poklikejte na soubor.</span><span class="sxs-lookup"><span data-stu-id="1fff7-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1fff7-108">Když <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> vlastnost je `true` (výchozí), <xref:System.Windows.Forms.CheckBox> je automaticky vybrána nebo vymazána po klepnutí.</span><span class="sxs-lookup"><span data-stu-id="1fff7-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="1fff7-109">Jinak, musíte ručně nastavit <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost při <xref:System.Windows.Forms.Control.Click> dojde k události.</span><span class="sxs-lookup"><span data-stu-id="1fff7-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="1fff7-110">Můžete také <xref:System.Windows.Forms.CheckBox> ovládacího prvku, opatření, která.</span><span class="sxs-lookup"><span data-stu-id="1fff7-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="1fff7-111">K určení postupu akce při zaškrtávací políčko Po kliknutí na</span><span class="sxs-lookup"><span data-stu-id="1fff7-111">To determine a course of action when a check box is clicked</span></span>  
  
1.  <span data-ttu-id="1fff7-112">Použijte příkaz case dotazovat hodnotu <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnosti k určení opatření, která.</span><span class="sxs-lookup"><span data-stu-id="1fff7-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="1fff7-113">Když <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je nastavena na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnost může vracet třemi možnými hodnotami, které představují se zaškrtnutým políčkem, políčko nezaškrtnuté vrácení nebo jiného neurčitého stavu ve kterém se zobrazí pole s neaktivní vzhled, který indikuje možnost není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1fff7-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    >  <span data-ttu-id="1fff7-114">Když <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je nastavena na `true`, <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost vrátí `true` pro obě <xref:System.Windows.Forms.CheckState.Checked> a <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="1fff7-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fff7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fff7-115">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="1fff7-116">Přehled ovládacího prvku CheckBox</span><span class="sxs-lookup"><span data-stu-id="1fff7-116">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="1fff7-117">Postupy: nastavení možností pomocí Windows Forms ovládacích prvků CheckBox</span><span class="sxs-lookup"><span data-stu-id="1fff7-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [<span data-ttu-id="1fff7-118">CheckBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1fff7-118">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)

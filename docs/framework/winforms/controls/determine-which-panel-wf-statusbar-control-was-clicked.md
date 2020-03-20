---
title: Určení panelu v ovládacím prvku Stavový panel bylo kliknuto
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
ms.openlocfilehash: eb3b10d515ba5b62236594e063ca7f060b34b73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182367"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="b38ec-102">Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="b38ec-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
> <span data-ttu-id="b38ec-103">Ovládací <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> prvky a nahradit a <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> přidat funkce a ovládací prvky; ovládací <xref:System.Windows.Forms.StatusBar> prvky <xref:System.Windows.Forms.StatusBarPanel> a jsou však zachovány pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="b38ec-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="b38ec-104">Chcete-li naprogramovat ovládací prvek [Stavový panel](statusbar-control-windows-forms.md) tak, <xref:System.Windows.Forms.StatusBar.PanelClick> aby reagoval na kliknutí uživatele, použijte příkaz case v rámci události.</span><span class="sxs-lookup"><span data-stu-id="b38ec-104">To program the [StatusBar Control](statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="b38ec-105">Událost obsahuje argument (argument panelu), který obsahuje odkaz <xref:System.Windows.Forms.StatusBarPanel>na klepnutí .</span><span class="sxs-lookup"><span data-stu-id="b38ec-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="b38ec-106">Pomocí tohoto odkazu můžete určit index panelu, na který jste klepnuli, a odpovídajícím způsobem programovat.</span><span class="sxs-lookup"><span data-stu-id="b38ec-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b38ec-107">Ujistěte <xref:System.Windows.Forms.StatusBar> se, <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> že vlastnost `true`ovládacího prvku je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="b38ec-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="b38ec-108">Chcete-li zjistit, na který panel bylo klepnuto</span><span class="sxs-lookup"><span data-stu-id="b38ec-108">To determine which panel was clicked</span></span>  
  
1. <span data-ttu-id="b38ec-109">V <xref:System.Windows.Forms.StatusBar.PanelClick> obslužné `Select Case` rutině události `switch case` použijte příkaz (v jazyce Visual Basic) nebo (Visual C# nebo Visual C++) k určení panelu, na který klepnul, a to prozkoumáním indexu panelu, na který klepnul v argumentech události.</span><span class="sxs-lookup"><span data-stu-id="b38ec-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in Visual Basic) or `switch case` (Visual C# or Visual C++) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="b38ec-110">Následující příklad kódu vyžaduje přítomnost <xref:System.Windows.Forms.StatusBar> ovládacího prvku `StatusBar1`a dvou <xref:System.Windows.Forms.StatusBarPanel> objektů `StatusBarPanel1` ve `StatusBarPanel2`formuláři a .</span><span class="sxs-lookup"><span data-stu-id="b38ec-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     <span data-ttu-id="b38ec-111">(Visual C#, Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="b38ec-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.statusBar1.PanelClick += new
       System.Windows.Forms.StatusBarPanelClickEventHandler
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b38ec-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b38ec-112">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="b38ec-113">Postupy: Nastavení velikosti panelů stavového řádku</span><span class="sxs-lookup"><span data-stu-id="b38ec-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="b38ec-114">Návod: Aktualizace informací stavového řádku za běhu</span><span class="sxs-lookup"><span data-stu-id="b38ec-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="b38ec-115">Přehled ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="b38ec-115">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)

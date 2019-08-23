---
title: 'Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím'
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
ms.openlocfilehash: 6229d8965949641105cd0e9708474c3249d52d1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965725"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="fcd6a-102">Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="fcd6a-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
> <span data-ttu-id="fcd6a-103"><xref:System.Windows.Forms.ToolStripStatusLabel> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBarPanel> Ovládací prvky <xref:System.Windows.Forms.StatusStrip> a nahrazují<xref:System.Windows.Forms.StatusBar> a přidávají funkce ovládacím prvkům a; ovládací prvky a jsou však uchovávány pro zpětnou kompatibilitu i pro budoucí použití, pokud výběrem.</span><span class="sxs-lookup"><span data-stu-id="fcd6a-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="fcd6a-104">Chcete-li programovat ovládací prvek stavového [ovládacího prvku](statusbar-control-windows-forms.md) pro reakci na kliknutí uživatele, použijte příkaz <xref:System.Windows.Forms.StatusBar.PanelClick> Case v rámci události.</span><span class="sxs-lookup"><span data-stu-id="fcd6a-104">To program the [StatusBar Control](statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="fcd6a-105">Událost obsahuje argument (argument panel), který obsahuje odkaz na kliknutí <xref:System.Windows.Forms.StatusBarPanel>.</span><span class="sxs-lookup"><span data-stu-id="fcd6a-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="fcd6a-106">Pomocí tohoto odkazu můžete určit index kliknutí na panely a program odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="fcd6a-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcd6a-107">Zajistěte <xref:System.Windows.Forms.StatusBar> , aby <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost ovládacího prvku byla `true`nastavena na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fcd6a-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="fcd6a-108">Určení panelu, na který byl kliknuto</span><span class="sxs-lookup"><span data-stu-id="fcd6a-108">To determine which panel was clicked</span></span>  
  
1. <span data-ttu-id="fcd6a-109">`switch case` `Select Case`Vobslužné rutině události použijte příkaz (v Visual Basic) nebo (Visual C# nebo Visual C++) a určete, na který panel byl klikl, prozkoumejte index kliknutí na panelu v argumentech události. <xref:System.Windows.Forms.StatusBar.PanelClick></span><span class="sxs-lookup"><span data-stu-id="fcd6a-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in Visual Basic) or `switch case` (Visual C# or Visual C++) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="fcd6a-110">Následující příklad kódu vyžaduje přítomnost, ve <xref:System.Windows.Forms.StatusBar> formuláři ovládacího prvku, `StatusBarPanel1` `StatusBar1`, a dvou <xref:System.Windows.Forms.StatusBarPanel> objektů a `StatusBarPanel2`.</span><span class="sxs-lookup"><span data-stu-id="fcd6a-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
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
  
     <span data-ttu-id="fcd6a-111">(Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="fcd6a-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fcd6a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcd6a-112">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="fcd6a-113">Postupy: Nastavení velikosti panelů stavového řádku</span><span class="sxs-lookup"><span data-stu-id="fcd6a-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="fcd6a-114">Návod: Aktualizace informací stavového řádku za běhu</span><span class="sxs-lookup"><span data-stu-id="fcd6a-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="fcd6a-115">Přehled ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="fcd6a-115">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)

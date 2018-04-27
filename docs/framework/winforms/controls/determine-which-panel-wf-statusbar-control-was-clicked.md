---
title: 'Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 35dc392ed95a5dbe8182b1adbd05affea55d0baa
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="04b78-102">Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="04b78-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="04b78-103"><xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkcí do <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky jsou uchovány pro zpětnou kompatibilitu a budoucí použití, pokud jste Vyberte.</span><span class="sxs-lookup"><span data-stu-id="04b78-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="04b78-104">Programu [StatusBar – ovládací prvek](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) řízení reakce na kliknutí uživatele, použijte příkaz case v rámci <xref:System.Windows.Forms.StatusBar.PanelClick> událostí.</span><span class="sxs-lookup"><span data-stu-id="04b78-104">To program the [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="04b78-105">Události obsahuje argument (argument panely), který obsahuje odkaz na kliknutelnou <xref:System.Windows.Forms.StatusBarPanel>.</span><span class="sxs-lookup"><span data-stu-id="04b78-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="04b78-106">Pomocí tohoto odkazu, můžete určit index panelu kliknutelnou a odpovídajícím způsobem programu.</span><span class="sxs-lookup"><span data-stu-id="04b78-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04b78-107">Ujistěte se, že <xref:System.Windows.Forms.StatusBar> ovládacího prvku <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="04b78-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="04b78-108">K určení panelu označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="04b78-108">To determine which panel was clicked</span></span>  
  
1.  <span data-ttu-id="04b78-109">V <xref:System.Windows.Forms.StatusBar.PanelClick> obslužné rutiny události, použití `Select Case` (v jazyce Visual Basic) nebo `switch case` (Visual C# nebo [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) příkaz k určení panelu označeného prověřením index kliknutelnou panelu argumenty událostí.</span><span class="sxs-lookup"><span data-stu-id="04b78-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in Visual Basic) or `switch case` (Visual C# or [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="04b78-110">Následující příklad kódu vyžaduje přítomnost na formuláři, nástroje <xref:System.Windows.Forms.StatusBar> řízení, `StatusBar1`a dvě <xref:System.Windows.Forms.StatusBarPanel> objekty, `StatusBarPanel1` a `StatusBarPanel2`.</span><span class="sxs-lookup"><span data-stu-id="04b78-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
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
  
     <span data-ttu-id="04b78-111">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="04b78-111">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="04b78-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="04b78-112">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="04b78-113">Postupy: Nastavení velikosti panelů stavového řádku</span><span class="sxs-lookup"><span data-stu-id="04b78-113">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [<span data-ttu-id="04b78-114">Návod: Aktualizace informací stavového řádku za běhu</span><span class="sxs-lookup"><span data-stu-id="04b78-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [<span data-ttu-id="04b78-115">Přehled ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="04b78-115">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)

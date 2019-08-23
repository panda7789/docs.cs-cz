---
title: 'Postupy: Nastavení velikosti panelů stavového řádku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- StatusBar control [Windows Forms], panel size
- status bars [Windows Forms], setting panel size
- panels [Windows Forms], setting size in status bars
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
ms.openlocfilehash: 4ba0f7f02b548a5d9ea1a99605a668f449b3e4a9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923630"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a><span data-ttu-id="b0727-102">Postupy: Nastavení velikosti panelů stavového řádku</span><span class="sxs-lookup"><span data-stu-id="b0727-102">How to: Set the Size of Status-Bar Panels</span></span>
> [!NOTE]
> <span data-ttu-id="b0727-103">Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.ToolStripStatusLabel></span><span class="sxs-lookup"><span data-stu-id="b0727-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="b0727-104">Každá instance <xref:System.Windows.Forms.StatusBarPanel> třídy v ovládacím prvku stavový ovládací prvek má několik dynamických vlastností, které určují jeho šířku a velikost chování za běhu. [](statusbar-control-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="b0727-104">Each instance of the <xref:System.Windows.Forms.StatusBarPanel> class within a [StatusBar Control](statusbar-control-windows-forms.md) control has a number of dynamic properties that determine its width and resize behavior at run time.</span></span>  
  
### <a name="to-set-the-size-of-a-panel"></a><span data-ttu-id="b0727-105">Nastavení velikosti panelu</span><span class="sxs-lookup"><span data-stu-id="b0727-105">To set the size of a panel</span></span>  
  
1. <span data-ttu-id="b0727-106">V proceduře <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>nastavte vlastnosti, <xref:System.Windows.Forms.StatusBarPanel.Width%2A> <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>a (nebo libovolnou podmnožinu v ní) pro panely stavového <xref:System.Windows.Forms.StatusBar.Panels%2A> řádku pomocí <xref:System.Windows.Forms.StatusBarPanel> jejich indexu předaného prostřednictvím vlastnosti kolekce.</span><span class="sxs-lookup"><span data-stu-id="b0727-106">In a procedure, set the <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, and <xref:System.Windows.Forms.StatusBarPanel.Width%2A> properties (or any subset therein) for the status-bar panels using their index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property of the <xref:System.Windows.Forms.StatusBarPanel> collection.</span></span>  
  
    ```vb  
    Public Sub SetStatusBarPanelSize()  
    ' Create panel and set text property.  
       StatusBar1.Panels.Add("One")  
    ' Set properties of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(0).Width = 200  
    ' Enable the StatusBar control to display panels.  
       StatusBar1.ShowPanels = True  
        End Sub  
    ```  
  
    ```csharp  
    public void SetStatusBarPanelSize()  
    {  
       // Create panel and set text property.  
       statusBar1.Panels.Add("One");  
       // Set properties of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[0].Width = 200;  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void SetStatusBarPanelSize()  
       {  
          // Create panel and set text property.  
          statusBar1->Panels->Add("One");  
          // Set properties of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[0]->Width = 200;  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b0727-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0727-107">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="b0727-108">Návod: Aktualizace informací stavového řádku za běhu</span><span class="sxs-lookup"><span data-stu-id="b0727-108">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="b0727-109">Postupy: Určete, na který panel model Windows Forms ovládací prvek stavový řádek.</span><span class="sxs-lookup"><span data-stu-id="b0727-109">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="b0727-110">Přehled ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="b0727-110">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)

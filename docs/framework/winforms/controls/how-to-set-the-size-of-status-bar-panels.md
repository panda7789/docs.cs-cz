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
ms.openlocfilehash: be1f216af61c1e7b77e84c584dc9d965a97c56b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539655"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>Postupy: Nastavení velikosti panelů stavového řádku
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripStatusLabel> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.StatusBar> řízení; však <xref:System.Windows.Forms.StatusBar> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.  
  
 Každá instance <xref:System.Windows.Forms.StatusBarPanel> třídy v rámci [ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) ovládací prvek má řadu dynamické vlastnosti, které určit šířku a změňte jeho velikost chování za běhu.  
  
### <a name="to-set-the-size-of-a-panel"></a>Nastavení velikosti panelu  
  
1.  V postupu, nastavte <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, a <xref:System.Windows.Forms.StatusBarPanel.Width%2A> vlastnosti (nebo všechny dílčí v něm) na stavový řádek předává panelů pomocí příslušného indexu <xref:System.Windows.Forms.StatusBar.Panels%2A> vlastnost <xref:System.Windows.Forms.StatusBarPanel> kolekce.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Návod: Aktualizace informací stavového řádku za běhu](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)
- [Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
- [Přehled ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)

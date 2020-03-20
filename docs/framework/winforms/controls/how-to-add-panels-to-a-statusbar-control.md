---
title: 'Postupy: Přidání panelů do ovládacího prvku StatusBar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- panels [Windows Forms], status bars
- status bars [Windows Forms], adding panels
- StatusBar control [Windows Forms], adding panels
ms.assetid: 835e3902-288c-4c38-9d69-0696d8695009
ms.openlocfilehash: 386c8cae425c458ddf4c446a454ae4213761e651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142196"
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a>Postupy: Přidání panelů do ovládacího prvku StatusBar
> [!IMPORTANT]
> Ovládací <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> prvky a nahradit a <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> přidat funkce a ovládací prvky; ovládací <xref:System.Windows.Forms.StatusBar> prvky <xref:System.Windows.Forms.StatusBarPanel> a jsou však zachovány pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.  
  
 Programovatelná oblast v rámci ovládacího prvku [Stavový](statusbar-control-windows-forms.md) <xref:System.Windows.Forms.StatusBarPanel> panel se skládá z instancí třídy. Ty jsou přidány prostřednictvím <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> dodatky do třídy.  
  
### <a name="to-add-panels-to-a-status-bar"></a>Přidání panelů do stavového řádku  
  
1. V postupu vytvořte panely stavového řádku <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>jejich přidáním do . Určete nastavení vlastností pro jednotlivé panely <xref:System.Windows.Forms.StatusBar.Panels%2A> pomocí jeho indexu promíjené vlastností.  
  
     V následujícím příkladu kódu je cesta nastavená pro umístění ikony složka **Dokumenty.** Toto umístění se používá, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tuto složku. Výběr tohoto umístění také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci. Následující příklad vyžaduje formulář <xref:System.Windows.Forms.StatusBar> s již přidaným ovládacím prvkem.  
  
    > [!NOTE]
    > Je <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> kolekce na základě nula, takže kód by měl postupovat odpovídajícím způsobem.  
  
    ```vb  
    Public Sub CreateStatusBarPanels()  
    ' Create panels and set text property.  
       StatusBar1.Panels.Add("One")  
       StatusBar1.Panels.Add("Two")  
       StatusBar1.Panels.Add("Three")  
    ' Set properties of StatusBar panels.  
    ' Set AutoSize property of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(1).AutoSize = StatusBarPanelAutoSize.Contents  
       StatusBar1.Panels(2).AutoSize = StatusBarPanelAutoSize.Contents  
    ' Set BorderStyle property of panels.  
       StatusBar1.Panels(0).BorderStyle = StatusBarPanelBorderStyle.Raised  
       StatusBar1.Panels(1).BorderStyle = StatusBarPanelBorderStyle.Sunken  
       StatusBar1.Panels(2).BorderStyle = StatusBarPanelBorderStyle.Raised  
    ' Set Icon property of third panel. You should replace the bolded  
    ' icon in the sample below with an icon of your own choosing.  
       StatusBar1.Panels(2).Icon = New _
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
       StatusBar1.ShowPanels = True  
    End Sub  
    ```  
  
    ```csharp  
    public void CreateStatusBarPanels()  
    {  
       // Create panels and set text property.  
       statusBar1.Panels.Add("One");  
       statusBar1.Panels.Add("Two");  
       statusBar1.Panels.Add("Three");  
       // Set properties of StatusBar panels.  
       // Set AutoSize property of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[1].AutoSize = StatusBarPanelAutoSize.Contents;  
       statusBar1.Panels[2].AutoSize = StatusBarPanelAutoSize.Contents;  
       // Set BorderStyle property of panels.  
       statusBar1.Panels[0].BorderStyle =  
          StatusBarPanelBorderStyle.Raised;  
       statusBar1.Panels[1].BorderStyle = StatusBarPanelBorderStyle.Sunken;  
       statusBar1.Panels[2].BorderStyle = StatusBarPanelBorderStyle.Raised;  
       // Set Icon property of third panel. You should replace the bolded  
       // icon in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       statusBar1.Panels[2].Icon =
          new System.Drawing.Icon (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Icon.ico");  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void CreateStatusBarPanels()  
       {  
          // Create panels and set text property.  
          statusBar1->Panels->Add("One");  
          statusBar1->Panels->Add("Two");  
          statusBar1->Panels->Add("Three");  
          // Set properties of StatusBar panels.  
          // Set AutoSize property of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[1]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          statusBar1->Panels[2]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          // Set BorderStyle property of panels.  
          statusBar1->Panels[0]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          statusBar1->Panels[1]->BorderStyle =  
             StatusBarPanelBorderStyle::Sunken;  
          statusBar1->Panels[2]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          // Set Icon property of third panel.  
          // You should replace the bolded image
          // in the sample below with an icon of your own choosing.  
          statusBar1->Panels[2]->Icon =  
             gcnew System::Drawing::Icon(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Icon.ico"));  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Dialogové okno Editor kolekcí](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))
- [Postupy: Nastavení velikosti panelů stavového řádku](how-to-set-the-size-of-status-bar-panels.md)
- [Návod: Aktualizace informací stavového řádku za běhu](walkthrough-updating-status-bar-information-at-run-time.md)
- [Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [Přehled ovládacího prvku StatusBar](statusbar-control-overview-windows-forms.md)

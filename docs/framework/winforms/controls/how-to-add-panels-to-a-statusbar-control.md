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
ms.openlocfilehash: fa5246d76e09091350a5d5276f2c06824b9906d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a>Postupy: Přidání panelů do ovládacího prvku StatusBar
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkcí do <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky jsou uchovány pro zpětnou kompatibilitu a budoucí použití, pokud jste Vyberte.  
  
 Programovatelný oblasti v rámci [StatusBar – ovládací prvek](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) řízení se skládá z instancí <xref:System.Windows.Forms.StatusBarPanel> třídy. Tyto jsou přidány prostřednictvím doplňky <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> třídy.  
  
### <a name="to-add-panels-to-a-status-bar"></a>Přidání panelů do stavového řádku  
  
1.  V postupu, vytvořit jejich přidáním do panelů stavového řádku <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>. Zadejte nastavení vlastností pro jednotlivé panely pomocí jeho index předána <xref:System.Windows.Forms.StatusBar.Panels%2A> vlastnost.  
  
     V následujícím příkladu kódu cesta pro umístění ikony je nastavena **dokumenty** složky. Toto umístění se používá, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat této složky. Výběr toto umístění také umožňuje uživatelům s minimální systém úrovně přístupu pro aplikaci bezpečně spustit. Následující příklad vyžaduje formulář s <xref:System.Windows.Forms.StatusBar> ovládací prvek již přidán.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> Je soubor od nuly, kód by měl pokračovat odpovídajícím způsobem.  
  
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
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Dialogové okno Editor kolekcí](http://msdn.microsoft.com/library/53fb3aad-bffa-4da5-ac89-8438e6fc803c)  
 [Postupy: Nastavení velikosti panelů stavového řádku](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [Návod: Aktualizace informací stavového řádku za běhu](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [Přehled ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)

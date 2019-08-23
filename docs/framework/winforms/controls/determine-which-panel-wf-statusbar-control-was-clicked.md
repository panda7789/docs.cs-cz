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
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripStatusLabel> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBarPanel> Ovládací prvky <xref:System.Windows.Forms.StatusStrip> a nahrazují<xref:System.Windows.Forms.StatusBar> a přidávají funkce ovládacím prvkům a; ovládací prvky a jsou však uchovávány pro zpětnou kompatibilitu i pro budoucí použití, pokud výběrem.  
  
 Chcete-li programovat ovládací prvek stavového [ovládacího prvku](statusbar-control-windows-forms.md) pro reakci na kliknutí uživatele, použijte příkaz <xref:System.Windows.Forms.StatusBar.PanelClick> Case v rámci události. Událost obsahuje argument (argument panel), který obsahuje odkaz na kliknutí <xref:System.Windows.Forms.StatusBarPanel>. Pomocí tohoto odkazu můžete určit index kliknutí na panely a program odpovídajícím způsobem.  
  
> [!NOTE]
> Zajistěte <xref:System.Windows.Forms.StatusBar> , aby <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost ovládacího prvku byla `true`nastavena na hodnotu.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Určení panelu, na který byl kliknuto  
  
1. `switch case` `Select Case`Vobslužné rutině události použijte příkaz (v Visual Basic) nebo (Visual C# nebo Visual C++) a určete, na který panel byl klikl, prozkoumejte index kliknutí na panelu v argumentech události. <xref:System.Windows.Forms.StatusBar.PanelClick>  
  
     Následující příklad kódu vyžaduje přítomnost, ve <xref:System.Windows.Forms.StatusBar> formuláři ovládacího prvku, `StatusBarPanel1` `StatusBar1`, a dvou <xref:System.Windows.Forms.StatusBarPanel> objektů a `StatusBarPanel2`.  
  
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
  
     (Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Postupy: Nastavení velikosti panelů stavového řádku](how-to-set-the-size-of-status-bar-panels.md)
- [Návod: Aktualizace informací stavového řádku za běhu](walkthrough-updating-status-bar-information-at-run-time.md)
- [Přehled ovládacího prvku StatusBar](statusbar-control-overview-windows-forms.md)

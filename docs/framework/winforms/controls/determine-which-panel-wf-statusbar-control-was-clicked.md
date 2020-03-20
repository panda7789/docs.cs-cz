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
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím
> [!IMPORTANT]
> Ovládací <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> prvky a nahradit a <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> přidat funkce a ovládací prvky; ovládací <xref:System.Windows.Forms.StatusBar> prvky <xref:System.Windows.Forms.StatusBarPanel> a jsou však zachovány pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.  
  
 Chcete-li naprogramovat ovládací prvek [Stavový panel](statusbar-control-windows-forms.md) tak, <xref:System.Windows.Forms.StatusBar.PanelClick> aby reagoval na kliknutí uživatele, použijte příkaz case v rámci události. Událost obsahuje argument (argument panelu), který obsahuje odkaz <xref:System.Windows.Forms.StatusBarPanel>na klepnutí . Pomocí tohoto odkazu můžete určit index panelu, na který jste klepnuli, a odpovídajícím způsobem programovat.  
  
> [!NOTE]
> Ujistěte <xref:System.Windows.Forms.StatusBar> se, <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> že vlastnost `true`ovládacího prvku je nastavena na .  
  
### <a name="to-determine-which-panel-was-clicked"></a>Chcete-li zjistit, na který panel bylo klepnuto  
  
1. V <xref:System.Windows.Forms.StatusBar.PanelClick> obslužné `Select Case` rutině události `switch case` použijte příkaz (v jazyce Visual Basic) nebo (Visual C# nebo Visual C++) k určení panelu, na který klepnul, a to prozkoumáním indexu panelu, na který klepnul v argumentech události.  
  
     Následující příklad kódu vyžaduje přítomnost <xref:System.Windows.Forms.StatusBar> ovládacího prvku `StatusBar1`a dvou <xref:System.Windows.Forms.StatusBarPanel> objektů `StatusBarPanel1` ve `StatusBarPanel2`formuláři a .  
  
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
  
     (Visual C#, Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Postupy: Nastavení velikosti panelů stavového řádku](how-to-set-the-size-of-status-bar-panels.md)
- [Návod: Aktualizace informací stavového řádku za běhu](walkthrough-updating-status-bar-information-at-run-time.md)
- [Přehled ovládacího prvku StatusBar](statusbar-control-overview-windows-forms.md)

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
ms.openlocfilehash: b83dc7273c612e914840307bc749abef780284ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527971"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkcí do <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky jsou uchovány pro zpětnou kompatibilitu a budoucí použití, pokud jste Vyberte.  
  
 Programu [StatusBar – ovládací prvek](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) řízení reakce na kliknutí uživatele, použijte příkaz case v rámci <xref:System.Windows.Forms.StatusBar.PanelClick> událostí. Události obsahuje argument (argument panely), který obsahuje odkaz na kliknutelnou <xref:System.Windows.Forms.StatusBarPanel>. Pomocí tohoto odkazu, můžete určit index panelu kliknutelnou a odpovídajícím způsobem programu.  
  
> [!NOTE]
>  Ujistěte se, že <xref:System.Windows.Forms.StatusBar> ovládacího prvku <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> je nastavena na `true`.  
  
### <a name="to-determine-which-panel-was-clicked"></a>K určení panelu označeného kliknutím  
  
1.  V <xref:System.Windows.Forms.StatusBar.PanelClick> obslužné rutiny události, použití `Select Case` (v jazyce Visual Basic) nebo `switch case` (Visual C# nebo [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) příkaz k určení panelu označeného prověřením index kliknutelnou panelu argumenty událostí.  
  
     Následující příklad kódu vyžaduje přítomnost na formuláři, nástroje <xref:System.Windows.Forms.StatusBar> řízení, `StatusBar1`a dvě <xref:System.Windows.Forms.StatusBarPanel> objekty, `StatusBarPanel1` a `StatusBarPanel2`.  
  
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
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
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
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Postupy: Nastavení velikosti panelů stavového řádku](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [Návod: Aktualizace informací stavového řádku za běhu](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [Přehled ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)

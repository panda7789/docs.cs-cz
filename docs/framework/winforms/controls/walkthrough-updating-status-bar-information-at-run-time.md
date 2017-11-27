---
title: "Návod: Aktualizace informací stavového řádku za běhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c67aa303f375734408201ce15d1c3db3dc32c8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>Návod: Aktualizace informací stavového řádku za běhu
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkcí do <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky jsou uchovány pro zpětnou kompatibilitu a budoucí použití, pokud jste Vyberte.  
  
 Často bude program volání pro aktualizaci obsahu stav panelu panelů dynamicky za běhu, na základě změn stavu aplikace nebo jiných interakci s uživatelem. Toto je běžným způsobem uživatelé signál, že jsou povoleny klíče například klávesy CAPS LOCK, NUMLOCK nebo SCROLL LOCK, nebo zadejte datum nebo hodiny jako pohodlný odkaz.  
  
 V následujícím příkladu použijete instanci <xref:System.Windows.Forms.StatusBarPanel> třída pro hostitele hodiny.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Připravit pro aktualizace stavového řádku  
  
1.  Vytvoření nového formuláře Windows.  
  
2.  Přidat <xref:System.Windows.Forms.StatusBar> ovládacího prvku do svého formuláře. Podrobnosti najdete v tématu [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
3.  Přidat panel panelu Stav pro vaše <xref:System.Windows.Forms.StatusBar> ovládacího prvku. Podrobnosti najdete v tématu [postupy: přidání panelů do ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).  
  
4.  Pro <xref:System.Windows.Forms.StatusBar> řízení, které jste přidali do svého formuláře nastavené <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `true`.  
  
5.  Přidat Windows Forms <xref:System.Windows.Forms.Timer> součásti pro formulář.  
  
    > [!NOTE]
    >  Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> součásti je určen pro prostředí Windows Forms. Pokud potřebujete časovač, který je vhodný pro prostředí serveru, najdete v části [Úvod do serverové časovače](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
6.  Nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true`.  
  
7.  Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost <xref:System.Windows.Forms.Timer> na 30000.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost <xref:System.Windows.Forms.Timer> součást je nastaven na 30 sekund (30 000 milisekund) zajistit, že přesný čas se projeví v čase, zobrazí.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>K implementaci časovače aktualizace stavového řádku  
  
1.  Vložte následující kód do obslužné rutiny události z <xref:System.Windows.Forms.Timer> součást aktualizovat na panelu <xref:System.Windows.Forms.StatusBar> ovládacího prvku.  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     V tomto okamžiku jste připraveni ke spuštění aplikace a sledovat hodiny spuštěné v panelu panelu stavu.  
  
### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Ladění aplikace a stiskněte klávesu F5 a spusťte ho. Podrobnosti o ladění najdete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
    > [!NOTE]
    >  To bude trvat přibližně 30 sekund pro hodiny se objeví ve stavovém řádku. Toto je získat nejpřesnější čas možné. Pokud naopak Pokud chcete, aby hodiny zobrazí dříve, můžete snížit hodnotu <xref:System.Windows.Forms.Timer.Interval%2A> vlastností nastavenou v kroku 7 v předchozím postupu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Postupy: přidání panelů do ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 [Postupy: určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [Přehled ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)

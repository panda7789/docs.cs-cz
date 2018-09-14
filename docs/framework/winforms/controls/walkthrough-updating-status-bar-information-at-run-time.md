---
title: 'Návod: Aktualizace informací stavového řádku za běhu'
ms.date: 03/30/2017
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
ms.openlocfilehash: 49722d5dadf694e8ee3037646652b921ddda3e91
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595591"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>Návod: Aktualizace informací stavového řádku za běhu
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkce, které <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud jste Zvolte.  
  
 Často program bude volat pro vás k aktualizaci obsahu stav panelu panelů dynamicky za běhu na základě změn stavu aplikace nebo jiných interakcí uživatele. Toto je běžný způsob signál uživatele, že jsou povolené kláves, jako jsou CAPS LOCK, NUM LOCK nebo SCROLL LOCK, nebo zadejte datum nebo čas jako pohodlný odkaz.  
  
 V následujícím příkladu použijete instance <xref:System.Windows.Forms.StatusBarPanel> třídy k hostování hodin.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Připravit na stavovém řádku pro aktualizaci  
  
1.  Vytvoření nového formuláře Windows.  
  
2.  Přidat <xref:System.Windows.Forms.StatusBar> ovládací prvek do formuláře. Podrobnosti najdete v tématu [postupy: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
3.  Přidat stav panelu panelu s vaší <xref:System.Windows.Forms.StatusBar> ovládacího prvku. Podrobnosti najdete v tématu [postupy: přidání panelů do ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).  
  
4.  Pro <xref:System.Windows.Forms.StatusBar> jste přidali do svého formuláře ovládací prvek nastavit <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `true`.  
  
5.  Přidání prvku Windows Forms <xref:System.Windows.Forms.Timer> komponentu do formuláře.  
  
    > [!NOTE]
    >  Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> součásti je určen pro prostředí Windows Forms. Pokud potřebujete časovač, který je vhodný pro prostředí serveru, přečtěte si [Úvod do serverových časovače](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
6.  Nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true`.  
  
7.  Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost <xref:System.Windows.Forms.Timer> na 30000.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost <xref:System.Windows.Forms.Timer> komponenty nastavena na 30 sekund (30 000 milisekund) k zajištění, že v čase, zobrazí se projeví přesnému času.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>K implementaci časovače aktualizace stavového řádku  
  
1.  Vložte následující kód do obslužné rutiny události <xref:System.Windows.Forms.Timer> součásti na panelu aktualizovat <xref:System.Windows.Forms.StatusBar> ovládacího prvku.  
  
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
  
     V tuto chvíli jste připraveni ke spuštění aplikace a sledujte hodin spuštěna v panelu Stav panelu.  
  
### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Ladit aplikaci a stiskněte klávesu F5 a spusťte ho. Podrobnosti o ladění naleznete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
    > [!NOTE]
    >  To bude trvat přibližně 30 sekund hodin se zobrazí ve stavovém řádku. Toto je získat nejpřesnější čas je to možné. Naopak, aby hodiny zobrazí dříve, můžete snížit hodnotu <xref:System.Windows.Forms.Timer.Interval%2A> vlastnosti, které jste nastavili v kroku 7 v předchozím postupu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Postupy: Přidání panelů do ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 [Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [Přehled ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)

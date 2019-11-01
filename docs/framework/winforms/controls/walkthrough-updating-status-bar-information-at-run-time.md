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
ms.openlocfilehash: f1d22079dfa3a6452efb74ef57530bb43e059a4a
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197098"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>Návod: Aktualizace informací stavového řádku za běhu
> [!IMPORTANT]
> Ovládací prvky <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> nahrazují a přidávají funkce ovládacím prvkům <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel>; ovládací prvky <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> se však uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
 Program často zavolá za účelem dynamické aktualizace obsahu panelů stavového řádku v době běhu na základě změn stavu aplikace nebo jiné interakce uživatele. To je běžný způsob, jak uživatele signalizovat, že jsou povolené klíče, jako je například Caps Lock, NUM LOCK nebo SCROLL LOCK, nebo aby jako pohodlný odkaz poskytovaly datum nebo hodiny.  
  
 V následujícím příkladu použijete instanci třídy <xref:System.Windows.Forms.StatusBarPanel> k hostování hodin.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Získání stavového řádku připraveného k aktualizaci  
  
1. Vytvoří nový formulář Windows.  
  
2. Přidejte ovládací prvek <xref:System.Windows.Forms.StatusBar> do formuláře. Podrobnosti naleznete v tématu [How to: Add Controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
3. Přidejte panel stavového řádku do ovládacího prvku <xref:System.Windows.Forms.StatusBar>. Podrobnosti najdete v tématu [Postup: přidání panelů do ovládacího prvku](how-to-add-panels-to-a-statusbar-control.md)stavový řádek.  
  
4. Pro ovládací prvek <xref:System.Windows.Forms.StatusBar>, který jste přidali do formuláře, nastavte vlastnost <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `true`.  
  
5. Přidejte do formuláře komponentu model Windows Forms <xref:System.Windows.Forms.Timer>.  
  
    > [!NOTE]
    > Komponenta model Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> je navržena pro model Windows Forms prostředí. Pokud potřebujete časovač, který je vhodný pro serverové prostředí, přečtěte si téma [Úvod k časovačům založeným na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
6. Vlastnost <xref:System.Windows.Forms.Timer.Enabled%2A> nastavte na hodnotu `true`.  
  
7. Nastavte vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> <xref:System.Windows.Forms.Timer> na 30000.  
  
    > [!NOTE]
    > Vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> komponenty <xref:System.Windows.Forms.Timer> je nastavená na 30 sekund (30 000 milisekund), aby se zajistilo, že se v zobrazeném čase projeví přesné časy.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Implementace časovače k aktualizaci stavového řádku  
  
1. Vložte následující kód do obslužné rutiny události součásti <xref:System.Windows.Forms.Timer> pro aktualizaci panelu ovládacího prvku <xref:System.Windows.Forms.StatusBar>.  
  
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
  
     V tuto chvíli jste připraveni spustit aplikaci a sledovat, jak se na panelu stavového řádku spouští hodiny.  
  
### <a name="to-test-the-application"></a>Testování aplikace  
  
1. Spusťte ladění aplikace a stisknutím klávesy F5 ji spusťte. Podrobnosti o ladění naleznete v tématu [ladění v aplikaci Visual Studio](/visualstudio/debugger/debugger-feature-tour).  
  
    > [!NOTE]
    > Bude trvat přibližně 30 sekund, než se hodiny zobrazí ve stavovém řádku. Tato možnost získá nejpřesnější čas. Pokud naopak chcete, aby se hodiny zobrazovaly dříve, můžete snížit hodnotu vlastnosti <xref:System.Windows.Forms.Timer.Interval%2A>, kterou jste nastavili v kroku 7 v předchozím postupu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Postupy: Přidání panelů do ovládacího prvku StatusBar](how-to-add-panels-to-a-statusbar-control.md)
- [Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [Přehled ovládacího prvku StatusBar](statusbar-control-overview-windows-forms.md)

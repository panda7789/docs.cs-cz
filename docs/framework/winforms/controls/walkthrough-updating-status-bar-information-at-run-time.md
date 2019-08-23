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
ms.openlocfilehash: 670746a1b964a85bc5136d976d831c6848466797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930986"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>Návod: Aktualizace informací stavového řádku za běhu
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripStatusLabel> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBarPanel> Ovládací prvky <xref:System.Windows.Forms.StatusStrip> a nahrazují<xref:System.Windows.Forms.StatusBar> a přidávají funkce ovládacím prvkům a; ovládací prvky a jsou však uchovávány pro zpětnou kompatibilitu i pro budoucí použití, pokud výběrem.  
  
 Program často zavolá za účelem dynamické aktualizace obsahu panelů stavového řádku v době běhu na základě změn stavu aplikace nebo jiné interakce uživatele. To je běžný způsob, jak uživatele signalizovat, že jsou povolené klíče, jako je například Caps Lock, NUM LOCK nebo SCROLL LOCK, nebo aby jako pohodlný odkaz poskytovaly datum nebo hodiny.  
  
 V následujícím příkladu použijete instanci <xref:System.Windows.Forms.StatusBarPanel> třídy k hostování hodin.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Získání stavového řádku připraveného k aktualizaci  
  
1. Vytvoří nový formulář Windows.  
  
2. <xref:System.Windows.Forms.StatusBar> Přidejte ovládací prvek do formuláře. Podrobnosti najdete v tématu [How to: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.  
  
3. Přidejte panel stavového řádku do <xref:System.Windows.Forms.StatusBar> ovládacího prvku. Podrobnosti najdete v tématu [How to: Přidejte panely do ovládacího prvku](how-to-add-panels-to-a-statusbar-control.md)stavový řádek.  
  
4. Pro ovládací prvek, který jste přidali do formuláře, <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> nastavte vlastnost na `true`hodnotu. <xref:System.Windows.Forms.StatusBar>  
  
5. Přidejte do formuláře <xref:System.Windows.Forms.Timer> komponentu model Windows Forms.  
  
    > [!NOTE]
    > Komponenta model Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> je navržena pro model Windows Forms prostředí. Pokud potřebujete časovač, který je vhodný pro serverové prostředí, přečtěte si téma [Úvod k časovačům založeným na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
6. Nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true`.  
  
7. <xref:System.Windows.Forms.Timer.Interval%2A> Nastavte vlastnost <xref:System.Windows.Forms.Timer> na hodnotu na 30000.  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost<xref:System.Windows.Forms.Timer> komponenty je nastavená na 30 sekund (30 000 milisekund), aby se zajistilo, že se v zobrazeném čase projeví přesné časy.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Implementace časovače k aktualizaci stavového řádku  
  
1. Vložte následující kód do obslužné rutiny <xref:System.Windows.Forms.Timer> události komponenty pro aktualizaci panelu <xref:System.Windows.Forms.StatusBar> ovládacího prvku.  
  
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
  
1. Spusťte ladění aplikace a stisknutím klávesy F5 ji spusťte. Podrobnosti o ladění naleznete v tématu [ladění v aplikaci Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
    > [!NOTE]
    > Bude trvat přibližně 30 sekund, než se hodiny zobrazí ve stavovém řádku. Tato možnost získá nejpřesnější čas. Naopak, pokud chcete, aby se hodiny zobrazovaly dřív, můžete snížit hodnotu <xref:System.Windows.Forms.Timer.Interval%2A> vlastnosti, kterou jste nastavili v kroku 7 v předchozím postupu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Postupy: Přidání panelů do ovládacího prvku stavový řádek](how-to-add-panels-to-a-statusbar-control.md)
- [Postupy: Určete, na který panel model Windows Forms ovládací prvek stavový řádek.](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [Přehled ovládacího prvku StatusBar](statusbar-control-overview-windows-forms.md)

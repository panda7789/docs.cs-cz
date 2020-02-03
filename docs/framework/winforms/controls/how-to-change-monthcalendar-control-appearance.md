---
title: Změnit vzhled ovládacího prvku MonthCalendar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: ded9059ede4ad03f637c0e697b880c41a9a8ba32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746650"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.MonthCalendar> umožňuje přizpůsobit vzhled kalendáře mnoha způsoby. Můžete například nastavit barevné schéma a zvolit zobrazení nebo skrytí čísel týdnů a aktuálního data.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Změna barevného schématu měsíčního kalendáře  
  
- Nastavte vlastnosti, například <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> a <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. Vlastnost <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> také určuje barvu písma pro dny v týdnu. Vlastnost <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Určuje barvu dat, která předcházejí, a dodržujte zobrazené měsíce nebo měsíce.  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    > Počínaje systémem Windows Vista a v závislosti na motivu se může stát, že nastavením některých vlastností se nezmění vzhled kalendáře. Pokud je například Windows nastavené na použití motivu Aero, nastavení <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>nebo vlastností <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> nemá žádný vliv. Je to proto, že aktualizovaná verze kalendáře je vykreslena s vzhled, který je odvozen v době běhu z aktuálního motivu operačního systému. Pokud chcete tyto vlastnosti použít a povolit starší verzi kalendáře, můžete pro svou aplikaci zakázat vizuální styly. Zakázání vizuálních stylů může mít vliv na vzhled a chování jiných ovládacích prvků v aplikaci. Chcete-li zakázat vizuální styly v Visual Basic, otevřete Návrháře projektu a zrušte zaškrtnuté políčko **Povolit vizuální styly pro XP** . Chcete-li zakázat vizuální C#styly v nástroji, otevřete program.cs a odkomentujte `Application.EnableVisualStyles();`. Další informace o vizuálních stylech naleznete v tématu [Povolení vizuálních stylů](/windows/desktop/controls/cookbook-overview).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Zobrazení aktuálního data v dolní části ovládacího prvku  
  
- Vlastnost <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> nastavte na hodnotu `true`. Následující příklad přepíná mezi zobrazením a vynecháním dnešního data při dvojitém kliknutí na formulář.  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     (Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>Zobrazení čísel týdnů  
  
- Vlastnost <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> nastavte na hodnotu `true`. Tuto vlastnost lze nastavit buď v kódu, nebo v okno Vlastnosti.  
  
     Čísla týdnů se zobrazí v samostatném sloupci nalevo od prvního dne v týdnu.  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>Viz také

- [Ovládací prvek MonthCalendar](monthcalendar-control-windows-forms.md)
- [Postupy: Výběr rozsahu kalendářních dat v ovládacím prvku Windows Forms MonthCalendar](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Postupy: Tučné zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar](display-more-than-one-month-wf-monthcalendar-control.md)

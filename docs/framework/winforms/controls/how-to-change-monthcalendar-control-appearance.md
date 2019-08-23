---
title: 'Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: 5582624d881b2d8039bcd5e8ac45e548c7b38f57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929050"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar
Ovládací prvek <xref:System.Windows.Forms.MonthCalendar> model Windows Forms umožňuje přizpůsobit vzhled kalendáře mnoha způsoby. Můžete například nastavit barevné schéma a zvolit zobrazení nebo skrytí čísel týdnů a aktuálního data.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Změna barevného schématu měsíčního kalendáře  
  
- Nastavte vlastnosti <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, jako jsou <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> a <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Vlastnost také určuje barvu písma pro dny v týdnu. <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Vlastnost určuje barvu kalendářních dat, která předchází, a následují po zobrazených měsících nebo měsících.  
  
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
    > Počínaje systémem Windows Vista a v závislosti na motivu se může stát, že nastavením některých vlastností se nezmění vzhled kalendáře. Pokud je <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>například Windows nastavené na použití motivu Aero, nastavení vlastností, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>nebo <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> nemá žádný vliv. Je to proto, že aktualizovaná verze kalendáře je vykreslena s vzhled, který je odvozen v době běhu z aktuálního motivu operačního systému. Pokud chcete tyto vlastnosti použít a povolit starší verzi kalendáře, můžete pro svou aplikaci zakázat vizuální styly. Zakázání vizuálních stylů může mít vliv na vzhled a chování jiných ovládacích prvků v aplikaci. Chcete-li zakázat vizuální styly v Visual Basic, otevřete Návrháře projektu a zrušte zaškrtnuté políčko **Povolit vizuální styly pro XP** . Chcete-li zakázat vizuální C#styly v nástroji, otevřete program.cs `Application.EnableVisualStyles();`a přidejte komentář. Další informace o vizuálních stylech naleznete v tématu [Povolení vizuálních stylů](/windows/desktop/controls/cookbook-overview).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Zobrazení aktuálního data v dolní části ovládacího prvku  
  
- Nastavte <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> vlastnost `true`. Následující příklad přepíná mezi zobrazením a vynecháním dnešního data při dvojitém kliknutí na formulář.  
  
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
  
- Nastavte <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> vlastnost `true`. Tuto vlastnost lze nastavit buď v kódu, nebo v okno Vlastnosti.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek MonthCalendar](monthcalendar-control-windows-forms.md)
- [Postupy: Vyberte rozsah dat v ovládacím prvku model Windows Forms MonthCalendar](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Postupy: Zobrazit konkrétní dny tučně pomocí ovládacího prvku model Windows Forms MonthCalendar](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku model Windows Forms MonthCalendar](display-more-than-one-month-wf-monthcalendar-control.md)

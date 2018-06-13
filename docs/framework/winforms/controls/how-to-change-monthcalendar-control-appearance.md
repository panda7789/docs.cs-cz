---
title: 'Postupy: Změna ovládacího prvku Windows Forms MonthCalendar&#39;s vzhledu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: aab2625afd5159cb2ce726bce16e917a9ad4d834
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531323"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a>Postupy: Změna ovládacího prvku Windows Forms MonthCalendar&#39;s vzhledu
Windows Forms <xref:System.Windows.Forms.MonthCalendar> řízení umožňuje přizpůsobení vzhledu kalendáře mnoha způsoby. Můžete například nastavit barevné schéma a vyberte k zobrazení nebo skrytí čísla týdne a aktuálním datem.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Chcete-li změnit barevné schéma měsíční kalendář  
  
-   Nastavte vlastnosti, jako je třeba <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> a <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Vlastnosti také určuje barvu písma pro dny v týdnu. <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Vlastnost určuje barvu kalendářních dat, které předcházet a postupujte podle zobrazených měsíc nebo měsíce.  
  
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
    >  Spouští se systémem Windows Vista a v závislosti na motiv, nastavení některé vlastnosti nemusí Změna vzhledu kalendáře. Například pokud Windows je nastavena pro použití motivu Aero, nastavení <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> vlastnosti nemá žádný vliv. Je to proto, že je aktualizovaná verze kalendáře vykreslen vzhledově odvozený v době běhu z aktuálního motivu operačního systému. Pokud chcete použít tyto vlastnosti a povolit v předchozích verzích kalendáře, můžete zakázat vizuální styly pro vaši aplikaci. Zakázání vizuální styly může ovlivnit vzhled a chování další ovládací prvky v aplikaci. Zakázání stylů v jazyce Visual Basic, otevřete v Návrháři projektu a zrušte zaškrtnutí políčka **vizuální styly XP povolit** zaškrtávací políčko. Chcete-li zakázat vizuální styly v jazyce C#, otevřete Program.cs a komentář `Application.EnableVisualStyles();`. Další informace o vizuální styly najdete v tématu [postupy: povolení vizuální styly XP Windows](http://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Chcete-li zobrazit aktuální datum v dolní části ovládacího prvku  
  
-   Nastavte <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> vlastnost `true`. Následující příklad Přepne mezi zobrazení a vynechání dnešní datum, když je formulář dvakrát kliknete.  
  
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
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>Zobrazení čísla týdne  
  
-   Nastavte <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> vlastnost `true`. Tuto vlastnost lze nastavit v kódu nebo v okně Vlastnosti.  
  
     Týden čísla se zobrazí v samotném sloupci nalevo od první den v týdnu.  
  
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
 [Ovládací prvek MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Postupy: Výběr rozsahu kalendářních dat v ovládacím prvku Windows Forms MonthCalendar](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Postupy: Tučné zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)

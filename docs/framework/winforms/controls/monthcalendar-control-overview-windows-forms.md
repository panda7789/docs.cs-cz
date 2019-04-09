---
title: MonthCalendar – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: 8928a78735392920d893661c70554bd35eba2886
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106233"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek zobrazí intuitivní grafické rozhraní pro uživatele k zobrazení a nastavit informace o datu. Ovládací prvek zobrazuje kalendář: Mřížka obsahující číslované dny v měsíci, uspořádané do sloupce pod dny v týdnu, s vybraný rozsah kalendářních dat, zvýrazněn. Můžete vybrat jiného měsíce kliknutím na tlačítka se šipkami na obou stranách titulek měsíce. Na rozdíl od podobný <xref:System.Windows.Forms.DateTimePicker> ovládací prvek, vyberete více než jeden den s tímto ovládacím prvkem. Další informace o <xref:System.Windows.Forms.DateTimePicker> řídí, najdete v článku [DateTimePicker – ovládací prvek](datetimepicker-control-windows-forms.md).  
  
## <a name="configuring-the-monthcalendar-control"></a>Konfigurace ovládacího prvku MonthCalendar  
 <xref:System.Windows.Forms.MonthCalendar> Vzhled ovládacího prvku je vysoce konfigurovatelné. Ve výchozím nastavení dnešní datum se zobrazí v kruhu a je také jste si poznamenali v dolní části mřížky. Tuto funkci můžete změnit nastavením <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> a <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> vlastností `false`. Čísla týdnů můžete také přidat do kalendáře nastavením <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> vlastnost `true`. Tím, že nastavíte <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> vlastnost, může mít několik měsíců zobrazeny vodorovně a svisle. Ve výchozím nastavení, se zobrazí neděli jako první den v týdnu, ale každý den, mohou být označeny pomocí <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A> vlastnost.  
  
 Můžete také nastavit určitých dat, který se má zobrazit tučně jednorázově, roční nebo měsíční, tak, že přidáte <xref:System.DateTime> objektů <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>, a <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> vlastnosti. Další informace najdete v tématu [jak: Zobrazení konkrétních dnů Bold s Windows Forms MonthCalendar – ovládací prvek](display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 Klíčové vlastnosti <xref:System.Windows.Forms.MonthCalendar> je ovládací prvek <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, rozsahu dat vybraného v ovládacím prvku. <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> Hodnota nemůže být delší než maximální počet dní, které lze vybrat, nastavte <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A> vlastnost. Nejstarší a nejnovější data, může uživatel vybrat jsou určeny <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> a <xref:System.Windows.Forms.MonthCalendar.MinDate%2A> vlastnosti.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MonthCalendar>
- [Ovládací prvek MonthCalendar](monthcalendar-control-windows-forms.md)

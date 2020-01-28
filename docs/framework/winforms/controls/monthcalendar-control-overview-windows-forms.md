---
title: MonthCalendar – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: a9b56164339d03b380a564b21855f6d94ec06af5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734937"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar – přehled ovládacího prvku (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.MonthCalendar> prezentuje intuitivní grafické rozhraní, které uživatelům umožňuje zobrazovat a nastavovat informace o datu. Ovládací prvek zobrazí kalendář: Mřížka obsahující očíslované dny v měsíci, uspořádaná ve sloupcích pod dny v týdnu s vybraným rozsahem zvýrazněných dat. Kliknutím na tlačítko se šipkou na kterékoli straně nadpisu měsíce můžete vybrat jiný měsíc. Na rozdíl od podobného ovládacího prvku <xref:System.Windows.Forms.DateTimePicker> můžete pomocí tohoto ovládacího prvku vybrat více než jedno datum. Další informace o ovládacím prvku <xref:System.Windows.Forms.DateTimePicker> naleznete v tématu [DateTimePicker Control](datetimepicker-control-windows-forms.md).  
  
## <a name="configuring-the-monthcalendar-control"></a>Konfigurace ovládacího prvku MonthCalendar  
 Vzhled ovládacího prvku <xref:System.Windows.Forms.MonthCalendar> je vysoce konfigurovatelný. Ve výchozím nastavení se dnešní datum zobrazuje v kruhu a je také uvedeno v dolní části mřížky. Tuto funkci můžete změnit nastavením vlastností <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> a <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> na `false`. Do kalendáře můžete přidat také čísla týdnů nastavením vlastnosti <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> na hodnotu `true`. Nastavením vlastnosti <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> můžete mít více měsíců zobrazených vodorovně a svisle. Ve výchozím nastavení se neděle zobrazuje jako první den v týdnu, ale kterýkoli den lze určit pomocí vlastnosti <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A>.  
  
 Přidáním <xref:System.DateTime> objektů do vlastností <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>a <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> můžete také nastavit určitá data tak, aby se zobrazovala tučně na jednom časovém intervalu. Další informace najdete v tématu [Postup: zobrazení konkrétních dnů tučně pomocí ovládacího prvku model Windows Forms MonthCalendar](display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 Klíčovou vlastností ovládacího prvku <xref:System.Windows.Forms.MonthCalendar> je <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, rozsah dat vybraný v ovládacím prvku. Hodnota <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> nemůže překročit maximální počet dní, které je možné vybrat, a nastavte vlastnost <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A>. Nejstarší a poslední datum, které může uživatel vybrat, jsou určena vlastnostmi <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> a <xref:System.Windows.Forms.MonthCalendar.MinDate%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MonthCalendar>
- [Ovládací prvek MonthCalendar](monthcalendar-control-windows-forms.md)

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
ms.openlocfilehash: 7ed917afe2640fe2ffef4904a3795c5f0e84ded9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537405"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.MonthCalendar> řízení uvede intuitivní grafické rozhraní pro uživatele k zobrazení a nastavit informace o datu. Tento ovládací prvek zobrazí kalendář: Mřížka obsahující číslem dny v měsíci, uspořádané ve sloupcích pod dny v týdnu, s vybraný rozsah kalendářních dat zvýrazněná. Kliknutím na tlačítko se šipkou na obou stranách titulek měsíc můžete vybrat jiný měsíc. Na rozdíl od podobné <xref:System.Windows.Forms.DateTimePicker> ovládací prvek, můžete vybrat více než jeden data pro tento ovládací prvek. Další informace o <xref:System.Windows.Forms.DateTimePicker> řízení najdete v tématu [DateTimePicker – ovládací prvek](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md).  
  
## <a name="configuring-the-monthcalendar-control"></a>Konfigurace MonthCalendar – ovládací prvek  
 <xref:System.Windows.Forms.MonthCalendar> Vzhledu ovládacího prvku je vysoce konfigurovatelné. Ve výchozím nastavení dnešní datum zobrazí jako v kroužku a je také jsou uvedené v dolní části mřížky. Tuto funkci můžete změnit nastavením <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> a <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> vlastnosti, které chcete `false`. Čísla týdnů můžete také přidat do kalendáře nastavením <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> vlastnost `true`. Nastavením <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> vlastnost, může mít několik měsíců zobrazovat vodorovně a svisle. Ve výchozím nastavení, je zobrazena neděli jako první den v týdnu, avšak kterýkoli den, mohou být za použití <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A> vlastnost.  
  
 Můžete také nastavit určitá data, která se zobrazí v tučné jednorázově, ročně nebo každý měsíc, přidáním <xref:System.DateTime> objekty ke <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>, a <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> vlastnosti. Další informace najdete v tématu [postupy: zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar Bold](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 Klíčové vlastnosti <xref:System.Windows.Forms.MonthCalendar> ovládací prvek je <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, rozsah dat vybraný v ovládacím prvku. <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> Hodnota nemůže být větší než maximální počet dní, které je možné vybrat, nastavte v <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A> vlastnost. Nejdřívější a nejnovější data, můžete vybrat uživatele byla určena <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> a <xref:System.Windows.Forms.MonthCalendar.MinDate%2A> vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MonthCalendar>  
 [Ovládací prvek MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)

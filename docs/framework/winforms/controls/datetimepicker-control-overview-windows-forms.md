---
title: DateTimePicker – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: 451172b51427e4932470c53737c7bc276920271c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909165"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>DateTimePicker – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DateTimePicker> ovládací prvek umožňuje uživateli vybrat jednu položku ze seznamu data nebo časy. Při použití představující datum, zobrazí se ve dvou částech: rozevírací seznam datum v textu a mřížka, která se zobrazí, když kliknete na šipku dolů vedle seznamu. Mřížka vypadá jako <xref:System.Windows.Forms.MonthCalendar> ovládací prvek, který slouží k výběru několika kalendářních datech. Další informace o <xref:System.Windows.Forms.MonthCalendar> řídí, najdete v článku [MonthCalendar – Přehled ovládacího prvku](monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Pokud chcete <xref:System.Windows.Forms.DateTimePicker> zobrazen jako ovládací prvek pro výběr nebo úpravy dob místo data, nastavte <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> vlastnost `true` a <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Další informace najdete v části [jak: Zobrazení času pomocí ovládacího prvku DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
 Když <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> je nastavena na `true`, zobrazí se vedle vybrané datum v ovládacím prvku zaškrtávací políčko. Pokud je zaškrtnuto zaškrtávací políčko, je možné aktualizovat vybrané hodnoty data a času. Pokud je políčko prázdné, hodnota se zobrazí není k dispozici.  
  
 Ovládací prvek <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> a <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> vlastnosti určit rozsah kalendářních dat a časů. <xref:System.Windows.Forms.DateTimePicker.Value%2A> Vlastnost obsahuje aktuální datum a čas ovládacího prvku nastavená na. Podrobnosti najdete v tématu [jak: Nastavení a vracení kalendářních dat pomocí Windows Forms DateTimePicker – ovládací prvek](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Hodnoty lze zobrazit čtyři formátů, které určil institut NIST <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost: <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>, nebo <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Pokud je vybraný vlastní formát, je nutné nastavit <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> vlastnosti odpovídající řetězci. Podrobnosti najdete v tématu [jak: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
- [Postupy: Nastavení a vrácení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)

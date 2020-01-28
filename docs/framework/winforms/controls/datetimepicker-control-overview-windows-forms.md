---
title: DateTimePicker – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: 63271dd91116c1f68d426f3ed5aa710644ded928
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746941"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>DateTimePicker – přehled ovládacího prvku (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DateTimePicker> umožňuje uživateli vybrat jednu položku ze seznamu kalendářních dat nebo časů. Když se používá k reprezentaci data, zobrazí se ve dvou částech: rozevírací seznam s datem, který je reprezentován textem, a mřížku, která se zobrazí po kliknutí na šipku dolů vedle seznamu. Mřížka vypadá jako ovládací prvek <xref:System.Windows.Forms.MonthCalendar>, který se dá použít k výběru více kalendářních dat. Další informace o ovládacím prvku <xref:System.Windows.Forms.MonthCalendar> naleznete v tématu [Přehled ovládacího prvku MonthCalendar](monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Pokud chcete, aby se <xref:System.Windows.Forms.DateTimePicker> zobrazoval jako ovládací prvek pro vybírání nebo úpravu časů místo kalendářních dat, nastavte vlastnost <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> na hodnotu `true` a vlastnost <xref:System.Windows.Forms.DateTimePicker.Format%2A> na <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Další informace najdete v tématu [Postup: zobrazení času pomocí ovládacího prvku DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
 Je-li vlastnost <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> nastavena na hodnotu `true`, zobrazí se vedle vybraného data v ovládacím prvku zaškrtávací políčko. Když je zaškrtávací políčko zaškrtnuto, je možné aktualizovat vybranou hodnotu data a času. Pokud je zaškrtávací políčko prázdné, hodnota se zobrazí jako nedostupná.  
  
 Vlastnosti <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> a <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> ovládacího prvku určují rozsah kalendářních dat a časů. Vlastnost <xref:System.Windows.Forms.DateTimePicker.Value%2A> obsahuje aktuální datum a čas, na který je ovládací prvek nastaven. Podrobnosti naleznete v tématu [How to: set a Return data with model Windows Forms DateTimePicker Control](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Hodnoty lze zobrazit ve čtyřech formátech, které jsou nastaveny vlastností <xref:System.Windows.Forms.DateTimePicker.Format%2A>: <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>nebo <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Pokud je vybrán vlastní formát, je nutné nastavit vlastnost <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> na příslušný řetězec. Podrobnosti naleznete v tématu [How to: Display Data in a Custom with the model Windows Forms DateTimePicker Control](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
- [Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)

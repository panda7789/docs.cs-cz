---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 555bf31b27ba233ffa54438077984b02b5e3084a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911977"
---
# <a name="datepicker"></a>DatePicker
<xref:System.Windows.Controls.DatePicker> Ovládací prvek umožňuje uživateli vybrat datum zadáním buď do textového pole, nebo pomocí rozevíracího seznamu <xref:System.Windows.Controls.Calendar> ovládacího prvku.  
  
 Následující ilustrace ukazuje <xref:System.Windows.Controls.DatePicker>.  
  
 ![Ovládací prvek DatePicker](./media/ndp-datepicker.png "NDP_DatePicker")  
Ovládací prvek DatePicker  
  
 Řadu <xref:System.Windows.Controls.DatePicker> vlastností ovládacího prvku jsou pro správu integrované <xref:System.Windows.Controls.Calendar>a funkce stejně jako rovnocenné vlastností v <xref:System.Windows.Controls.Calendar>. Konkrétně se <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, a <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> vlastnosti fungovat stejně jako jejich <xref:System.Windows.Controls.Calendar> protějšky. Další informace naleznete v tématu <xref:System.Windows.Controls.Calendar>.  
  
 Uživatelé mohou zadat data přímo do textové pole, které nastaví <xref:System.Windows.Controls.DatePicker.Text%2A> vlastnost. Pokud <xref:System.Windows.Controls.DatePicker> zadaný řetězec nelze převést na platné datum <xref:System.Windows.Controls.DatePicker.DateValidationError> událost se vyvolá. Ve výchozím nastavení, to způsobí výjimku, ale obslužnou rutinu události pro <xref:System.Windows.Controls.DatePicker.DateValidationError> můžete nastavit <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> vlastnost `false` a zakázat výjimku vyvolána.  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvky](index.md)
- [Styly a šablony](styling-and-templating.md)

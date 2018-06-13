---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 910ce09bfad6a46e3d96784b980ee4175c3d26a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550061"
---
# <a name="datepicker"></a>DatePicker
<xref:System.Windows.Controls.DatePicker> Řízení umožňuje uživateli zadáním buď ho do textového pole, nebo pomocí rozevíracího seznamu vyberte datum <xref:System.Windows.Controls.Calendar> ovládacího prvku.  
  
 Následující obrázek znázorňuje <xref:System.Windows.Controls.DatePicker>.  
  
 ![Ovládací prvek DatePicker řízení](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")  
Ovládací prvek DatePicker ovládací prvek  
  
 Řadu <xref:System.Windows.Controls.DatePicker> vlastností ovládacího prvku jsou pro správu jeho vestavěné <xref:System.Windows.Controls.Calendar>a funkce stejně jako na ekvivalentní vlastnost v <xref:System.Windows.Controls.Calendar>. Konkrétně <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, a <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> vlastnosti fungovat stejně jako na jejich <xref:System.Windows.Controls.Calendar> svými protějšky. Další informace naleznete v tématu <xref:System.Windows.Controls.Calendar>.  
  
 Uživatelé mohou zadat datum přímo do textové pole, která nastaví <xref:System.Windows.Controls.DatePicker.Text%2A> vlastnost. Pokud <xref:System.Windows.Controls.DatePicker> zadaný řetězec nelze převést na platné datum <xref:System.Windows.Controls.DatePicker.DateValidationError> událostí, bude vyvolána. Ve výchozím nastavení, to způsobí výjimku, ale obslužné rutiny události pro <xref:System.Windows.Controls.DatePicker.DateValidationError> můžete nastavit <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> vlastnost `false` a zabránit výjimku vyvolána.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky](../../../../docs/framework/wpf/controls/index.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)

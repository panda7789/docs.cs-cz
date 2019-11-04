---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 3e66b2306c11c54db14eb05cc6860257635cc653
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460355"
---
# <a name="datepicker"></a>DatePicker
Ovládací prvek <xref:System.Windows.Controls.DatePicker> umožňuje uživateli vybrat datum buď jeho zadáním do textového pole nebo pomocí rozevíracího <xref:System.Windows.Controls.Calendar> ovládacího prvku.  
  
 Následující obrázek ukazuje <xref:System.Windows.Controls.DatePicker>.  
  
 ![Ovládací prvek DatePicker](./media/ndp-datepicker.png "NDP_DatePicker")  
Ovládací prvek DatePicker  
  
 Mnohé z vlastností ovládacího prvku <xref:System.Windows.Controls.DatePicker> jsou pro správu integrované <xref:System.Windows.Controls.Calendar>a fungují stejně jako ekvivalentní vlastnost v <xref:System.Windows.Controls.Calendar>. Konkrétně funkce <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>a <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> fungují stejně jako jejich <xref:System.Windows.Controls.Calendar> protějšky. Další informace najdete v tématu <xref:System.Windows.Controls.Calendar>.  
  
 Uživatelé mohou zadat datum přímo do textového pole, které nastaví vlastnost <xref:System.Windows.Controls.DatePicker.Text%2A>. Pokud <xref:System.Windows.Controls.DatePicker> nemůže převést zadaný řetězec na platné datum, bude vyvolána událost <xref:System.Windows.Controls.DatePicker.DateValidationError>. Ve výchozím nastavení to způsobí výjimku, ale obslužná rutina události pro <xref:System.Windows.Controls.DatePicker.DateValidationError> může nastavit vlastnost <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> na `false` a zabránit vyvolání výjimky.  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvky](index.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)

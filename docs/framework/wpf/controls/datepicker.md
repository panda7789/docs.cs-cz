---
title: DatePicker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd2a1755ae076369661b2c9a7a2b744961cdb129
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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

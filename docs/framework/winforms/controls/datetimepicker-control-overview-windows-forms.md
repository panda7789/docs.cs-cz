---
title: DateTimePicker – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: cf44cdff7da06a27921ce5881199a3a88b1096f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528339"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>DateTimePicker – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DateTimePicker> řízení umožňuje uživateli vybrat jednu položku ze seznamu data nebo časy. Při použití představující datum, zobrazí se ve dvou částech: rozevírací seznam s datum tvaru v textovém a mřížky, které se zobrazí po kliknutí na šipku dolů vedle seznamu. Mřížky vypadá <xref:System.Windows.Forms.MonthCalendar> řízení, které lze použít pro výběr více daty. Další informace o <xref:System.Windows.Forms.MonthCalendar> řízení najdete v tématu [MonthCalendar – Přehled ovládacího prvku](../../../../docs/framework/winforms/controls/monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Pokud chcete <xref:System.Windows.Forms.DateTimePicker> vypadaly jako ovládací prvek pro výběr nebo úpravy dob místo kalendářních dat, nastavte <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> vlastnost, která má `true` a <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Další informace najdete v části [postupy: zobrazení času pomocí ovládacího prvku DateTimePicker](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).  
  
 Když <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> je nastavena na `true`, zaškrtávací políčko se zobrazí vedle vybrané datum v ovládacím prvku. Pokud je zaškrtnuté políčko, můžete aktualizovat vybrané hodnoty data a času. Pokud je políčko prázdné, zobrazí se hodnota není k dispozici.  
  
 Ovládacího prvku <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> a <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> vlastnosti určit rozsah data a časy. <xref:System.Windows.Forms.DateTimePicker.Value%2A> Vlastnost obsahuje aktuální datum a čas ovládacího prvku nastavena na. Podrobnosti najdete v tématu [postup: sady a vrátí kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Hodnoty lze zobrazit v čtyři formáty, které se nastavují <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost: <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>, nebo <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Pokud je vybraný vlastní formát, je nutné nastavit <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> vlastnost k příslušným řetězcem. Podrobnosti najdete v tématu [postupy: zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)  
 [Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
